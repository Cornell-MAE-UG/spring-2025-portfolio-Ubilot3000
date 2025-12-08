---
layout: project
title: "FEA Wrench Design"
subtitle: "Just keep swimming..."
date: 2025-12-05
image: /assets/images/wec_rendering.PNG
tags: [ANSYS, Design]
---

### Summary
The final project in the MAE 3270: Mechanics of Materials course was to identify a wrench design and material that could meet a series of safety factor constraints, including yield strength, fracture toughness, and cyclic loading. After chosing a design, students had to CAD the model and test its performance in ANSYS Static Structural. Comparing FEA results to simplified hand-calculations, students got a better understanding of where the assumptions made in simplified equations were valid or not.


### Identifying Design Range
Safety factor 
- $$X_0$$ = 4 for yield or brittle failure, depending on the material.
- $$X_K$$ = 2 for crack growth with an assumed 0.04 in crach length.
- $$X_S$$ = 1.5 for fatigue stress at 1,000,000 cycles.

```matlab
% --- Ti-6Al-4V ---
E        = 16.3e6;   % Young's modulus (psi)
nu       = 0.332;   % Poisson's ratio (not used directly here)
su       = 114e3;  % tensile (or yield) strength (psi)
KIC      = 94.2e3;   % fracture toughness (psi*sqrt(in))
sfatigue = 88.9e3;  % fatigue strength for 10^6 cycles (psi)
a0       = 0.04;   % assumed crack depth (in)
Y        = 1.12;   % geometry factor for surface crack


% Safety factor requirements
Xo = 4.0;   % strength safety factor
XK = 2.0;   % fracture (K) safety factor
XS = 1.5;   % fatigue safety factor

%% ---- Design variable ranges ----
L = M / F;
fprintf("Wrench Length: %.2f in\n", L);
h_vec = linspace(0.25, 4, 5000);
b_vec = linspace(0.25, 4, 1000);

nh = numel(h_vec);
nb = numel(b_vec);

% Logical array of acceptable designs
ok = false(nh, nb);

% Optional: store SFs and output for plotting / inspection
SF_strength = zeros(nh, nb);
SF_crack    = zeros(nh, nb);
SF_fatigue  = zeros(nh, nb);
output_mVV  = zeros(nh, nb);

%% ---- Sweep over h, b ----

% End load P that gives torque M = P*L
P       = M / L;
M_fixed = M;             % max bending moment at drive (for failure)
M_gauge = P * (L - c);   % bending moment at gauge (for output)

for ih = 1:nh
    h = h_vec(ih);
    for ib = 1:nb
        b = b_vec(ib);

        % Section properties
        I = b * h^3 / 12;

        % ---- Stresses at fixed end (for failure checks) ----
        sigma_max = 6 * M_fixed / (b * h^2);  % psi

        % Strength safety factor
        SFs = su / sigma_max;

        % Fracture safety factor
        KI  = Y * sigma_max * sqrt(pi * a0);  % psi*sqrt(in)
        SFk = KIC / KI;

        % Fatigue safety factor (fully reversed)
        SFf = sfatigue / sigma_max;

        % ---- Gauge strain and output (at gauge location) ----
        sigma_g = 6 * M_gauge / (b * h^2);  % psi at gauge
        eps_g   = sigma_g / E;              % strain at gauge
        out     = 1e3 * eps_g;              % mV/V for half bridge with GF ≈ 2

        SF_strength(ih, ib) = SFs;
        SF_crack(ih, ib) = SFk;
        SF_fatigue(ih, ib) = SFf;
        output_mVV(ih, ib) = out;

        % ---- Acceptable design check ----
        ok(ih, ib) = (SFs >= Xo) && ...
            (SFk >= XK) && ...
            (SFf >= XS) && ...
            (out >= 1.0);   % >= 1.0 mV/V
    end
end


```