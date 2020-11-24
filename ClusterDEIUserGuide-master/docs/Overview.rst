Overview of the Cluster DEI Platform
==============================

.. _overview: 

**Cluster DEI** is a computing platform. It consists in many nodes equipped with:

- **runner-[01,02,03]** CPUs = 48, RAM = 1.5TB
- **runner-[04,05,06]** CPUs = 72, RAM = 2TB, GPUs = Nvidia Quadro P2000
- **runner-07** CPUs = 12, RAM = 126GB 
- **runner-08** CPUs = 12, RAM = 158GB
- **runner-13** CPUs = 64, RAM = 255GB 
- **runner-14** CPUs = 64, RAM = 255GB 
- **runner-15** CPUs = 12, RAM = 94GB  
- **runner-[16,17]** CPUs = 24, RAM = 78GB 
- **runner-[18-19]** CPUs = 8, RAM = 30GB  
- **gpu1** CPUs = 24, RAM = 1TB, GPUs = 10x Nvidia Titan RTX
- **gpu2** CPUs = 12, RAM = 120GB, GPUs = 2x Nvidia Titan XP

Access to the computing resources is regulated through the SLURM scheduler.

The system is equipped with some *system* software managed by the administrators. The software 
catalog can be extended by:

  * Requesting the installation *system wide*, if the software is considered useful for a large
    user group, by using the `DEI Helpdesk System <https://www.dei.unipd.it/helpdesk/>`_ 
  * Installing your software(s) inside a *Singularity* container

.. _authors:
------------

Paolo Emilio Mazzon - paoloemilio.mazzon@unipd.it
Lorenzo Sartoratti - lorenzo.sartoratti@unipd.it
Giacomo Baruzzo - giacomo.baruzzo@unipd.it
Agostino Andriolo - agostino.andriolo@unipd.it
