Overview of the Cluster DEI Platform
==============================
.. |br| raw:: html

     <br>
.. _overview: 

**Cluster DEI** is a computing platform. It consists in many nodes equipped with:

- **runner-[01-03]** Three nodes with 48 CPUs (4x Intel(R) Xeon(R) Gold 5118 CPU @ 2.30/3.20GHz), 1.5TB RAM 
- **runner-[04-06]** Three nodes with 72 CPUs (4x Intel(R) Xeon(R) Gold 5220 CPU @ 2.20/3.90GHz), 2TB RAM, |br|    
  one Nvidia Quadro P2000 GPU
- **runner-[07-09]** Three nodes with 96 CPUs (4x Intel(R) Xeon(R) Gold 6252N CPU @ 2.30/3.60GHz, 3TB RAM
- **gpu1** CPUs = 24 (2x Intel(R) Xeon(R) Gold 5118 CPU @ 2.30/3.20GHz), RAM = 1TB, |br|        
  GPUs = 6x Nvidia Titan RTX
- **gpu2** CPUs = 32 (2x Intel(R) Xeon(R) Gold 5218 CPU @ 2.30/3.90GHz), RAM = 1.5TB, |br|        
  GPUs = 8x Nvidia RTX 3090
- **gpu3** CPUs = 32 (2x Intel(R) Xeon(R) Gold 5218 CPU @ 2.30/3.90GHz), RAM = 1.5TB, |br|        
  GPUs = 8x Nvidia RTX 3090
  
  

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
