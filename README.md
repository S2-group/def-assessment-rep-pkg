def-verification
====================================

This repository hosts the replication package of the master's thesis:  "An independent verification and improvement proposal of the Digital Environmental Footprints formulas from the SDIA". This study consists of an  experiment that stresses a set of servers to certain CPU loads in realistic and synthetic workload scenarios to measure their energy consumption. Later, the obtained results are compared against the predictions from the DEF (Digital Environmental Formulas) from SDIA for those servers.

The aim of this experiment is to independently verify the validity of DEF formulas to model real systems.

Explanatory slides
----------------------
You can find here the [slides](https://docs.google.com/presentation/d/1bEFWuwrVfh1EOHOaQKpiMk8k0XHbNL4rB-iwBPBWa_Q/edit?usp=sharing). More detailed info about the experiment details can be found in the appendix section of the presentation.

Experiment Description
----------------------

The experiment aims to measure the energy consumption of a group of servers under different loads. The experiment is orchestrated with [ExperimentRunner](https://github.com/S2-group/experiment-runner). The servers are subjected to different CPU loads using [stress-ng](https://github.com/ColinIanKing/stress-ng), a well-known Linux stressor, and [TrainTicketSystem](https://github.com/FudanSELab/train-ticket), a microservice-based web-service. The energy consumption data is obtained via a [Rittal](https://github.com/GioDoesntKnowCode/Rittal_Power_Monitoring) monitoring system, while the CPU data is obtained via 'lm-sensors' and 'mpstat'. The obtained data is then preprocessed using Python and analysed using Excel.

Architecture
--------
![ExperimentSetup](https://github.com/eguiwow/def-verification/assets/22910746/87cf9e8e-28f4-4d6e-8121-abed32f1166b)
* Developing System (DS): Linux-based computer where the experiment gets started and is conducted
* Monitoring System (MS): Linux-based server in charge of monitoring the energy consumption of the SUT.
* System Under Test (SUT): Linux-based servers in which the experiment is performed, this is, they are stressed through the use of the TTS or stress-ng at different CPU loads for various runs.

Requirements
--------
* DS
  - Experiment Runner (installation instructions in the [repo](https://github.com/S2-group/experiment-runner))
  - k6 suite ([installation](https://k6.io/docs/get-started/installation/))
  - Rittal Power monitoring repo ([installation](https://github.com/GioDoesntKnowCode/Rittal_Power_Monitoring))
* MS
  - Rittal Power monitoring repo ([installation](https://github.com/GioDoesntKnowCode/Rittal_Power_Monitoring))
* SUT
  - Train Ticket System ([installation guide](https://github.com/FudanSELab/train-ticket/wiki/Installation-Guide))
  - Stress-ng (installation instructions in the [repo](https://github.com/ColinIanKing/stress-ng))

Workflow
--------

The experiment workflow consists of the following steps:

1.  Experiment Runner is used to orchestrate, configure, and run the experiment.
2.  The energy consumption data is collected via Rittal.
3.  The CPU data is collected via 'lm-sensors' and 'mpstat', memory data via 'free'.
4.  The collected data is preprocessed using Python.
5.  The cleaned data is analysed using Excel

Running the Experiment (WIP)
----------------------

These are the followed steps to run the experiment:

1.  Clone the repository.
2.  Install the necessary dependencies (from Requirements).
3.  Configure the necessary modifications in the RunnerConfig.py files.
4.  Execute the experiment by
```bash
python experiment-runner/ <MyRunnerConfig.py>
```

Repository Structure
--------------------

The repository contains the following files and directories:

-   `bash_scripts/`: contains the bash scripts used to subject the server to different loads.
-   `preprocessing/`: contains the Python scripts used to preprocess the obtained data.
-   `experiment.log`: info about the experiment.
-   `README.md`: this file.


Feel free to contact me for further requests and to adapt this README file to suit your project's specific needs.
