def-verification
====================================

This repository hosts the replication package of the master's thesis:  "An independent verification and improvement proposal of the Digital Environmental Footprints formulas from the SDIA". This study consists of an  experiment that stresses a set of servers to certain CPU loads in realistic and synthetic workload scenarios to measure their energy consumption. Later, the obtained results are compared against the predictions from the DEF (Digital Environmental Formulas) from SDIA for those servers.

The aim of this experiment is to independently verify the validity of DEF formulas to model real systems.

Explanatory slides
----------------------
You can find here the [slides](https://docs.google.com/presentation/d/1bEFWuwrVfh1EOHOaQKpiMk8k0XHbNL4rB-iwBPBWa_Q/edit?usp=sharing). More detailed info about the experiment details can be found in the appendix section of the presentation.

Experiment Description
----------------------

The experiment aims to measure the energy consumption of a group of servers under different loads. The servers are subjected to different CPU loads using [stress-ng](https://github.com/ColinIanKing/stress-ng), a well-known Linux stressor, and [TrainTicketSystem](https://github.com/FudanSELab/train-ticket), a microservice-based web-service. The energy consumption data is obtained via a [Rittal](https://github.com/GioDoesntKnowCode/Rittal_Power_Monitoring) monitoring system, while the CPU data is obtained via 'lm-sensors' and 'mpstat'. The obtained data is then preprocessed using Python and analysed using Excel.

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
2.  Install the necessary dependencies (e.g., stress-ng, WattsupPro, lm-sensors, mpstat).
3.  Run stress-ng to subject the server to different loads.
4.  Collect the energy consumption and CPU data using mpstat and lm-sensors tools.

Repository Structure
--------------------

The repository contains the following files and directories:

-   `bash_scripts/`: contains the bash scripts used to subject the server to different loads.
-   `preprocessing/`: contains the Python scripts used to preprocess the obtained data.
-   `experiment.log`: info about the experiment.
-   `README.md`: this file.


Feel free to contact me for further requests and to adapt this README file to suit your project's specific needs.
