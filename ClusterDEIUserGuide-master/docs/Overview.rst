Overview of the Cluster DEI Platform
==============================
.. |br| raw:: html

     <br>
.. _overview: 

**Cluster DEI** is a computing platform. It consists in many nodes equipped with:

- **runner-01** CPUs = 48 (4x Intel(R) Xeon(R) Gold 5118 CPU @ 2.30/3.20GHz), RAM = 1.5TB
- **runner-02** CPUs = 48 (4x Intel(R) Xeon(R) Gold 5118 CPU @ 2.30/3.20GHz), RAM = 1.5TB
- **runner-03** CPUs = 48 (4x Intel(R) Xeon(R) Gold 5118 CPU @ 2.30/3.20GHz), RAM = 1.5TB
- **runner-04** CPUs = 72 (4x Intel(R) Xeon(R) Gold 5220 CPU @ 2.20/3.90GHz), RAM = 2TB, |br|    
  GPU = Nvidia Quadro P2000
- **runner-05** CPUs = 72 (4x Intel(R) Xeon(R) Gold 5220 CPU @ 2.20/3.90GHz), RAM = 2TB, |br|   
  GPU = Nvidia Quadro P2000
- **runner-06** CPUs = 72 (4x Intel(R) Xeon(R) Gold 5220 CPU @ 2.20/3.90GHz), RAM = 2TB, |br| 
  GPU = Nvidia Quadro P2000
- **runner-07** CPUs = 96 (4x Intel(R) Xeon(R) Gold 6252N CPU @ 2.30/3.60GHz, RAM = 3TB
- **runner-08** CPUs = 96 (4x Intel(R) Xeon(R) Gold 6252N CPU @ 2.30/3.60GHz, RAM = 3TB
- **runner-09** CPUs = 96 (4x Intel(R) Xeon(R) Gold 6252N CPU @ 2.30/3.60GHz, RAM = 3TB
- **gpu1** CPUs = 24 (2x Intel(R) Xeon(R) Gold 5118 CPU @ 2.30/3.20GHz), RAM = 1TB, |br|        
  GPUs = 6x Nvidia Titan RTX

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
