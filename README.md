# Franka Friction Identification Dataset

Dataset accompanying the submission to IEEE RO-MAN 2026.

This repository contains the datasets, experimental configurations, and identified friction parameters used for friction model identification and validation on a Franka Emika Panda robot.

## Repository Structure

```text
01_identification_trajectories/
02_validation_trajectories/
03_initial_joint_configurations/
04_contact_experiment_configurations/
05_identified_friction_parameters/
```

## Identification Trajectories

The identification dataset comprises **315 experimental conditions** (joint, configuration, and velocity combinations), corresponding to **420 reference trajectories**.

Each identification trajectory is organized according to:

```text
qX/
└── qX_cY/
    └── v_Z/
```

where:

* `qX` denotes the excited joint (`q1`–`q7`),
* `cY` denotes the initial robot configuration,
* `v_Z` denotes the maximum joint velocity used for the trajectory.

For configurations located away from the joint limits, trajectories were executed in both positive and negative directions to capture direction-dependent friction effects. Consequently, both

```text
traj_pos_position.csv
traj_pos_velocity.csv

traj_neg_position.csv
traj_neg_velocity.csv
```

are available.

For configurations located close to the physical joint limits, motion was restricted to the feasible direction only. In these cases, only positive or only negative trajectories are provided.

Trajectory files contain joint-space reference trajectories for all seven robot joints.

## Validation Trajectories

The validation dataset contains **105 trajectories** that were not used during parameter identification.

These trajectories were used for independent experimental and simulation validation of the identified friction models.

Unlike the identification trajectories, validation trajectories were executed at lower velocities (up to **0.5 rad/s**), reflecting the operating range used in the subsequent contact-control experiments.

Each validation trajectory contains joint-space position and velocity references for all seven joints.

## Initial Joint Configurations

The file:

```text
initial_joint_configurations.xlsx
```

contains the initial robot configurations used during trajectory generation.

Each sheet corresponds to one excited joint (`q1`–`q7`).

Configurations `c1-c9` were used for parameter identification, while configurations `c10-c12` were used for trajectory validation.

Joint positions are provided in both radians and degrees.

## Contact Experiment Configurations

The file:

```text
contact_experiment_configurations.xlsx
```

contains the initial robot configurations used in the task-space contact experiments reported in the paper.

These configurations were selected to evaluate contact behavior under different robot postures and interaction conditions.

Joint positions are provided in both radians and degrees.

## Identified Friction Parameters

The file:

```text
identified_friction_parameters.xlsx
```

contains the identified parameter values of both friction models considered in the paper:

* Symmetric friction model
* Asymmetric friction model

Parameter values are reported for all seven joints of the Franka Emika Panda robot.

## License

This dataset is licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0).

https://creativecommons.org/licenses/by/4.0/
