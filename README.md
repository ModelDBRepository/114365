# Requirement of an allosteric kinetics of NMDA receptors for spike-timing-dependent plasticity

Note from the ModelDB Administrator: the below is a copy of the author's web site at [http://www.bi.s.u-tokyo.ac.jp/kuroda-lab/info/STDP/index.html](http://www.bi.s.u-tokyo.ac.jp/kuroda-lab/info/STDP/index.html)

---

# "Requirement of an allosteric kinetics of NMDA receptors for spike-timing-dependent plasticity"

H. Urakubo, M. Honda, R.C. Froemke, S. Kuroda, *J Neurosci* 28(13) pp 3310-3323 (2008)

# Supplmentary Information

The source codes of an allosteric STDP model are provided [here](http://www.bi.s.u-tokyo.ac.jp/kuroda-lab/info/STDP/Urakubo2008.tar.gz) ("tar zxvf Urakubo2008.tar.gz" for uncompression), and detailed model description is [here](http://www.bi.s.u-tokyo.ac.jp/kuroda-lab/info/STDP/Urakubo2008SI.pdf). The source codes [Urakubo2008.tar.gz](http://www.bi.s.u-tokyo.ac.jp/kuroda-lab/info/STDP/Urakubo2008.tar.gz) contain the demonstration programs of voltage-dependent synaptic plasticity (Volt, Fig 2), spike-timing-dependent plasticity (STDP, Fig 4) and burst-dependent plasticity (BURST, Fig 7). All models were built on the GENESIS/kinetikit (version 2.2.1 or 2.3) with X86-Linux. To execute the demonstration programs, [the GENESIS simulator](http://www.genesis-sim.org/GENESIS/) (version 2.2.1 or 2.3) must be installed from source codes to your LINUX/UNIX system appropreately. The contruction of directories of the source codes is shown as follows.

| | | |
|-|-|-|
| **newgenesis** | | Extended GENESIS. The extended GENESIS is executable on X86-64 redhat Enterprise Linux ES ver 4 with appropriate ~/.simrc, kkit, etc. Otherwize, create your own "newgenesis" as described in MODEL/genesis_customizing/. |
| **Volt.out, STDP.out, BURST1.out, BURST2.out, BURST3.out** | | Scripts for simulations (csh/tcsh is assumed). Execute the files by "csh Volt.out". Note that the execution time is very long. It takes about 1 hour for one parameter simulation with 2.4 GHz AMD Opteron. |
| **Volt_PBSPro.out, STDP_PBSPro.out, BURST1_PBSPro.out, BURST2_PBSPro.out, BURST3_PBSPro.out** | | If your system has the job scheduler "PBS professional" ver 7 or above, you can use the scripts instead of Volt.out, STDP.out etc. to execute multiple simulations in parallel. Edit the files to fit your system. |
| **DATA_STDP/** | | Data strage for spike-timing-dependent plasticity (STDP, Fig 4). The subdirectories 0-17 store the simulation results of 100 pre- and post-spike pairing at T<sub>post</sub>-T<sub>pre</sub> = -256, -128, -64, -32, -16, -8, ..., 256 ms, respectively. |
| **DATA_Volt/** | | Data strage for voltage-dependent plasticity (Volt, Fig 2). The subdirectories 0-9 store the simulation results of 100 pre-spiking with holding -115, -105 -95, ..., 25 mV, respectively. |
| **DATA_BURST/** | | Data strage for burst-dependent plasticity (BURST, Fig 7A-C). The subdirectories POST1_PRE5, PRE5_POST1 and PostPrePost4 store the correspondent simulation results. |
| **tmp1/ - tmp5/** | | Temporal file strage of the GENESIS programs. |
| **PROGRAMS/** | | GENESIS subroutines. |
| **GRAPHS/** | | Graph plot files (Matlab m-files). VoltMolcProf.m draws Fig 2A-E, VoltMolcTot.m draws Fig 2G VoltCond.m draws Fig 2HI, STDPCond.m draws Fig 4DE, STDPMolc.m draws Fig 4FG, BURST1.m draws Fig 7A, BURST2.m draws Fig 7B, and BURST2.m draws Fig 7C. |
| **MODEL/** | **core33.g** | Kkit file of signaling cascade and AMPAR trafficking models. The model must be executed with initials33.g or initials_VoltageClamp33.g on the extended GENESIS. |
|  | **initials33.g** | Initial file loader for simulation of STDP and BURST. |
|  | **initials_VoltageClamp33.g** | Initial file loader for simulation of Volt. |
|  | **initial_routines/** | Initial files. |
|  | **Poirazi_cell/** | A postsynaptic neuron model with a sample program. Execute "./newgenesis main_Poirazi.g" with your own "newgenesis." |
|  | **genesis_customizing/** | Extension on the GENESIS simulator. The extension "newgenesis" of your own system is required for successful execution of the sample programs. To create "newgenesis" of your own system: <br>1. Check the versions of ${GENESIS_SOURCE}/Usermake and ${GENESIS_SOURCE}/Libmake by reading the first lines of the files. If the versions are different from ${Urakubo2008}/MODEL/genesis_customizing/Makefile and ${Urakubo2008}/MODEL/genesis_customizing/*/Makefile, this may cause problems. Replace the files with your GENESIS files, if the problems occur.<br>2. Modify the system configuration variables (line 57, lines 64-73) of ${Urakubo2008}/MODEL/genesis_customizing/Makefile for your own system. You can refer to ${GENESIS_SOURCE}/src/Makefile.<br>3. Fill the user configuration variables of ${Urakubo2008}/MODEL/genesis_customizing/Makefile if you replaced the files with ${GENESIS_SOURCE}/Usermake.<br>4. Fill the user configuration section of ${Urakubo2008}/MODEL/genesis_customizing/*/Makefile if you replaced the files with ${GENESIS_SOURCE}/Libmake.<br>5. "make" in the directory "${Urakubo2008}/MODEL/genesis_customizing".<br>6. If the programs are compiled successfully, "cp ./newgenesis ./../../" and enjoy the sample programs! |

---

2025-06-02: Standardized to Markdown.