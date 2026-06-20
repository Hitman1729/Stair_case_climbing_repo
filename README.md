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
| Software | Kinovea Version 0.9.5 |

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
