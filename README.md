# ABOP_lammps
Collection of some analytical bond order potentials ( listed in the LAMMPS format) from literature.

# W-C
The WC potential is taken from 

Ref.1: N. Juslin, P. Erhart, P. Tr\"{a}skelin, J. Nord, K. O. E. Henriksson, K. Nordlund, E. Salonen, and K. Albe, *J. Appl. Phys.*, **98**, 123520(2005); DO: [10.1063/1.2149492](https://doi.org/10.1063/1.2149492).

Ref.2: M.V.G. Petisme, M.A. Gren, G. Wahnstr{\"{o}}m, *Int. J. Refract. Hard Met.*, **49**, 75--80(2015); DOI: [10.1016/j.ijrmhm.2014.07.037](https://doi.org/10.1016/j.ijrmhm.2014.07.037).

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

Ref. 5: P. Erhart, N. Juslin, O. Goy, K. Nordlund, R. M{\"{u}}ller, and K. Albe, *J. Phys.: Condens. Matter* **18** (2006)6585-6605; DOI: [10.1088/0953-8984/18/29/003](http://dx.doi.org/10.1088/0953-8984/18/29/003).

Source 1: [provided by openKIM](https://openkim.org/files/MO_616776018688_002/Tersoff_ErhartJuslinGoy_2006_ZnO.params). In this file, the **n** values of 'Zn Zn O', 'O Zn O', 'O O Zn', 'Zn O Zn' are set to **0.0**.

**Note**: some discussions about the reliability of this Zn-O potential can be found on the [forum of lammps](https://lammps.sandia.gov/threads/msg49926.html).

# Au
The Au potential is taken from 

Ref. 6: M. Backman, N. Juslin, and K. Nordlund, *Eur. Phys. J. B* **85**(2012)317; DOI: [10.1140/epjb/e2012-30429-y](http://dx.doi.org/10.1140/epjb/e2012-30429-y).

# Pt-C
The PtC potential is taken from 

Ref. 7: K. Albe, K. Nordlund, and R. S. Averback, *Phys. Rev. B* **65** (2002)195124; DOI: [10.1103/physrevb.65.195124](https://doi.org/10.1103/physrevb.65.195124).

# Ti-Al-C
The Ti-Al-C potential for Ti<sub>3</sub>AlC<sub>2</sub> MAX Phase and Ti-Si-C poential for Ti<sub>3</sub>SiC<sub>2</sub> MAX Phase are taken from 

Ref. 8: G. Plummer and G. J. Tucker, *Phys. Rev. B* **100** (2019)214114; DOI: [10.1103/PhysRevB.100.214114](https://doi.org/10.1103/PhysRevB.100.214114).

# Be-O
The Be-O potential is taken from 

Ref. 9: J. Byggm\"{a}star, E. A. Hodille, Y. Ferro, and K. Nordlund, *J. Phys.: Condens. Matter*, **30**, 135001(2018); DOI: [10.1088/1361-648X/aaafb3](https://doi.org/10.1088/1361-648X/aaafb3).

To describe repulsive short-range interactions more accurately,  the universal repulsive Ziegler-Biersack-Littmark (ZBL) potential V<sub>ZBL</sub> (r<sub>ij</sub>) is used jointly with the original potential V<sub>ij</sub>.

V'<sub>ij</sub> = F(r<sub>ij</sub>) V<sub>ij</sub> + [1-F(r<sub>ij</sub>)] V<sub>ZBL</sub>

F(r<sub>ij</sub>) is Fermi function, i.e., 1/[1+exp(-b<sub>f</sub> (r<sub>ij</sub> -r<sub>f</sub>))]

|  Parameters   | Be-Be | O-O  | Be-O |
| :-----------: | :---: | :--: | :--: |
| b<sub>f</sub> | 15.0  | 12.0 | 15.0 |
| r<sub>f</sub> |  0.8  | 0.5  | 0.8  |


# Be-C
The Be-C potential is taken from 

Ref. 10: C. Bj\"{o}rkas, N. Juslin, H. Timko, K. V\"{o}rtler, K. Nordlund, K. Henriksson, and P. Erhart, *J. Phys.: Condens. Matter*, **21**, 445002(2009); DOI: [10.1088/0953-8984/21/44/445002](http://dx.doi.org/10.1088/0953-8984/21/44/445002).

To describe repulsive short-range interactions more accurately,  the universal repulsive Ziegler-Biersack-Littmark (ZBL) potential V<sub>ZBL</sub> (r<sub>ij</sub>) is used jointly with the original potential V<sub>ij</sub>.

V'<sub>ij</sub> = F(r<sub>ij</sub>) V<sub>ij</sub> + [1-F(r<sub>ij</sub>)] V<sub>ZBL</sub>

F(r<sub>ij</sub>) is Fermi function, i.e., 1/[1+exp(-b<sub>f</sub> (r<sub>ij</sub> -r<sub>f</sub>))]

|  Parameters   | Be-Be | C-C  | Be-C |
| :-----------: | :---: | :--: | :--: |
| b<sub>f</sub> | 15.0  | 8.0  | 16.0 |
| r<sub>f</sub> |  0.8  | 0.6  | 0.7  |


