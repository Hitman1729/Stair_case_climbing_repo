# Stair Climbing Joint Torque Estimation

## Video-Based Hip and Knee Joint Torque Estimation During Stair Climbing Using Fourier-Augmented Euler-Lagrange Inverse Dynamics

---

## Authors

Hitesh Mohan Veludandi, Subrahmanya Krishna Teja Chimalakonda,
Mohammad Sameer, Sri Charan Sarma Eranki, Mani Varma Vathadi,
Dr. Emon Barua

Department of Mechanical Engineering,
Maulana Azad National Institute of Technology (MANIT), Bhopal, India

## Corresponding Author

Dr. Emon Barua
emon.barua@manit.ac.in

## Journal

Journal of Biomechanics (Under Review, 2025)

## Repository DOI

https://doi.org/10.5281/zenodo.XXXXXXX

---

## Overview

This repository contains all data and MATLAB code supporting the
above manuscript. The study presents a low-cost pipeline for
estimating hip and knee joint torques during stair climbing using
only a single video camera and open-source software, without force
plates or three-dimensional motion capture.

Three healthy male subjects performed stair climbing on a standard
indoor staircase. Hip and knee joint angles were measured at 120
frames per second using a Sony Alpha A6100 camera and Kinovea
software. A Fourier 4th-order model was fitted in MATLAB to produce
smooth analytical kinematic profiles, and a two-degree-of-freedom
Euler-Lagrange dynamic model was used to compute continuous hip and
knee joint torque time histories.

---

## Subject Details

| Subject   | Body Mass (kg) | Height (m) | Frames | T (s) |
|-----------|----------------|------------|--------|-------|
| Subject 1 | 61 | 1.69 | 181 | 1.502 |
| Subject 2 | 63 | 1.70 | 158 | 1.310 |
| Subject 3 | 73 | 1.76 | 163 | 1.351 |

All subjects participated voluntarily and provided informed consent.
Subjects are anonymised as Subject 1, Subject 2, and Subject 3
throughout all files for privacy.

---

## Staircase and Camera Specifications

| Parameter | Value |
|-----------|-------|
| Riser height | 14.5 cm |
| Tread depth | 29.5 cm |
| Pitch angle | 26.2 degrees |
| Camera | Sony Alpha A6100 (ILCE-6100) |
| Frame rate | 120 fps |
| Resolution | 1920 x 1080 pixels (Full HD) |
| Software | Kinovea Version 2025.2.0 |

---

## Repository Structure
Stair_case_climbing_repo/

│

├── README.md

├── LICENSE

│

├── data/

│   ├── raw_angles/

│   │   ├── Subject1_hip_file.csv

│   │   ├── Subject1_knee_file.csv

│   │   ├── Subject2_hip_file.csv

│   │   ├── Subject2_knee_file.csv

│   │   ├── Subject3_hip_file.csv

│   │   └── Subject3_knee_file.csv

│   │

│   └── converted_angles/

│       ├── Subject1_converted_angles.xlsx

│       ├── Subject2_converted_angles.xlsx

│       └── Subject3_converted_angles.xlsx

│

├── code/

│   ├── MATLAB_Fourier_Fitting.m

│   └── MATLAB_EulerLagrange_Torque.m

│

├── fourier_coefficients/

│   └── Supplementary_Table_S1_Fourier_Coefficients.xlsx

│

└── torque_values/

├── Subject1_torque_output.xlsx

├── Subject2_torque_output.xlsx

└── Subject3_torque_output.xlsx
---

## File Descriptions

### data/raw_angles/

Six CSV files containing raw hip and knee angle data exported
directly from Kinovea Version 2025.2.0 at 120 frames per second.

Each file contains two columns:
- Column 1: Time (milliseconds, as exported by Kinovea)
- Column 2: Angle (radians)

**Note:** Time is exported in milliseconds by Kinovea. The MATLAB
scripts convert this to seconds by dividing by 1000 before fitting,
as described in the paper.

File naming:
- SubjectN_hip_file.csv  — hip angle measured from the vertical
- SubjectN_knee_file.csv — included knee angle between thigh and shank

The raw hip angle is consistently negative in Kinovea because the
vertical reference marker is placed above the hip joint centre.
The raw knee angle is positive and obtuse, representing the
supplement of the true knee flexion angle.

### data/converted_angles/

Three Excel files (one per subject) containing the converted joint
flexion angles after applying the conversion formula to the raw
Kinovea output. Each file contains both the hip and knee converted
angles for that subject.

