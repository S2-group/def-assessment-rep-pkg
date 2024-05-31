def-verification
====================================

This repository hosts the replication package of the empirical study titled:  "An empirical assessment and improvement of the Digital Environmental Footprint formulas for server-side software".

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

Running the Experiment (from DS)
----------------------

These are the followed steps to run the experiment:

1.  Clone the repository.
2.  Install the necessary dependencies in DS (from Requirements).
3.  Install the necessary dependencies in the SUTs.
4.  Install the necessary dependencies in the MS.
5.  Perform the necessary modifications in the RunnerConfig.py files.
6.  Execute the experiment with
```bash
python experiment-runner/ <SelectedRunnerConfig.py>
```

Repository Structure
--------------------

The repository contains the following files and directories:

- `experiment-runner/`: experiment-runner configuration
  - `GL2/`: RunnerConfig files and results for experiments on SUT1 (GL2)
  - `GL5/`: RunnerConfig files and results for experiments on SUT2 (GL5)
  - `GL6/`: RunnerConfig files and results for experiments on SUT3 (GL6)
  - `experiment-runner/`: experiment-runner's internal source code
  - `other_RunnerConfigs_ander/`: old RunnerConfig files
- `scripts/`: contains all the necessary scripts for the experiment.
  - `analysis/`: scripts used for the data analysis
  - `archive/`: old scripts, not in use anymore
  - `experiment-runner/`: scripts used for running the experiment
  - `preprocessing/`: scripts that clean and parse the data to the required format
  - `utils/`: other scripts for auxiliary tasks
- `README.md`: this file.


Feel free to contact me for further requests and to adapt this README file to suit your project's specific needs.
