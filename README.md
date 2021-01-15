# ABOP_lammps
Collection of some analytical bond order potentials ( listed in the LAMMPS format) from literature.

# W-C
The WC potential is taken from 

Ref.1: N. Juslin, P. Erhart, P. Tr\"{a}skelin, J. Nord, K. O. E. Henriksson, K. Nordlund, E. Salonen, and K. Albe, *J. Appl. Phys.*, **98**, 123520(2005); DO: [10.1063/1.2149492](https://doi.org/10.1063/1.2149492).

Ref.2: M.V.G. Petisme, M.A. Gren, G. Wahnstr\"{o}m}, *Int. J. Refract. Hard Met.*, **49**, 75--80(2015); DOI: [10.1016/j.ijrmhm.2014.07.037](https://doi.org/10.1016/j.ijrmhm.2014.07.037).

**Note**: there is a typo for the "beta" value of C-C in Table 1 of Ref. 2, which is inconsistent with the one in Ref. 1.

# Ga-N
[Provided by openKIM](https://www.ctcms.nist.gov/potentials/Download/2003--Nord-J-Albe-K-Erhart-P-Nordlund-K--Ga-N/1/2003_GaN.tersoff). In this file, the **n** values of 'Ga Ga N', 'N Ga N', 'N N Ga', 'Ga N Ga' are set to **0.0**.

[Provided by LAMMPS](https://github.com/lammps/lammps/blob/master/potentials/GaN.tersoff). In this file, the **n** values of 'Ga Ga N', 'N Ga N', 'N N Ga', 'Ga N Ga' are set to **1.0**.

This difference in the setup of **n** doesn't affect the simulation results. It will give identical results. 