Columns in each file:
- Time (seconds)
- Raw hip angle (radians)
- Converted hip angle theta_1 (radians)
- Raw knee angle (radians)
- Converted knee angle theta_2 (radians)

### code/MATLAB_Fourier_Fitting.m

MATLAB script for Fourier 4th-order curve fitting of the converted
hip and knee angle data. Only 14 representative points from the full
dataset were used for accurate curve fitting, as described in the paper.

Requirements: MATLAB R2020a or later, Curve Fitting Toolbox

Instructions:
1. Load the converted angle xlsx file for the subject
2. Set the subject name and gait cycle duration T
3. Run the script
4. Fourier coefficients are printed to the command window
5. Fitted curves are plotted automatically with R-squared and RMSE

### code/MATLAB_EulerLagrange_Torque.m

MATLAB script for computing hip and knee joint torques using the
two-degree-of-freedom Euler-Lagrange dynamic model.

Requirements: MATLAB R2020a or later

Instructions:
1. Enter the Fourier coefficients from the fitting script
2. Set subject body mass M and height H at line 32
3. Run the script
4. Hip and knee torque time histories are plotted and exported

### fourier_coefficients/

Supplementary Table S1 containing all fitted Fourier coefficients
(a0 through b4), together with R-squared and RMSE goodness-of-fit
statistics, for the hip and knee angles of all three subjects.

### torque_values/

Three Excel files containing the computed hip torque and knee torque
time histories for each subject across the complete gait cycle.

---

## Angle Conversion Formula
theta = pi - |theta_raw|
Applied identically to both hip and knee angles, where theta_raw is
the raw Kinovea angle in radians and theta is the converted joint
flexion angle.

- Hip raw angles are negative in Kinovea.
- Knee raw angles are positive and obtuse in Kinovea.

---

## Body Segment Parameter Equations

All body segment inertial parameters were computed from subject body
mass M (kg) and height H (m):

| Parameter | Formula | Source |
|-----------|---------|--------|
| Thigh length L1 | 0.245 x H | Plagenhoef et al. (1983) |
| Shank length L2 | 0.246 x H | Plagenhoef et al. (1983) |
| Thigh mass m1 | 0.100 x M | Winter (2009) |
| Shank mass m2 | 0.0465 x M | Winter (2009) |
| Thigh COM r1 | 0.433 x L1 | de Leva (1996) |
| Shank COM r2 | 0.433 x L2 | de Leva (1996) |
| Thigh ROG k1 | 0.323 x L1 | de Leva (1996) |
| Shank ROG k2 | 0.302 x L2 | de Leva (1996) |
| Thigh MOI I1 | m1 x k1^2 | — |
| Shank MOI I2 | m2 x k2^2 | — |

---

## How to Reproduce the Results

1. Download the raw CSV files from data/raw_angles/
2. Apply the angle conversion formula, or use the pre-converted
   files in data/converted_angles/
3. Run MATLAB_Fourier_Fitting.m for each subject to obtain the
   Fourier coefficients
4. Run MATLAB_EulerLagrange_Torque.m using those coefficients and
   the subject body mass and height
5. Compare the peak torque outputs with Table 4 of the paper:
   - Subject 1: Hip 27.29 N.m, Knee 9.59 N.m
   - Subject 2: Hip 39.97 N.m, Knee 12.72 N.m
   - Subject 3: Hip 49.43 N.m, Knee 16.28 N.m

---

## Citation

If you use this data or code in your research, please cite:

**Paper:**
Veludandi, H.M., Chimalakonda, S.K.T., Sameer, M., Eranki, S.C.S.,
Vathadi, M.V., Barua, E. (2025). Video-Based Hip and Knee Joint
Torque Estimation During Stair Climbing Using Fourier-Augmented
Euler-Lagrange Inverse Dynamics. Journal of Biomechanics.

**Repository:**
Veludandi, H.M., et al. (2025). Data and Code for: Video-Based Hip
and Knee Joint Torque Estimation During Stair Climbing Using
Fourier-Augmented Euler-Lagrange Inverse Dynamics (Version 1.0).
Zenodo. https://doi.org/10.5281/zenodo.XXXXXXX

---

## License

This work is dedicated to the public domain under
CC Zero v1.0 Universal (CC0 1.0).
https://creativecommons.org/publicdomain/zero/1.0/

You are free to copy, modify, distribute, and use the data and code
for any purpose without restriction.
