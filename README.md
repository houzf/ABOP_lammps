# ABOP_lammps
Collection of some analytical bond order potentials ( listed in the LAMMPS format) from literature.

# W-C
The WC potential is taken from 

Ref.1: N. Juslin, P. Erhart, P. Tr\"{a}skelin, J. Nord, K. O. E. Henriksson, K. Nordlund, E. Salonen, and K. Albe, *J. Appl. Phys.*, **98**, 123520(2005); DO: [10.1063/1.2149492](https://doi.org/10.1063/1.2149492).

Ref.2: M.V.G. Petisme, M.A. Gren, G. Wahnstr\"{o}m}, *Int. J. Refract. Hard Met.*, **49**, 75--80(2015); DOI: [10.1016/j.ijrmhm.2014.07.037](https://doi.org/10.1016/j.ijrmhm.2014.07.037).

**Note**: there is a typo for the "beta" value of C-C in Table 1 of Ref. 2, which is inconsistent with the one in Ref. 1.

# Ga-N
The GaN potential is taken from 

Ref.3: J. Nord, K. Albe, P. Erhart, and K. Nordlund, *J. Phys. Condens Matter*, **15**, 5649 (2003); DOI: [10.1088/0953-8984/15/32/324](https://doi.org/10.1088/0953-8984/15/32/324).

Source 1: [provided by openKIM](https://www.ctcms.nist.gov/potentials/Download/2003--Nord-J-Albe-K-Erhart-P-Nordlund-K--Ga-N/1/2003_GaN.tersoff). In this file, the **n** values of 'Ga Ga N', 'N Ga N', 'N N Ga', 'Ga N Ga' are set to **0.0**.

Source 2: [Provided by LAMMPS](https://github.com/lammps/lammps/blob/master/potentials/GaN.tersoff). In this file, the **n** values of 'Ga Ga N', 'N Ga N', 'N N Ga', 'Ga N Ga' are set to **1.0**.

This difference in the setup of **n** doesn't affect the simulation results. It will give identical results. 


# Ga-As
The GaAs potential is taken from 

Ref. 4: K. Albe, K. Nordlund, J. Nord, and A. Kuronen, *Phys. Rev. B* **66**, 035205(2002); DOI: [10.1103/PhysRevB.66.035205](https://doi.org/10.1103/physrevb.66.035205).

Source 1: [provided by openKIM](https://www.ctcms.nist.gov/potentials/Download/2002--Albe-K-Nordlund-K-Nord-J-Kuronen-A--Ga-As/1/2002_GaAs.tersoff). In this file, the **n** values of 'Ga Ga As', 'As Ga As', 'As As Ga', 'Ga As Ga' are set to **0.0**.

# Zn-O
The ZnO potential is taken from 

Ref. 5: P. Erhart, N. Juslin, O. Goy, K. Nordlund, R. M{\"{u}}ller, and K. Albe, *J. Phys.: Condens. Matter* **18** (2006) 6585-6605; DOI: [10.1088/0953-8984/18/29/003](http://dx.doi.org/10.1088/0953-8984/18/29/003).

Note: some discussions about the reliablity of this Zn-O potential can be found on the [forum of lammps](https://lammps.sandia.gov/threads/msg49926.html).
