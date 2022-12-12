# ABOP_lammps
Collection of some analytical bond order potentials ( listed in the LAMMPS format) from literature.

## Comparison between different formulas

| Tersoff_1 in LAMMPS                                          | Analytical bond-order potential (ABOP)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| $$E=\frac{1}{2}\sum_{i}\sum_{j\neq i}V_{ij}$$                | $$E=\sum_{i}\sum_{j>i}V_{ij}$$                              |
| $$V_{ij}=f_\mathrm{C}(r_{ij}+\delta)[f_\mathrm{R}(r_{ij}+\delta)+b_{ij}f_\mathrm{A}(r_{ij}+\delta)]$$ | $$V_{ij}=f_\mathrm{C}(r_{ij})[V_\mathrm{R}(r_{ij})-\bar{b_{ij}}V_\mathrm{A}(r_{ij})]$$ |
| $$f_\mathrm{C}(r)=\left\{\begin{array}{ll}1, & r <R-D \\\frac{1}{2}-\frac{1}{2}\sin\left(\frac{\pi}{2}\frac{r-R}{D}\right), & R-D<r<R+D \\0,&r>R+D\end{array} \right.$$ | $$f_\mathrm{C}(r)=\left\{\begin{array}{ll}1, & r \leq R-D \\\frac{1}{2}-\frac{1}{2}\sin\left[\frac{\pi}{2D}(r-R)\right], & |R-r|<D \\0,&r\geq R+D\end{array} \right.$$ |
| $$f_\mathrm{R}(r)=A\exp(-\lambda_{1}r)$$                     | $$V_\mathrm{R}(r_{ij})=\frac{D_0}{S-1}\exp\left[-\beta\sqrt{2S}(r_{ij}-r_{0})\right]$$ |
| $$f_\mathrm{A}(r)=-B\exp(-\lambda_{2}r)$$                    | $$V_\mathrm{A}(r_{ij})=\frac{SD_0}{S-1}\exp\left[-\beta\sqrt{2/S}(r_{ij}-r_{0})\right]$$ |
| $$b_{ij}=\left(1+\beta^{n}\zeta_{ij}^{n}\right)^{-\frac{1}{2n}}$$ | $$\bar{b_{ij}}=\frac{b_{ij}+b_{ji}}{2}$$                    |
|                                                              | $$b_{ij}=(1+\chi_{ij})^{-1/2}$$                              |
| $$\zeta_{ij}=\sum_{k\neq i,j}f_\mathrm{C}(r_{ik}+\delta)g\left[\theta_{ijk}(r_{ij},r_{ik})\right]\exp\left[\lambda_{3}^{m}(r_{ij}-r_{ik})^{m}\right]$$ | $$\chi_{ij}=\sum_{k(\neq i,j)}f_\mathrm{C}(r_{ik})g_{ik}(\theta_{ijk})\omega_{ijk}\exp[\alpha_{ijk}(r_{ij}-r_{ik})]$$ |
| $$g(\theta)=\gamma_{ijk}\left[1+\frac{c^2}{d^2}-\frac{c^2}{d^2+(\cos\theta-\cos\theta_{0})^{2}}\right]$$ | $$g_{ik}(\theta_{ijk})=\gamma_{ik}\left[1+\frac{c^2_{ik}}{d^2_{ik}}-\frac{c^2_{ik}}{d^2_{ik}+(h_{ik}+\cos\theta_{ijk})^{2}}\right]$$ |
 

$D_0$ and $r_0$: the bond energy and length of a dimer.   
 
$\beta$ and $S$: fitting parameters that control the shape of the pair potential.

From the parameters $r_0$, $D_{0}$, $S$, $\beta$, $\alpha$, $\omega$, and $h$ given in the ABOP, we can obtain the parameters $A$, $B$, $\lambda_{1}$, $\lambda_{2}$, $\lambda_{3}$, $\gamma$, and $\cos\theta_{0}$ in the Tersoff_1 format of LAMMPS  according to the followings:
$\lambda_{1}   =   \beta\sqrt{2S}$,  $\lambda_{2}  =  \beta\sqrt{2/S}$,  $A=\frac{D_{0}}{S-1}\exp(\lambda_{1}r_{0})$, $B = \frac{SD_{0}}{S-1}\exp(\lambda_{2}r_{0})$, $\lambda_{3}  =  \alpha$ with $m=1$,  $\cos\theta_{0}  =  -h $, $\gamma = \omega\gamma$, 
where $n$ = 1, $\beta$ = 1, $m$ = 1 in Tersoff_1 format of LAMMPS.

##  Data format in Tersoff file with a“.tersoff” suffix

 Lines that are not blank or comments (starting with #) define parameters for a triplet of elements.  The parameters in a single entry correspond to coefficients in the formula above:

| Tersoff_1 | element 1                                  | element 2                          | element 3                                               | $m$ | $\gamma$       | $\lambda_{3}$  | $c$ | $d$ | $\cos\theta_{0}$         | $n$ | $\beta$ | $\lambda_{2}$   | $B$                                        | $R$          | $D$          | $\lambda_{1}$    | $A$                                       |
| --------- | ------------------------------------------ | ---------------------------------- | ------------------------------------------------------- | ----- | ---------------- | ---------------- | ----- | ----- | -------------------------- | ----- | --------- | ------------------- | -------------------------------------------- | -------------- | -------------- | ------------------ | ------------------------------------------- |
| Note      | the center of atom in a 3-body interaction | the atom bonded to the center atom | the atom influencing the 1-2 bond in a bond-order sense |       |                  | 1/distance units |       |       | can be a value < -1 or > 1 |       |           | 1/distance units    | energy units                                 | distance units | distance units | 1/distance units   | energy units                                |
|           |                                            |                                    |                                                         | 1     | $\omega\gamma$ | $\alpha$       |       |       | $-h$                     | 1     | 1         | $\beta\sqrt{2/S}$ | $\frac{SD_{0}}{S-1}\exp(\lambda_{2}r_{0})$ | $R$          | $D$          | $\beta\sqrt{2S}$ | $\frac{D_{0}}{S-1}\exp(\lambda_{1}r_{0})$ |

* The $n$, $\beta$, $\lambda_2$, $B$, $\lambda_1$, and $A$ parameters are only used for two-body interactions. 
* The $m$, $\gamma$, $\lambda_3$, $c$, $d$, and $\cos\theta_0$ parameters are only used for three-body interactions. 
*  The $R$ and $D$ parameters are used for both two-body and three-body interactions.
* The non-annotated parameters are unitless.  
* The value of $m$ must be 3 or 1.
* The Tersoff potential file must contain entries for all the elements listed in the pair_coeff command.  It can also contain entries for additional elements not being used in a particular simulation; LAMMPS ignores those entries.
* For a **single-element** simulation, only a **single entry** is required (e.g. SiSiSi).  For a **two-element** simulation, the file must contain **8 entries** (for SiSiSi, SiSiC, SiCSi, SiCC, CSiSi, CSiC, CCSi, CCC), that specify Tersoff parameters for all permutations of the two elements interacting in three-body configurations.  Thus for **3 elements**, **27 entries** would be required, etc.
* The first element in the entry is the center atom in a three-body interaction and it is bonded to the second atom and the bond is influenced by the third atom.  
  * Thus an entry for SiCC means Si bonded to a C with another C atom influencing the bond.  
  * Thus three-body parameters for SiCSi and SiSiC entries will not, in general, be the same.  The parameters used for the two-body interaction come from the entry where the second element is repeated. 
  * Thus the two-body parameters for Si interacting with C, comes from the SiCC entry.

* The parameters used for a particular three-body interaction come from the entry with the corresponding three elements.  The parameters used only for two-body interactions ( $n$, $\beta$, $\lambda_{2}$ , $B$, $\lambda_{1}$, and $A$) in entries whose second and third element are different (e.g. SiCSi) are not used for anything and can be set to 0.0 if desired.


# W-C
The WC potential is taken from 

Ref.1: N. Juslin, P. Erhart, P. Tr&#228;skelin, J. Nord, K. O. E. Henriksson, K. Nordlund, E. Salonen, and K. Albe, *J. Appl. Phys.*, **98**, 123520(2005); DO: [10.1063/1.2149492](https://doi.org/10.1063/1.2149492).

Ref.2: M.V.G. Petisme, M.A. Gren, G. Wahnstr&#246;m, *Int. J. Refract. Hard Met.*, **49**, 75--80(2015); DOI: [10.1016/j.ijrmhm.2014.07.037](https://doi.org/10.1016/j.ijrmhm.2014.07.037).

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

Ref. 5: P. Erhart, N. Juslin, O. Goy, K. Nordlund, R. M&#252;ller, and K. Albe, *J. Phys.: Condens. Matter* **18** (2006)6585-6605; DOI: [10.1088/0953-8984/18/29/003](http://dx.doi.org/10.1088/0953-8984/18/29/003).

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

Ref. 9: J. Byggm&#228;star, E. A. Hodille, Y. Ferro, and K. Nordlund, *J. Phys.: Condens. Matter*, **30**, 135001(2018); DOI: [10.1088/1361-648X/aaafb3](https://doi.org/10.1088/1361-648X/aaafb3).

To describe repulsive short-range interactions more accurately,  the universal repulsive Ziegler-Biersack-Littmark (ZBL) potential V<sub>ZBL</sub> (r<sub>ij</sub>) is used jointly with the original potential V<sub>ij</sub>.

V'<sub>ij</sub> = F(r<sub>ij</sub>) V<sub>ij</sub> + [1-F(r<sub>ij</sub>)] V<sub>ZBL</sub>

F(r<sub>ij</sub>) is Fermi function, i.e., 1/[1+exp(-b<sub>f</sub> (r<sub>ij</sub> -r<sub>f</sub>))]

|  Parameters   | Be-Be | O-O  | Be-O |
| :-----------: | :---: | :--: | :--: |
| b<sub>f</sub> | 15.0  | 12.0 | 15.0 |
| r<sub>f</sub> |  0.8  | 0.5  | 0.8  |


# Be-C
The Be-C potential is taken from 

Ref. 10: C. Bj&#246;rkas, N. Juslin, H. Timko, K. V&#246;rtler, K. Nordlund, K. Henriksson, and P. Erhart, *J. Phys.: Condens. Matter*, **21**, 445002(2009); DOI: [10.1088/0953-8984/21/44/445002](http://dx.doi.org/10.1088/0953-8984/21/44/445002).

To describe repulsive short-range interactions more accurately,  the universal repulsive Ziegler-Biersack-Littmark (ZBL) potential V<sub>ZBL</sub> (r<sub>ij</sub>) is used jointly with the original potential V<sub>ij</sub>.

V'<sub>ij</sub> = F(r<sub>ij</sub>) V<sub>ij</sub> + [1-F(r<sub>ij</sub>)] V<sub>ZBL</sub>

F(r<sub>ij</sub>) is Fermi function, i.e., 1/[1+exp(-b<sub>f</sub> (r<sub>ij</sub> -r<sub>f</sub>))]

|  Parameters   | Be-Be | C-C  | Be-C |
| :-----------: | :---: | :--: | :--: |
| b<sub>f</sub> | 15.0  | 8.0  | 16.0 |
| r<sub>f</sub> |  0.8  | 0.6  | 0.7  |

# W-N & W
The W-N potential is taken from 

Ref. 11:  J. Polvi, K. Heinola, and K. Nordlund, *Modelling Simul. Mater. Sci. Eng.*, **24**, 065007(2016); DOI: [10.1088/0965-0393/24/6/065007](http://dx.doi.org/10.1088/0965-0393/24/6/065007).

To describe repulsive short-range interactions more accurately,  the universal repulsive Ziegler-Biersack-Littmark (ZBL) potential V<sub>ZBL</sub> (r<sub>ij</sub>) is used jointly with the original potential V<sub>ij</sub>.

V'<sub>ij</sub> = F(r<sub>ij</sub>) V<sub>ij</sub> + [1-F(r<sub>ij</sub>)] V<sub>ZBL</sub>

F(r<sub>ij</sub>) is Fermi function, i.e., 1/[1+exp(-b<sub>f</sub> (r<sub>ij</sub> -r<sub>f</sub>))]

|  Parameters   | W-W | N-N  | W-N |
| :-----------: | :---: | :--: | :--: |
| b<sub>f</sub> | 12.0  | 12.0  | 12.0 |
| r<sub>f</sub> |  1.3  | 0.5  | 0.4  |

The parameters for W-W are taken from 

Ref. 12: T. Ahlgren, K. Heinola, N. Juslin, and A. Kuronen, *J. Appl. Phys.* **107**, 033516(2010); DOI:[10.1063/1.3298466](http://dx.doi.org/10.1063/1.3298466).


# Be-W
The Be-W potential is taken from 

Ref. 13: C. Bj&#246;rkas, K. O. E. Henriksson, M. Probst, and K. Nordlund, *J. Phys.: Condens. Matter*, **22**, 352206(2010); DOI: [10.1088/0953-8984/22/35/352206](http://dx.doi.org/10.1088/0953-8984/22/35/352206).

To describe repulsive short-range interactions more accurately,  the universal repulsive Ziegler-Biersack-Littmark (ZBL) potential V<sub>ZBL</sub> (r<sub>ij</sub>) is used jointly with the original potential V<sub>ij</sub>.

V'<sub>ij</sub> = F(r<sub>ij</sub>) V<sub>ij</sub> + [1-F(r<sub>ij</sub>)] V<sub>ZBL</sub>

F(r<sub>ij</sub>) is Fermi function, i.e., 1/[1+exp(-b<sub>f</sub> (r<sub>ij</sub> -r<sub>f</sub>))]

|  Parameters   | Be-Be | W-W  | Be-W |
| :-----------: | :---: | :--: | :--: |
| b<sub>f</sub> | 15.0  | 12.0  | 13.0 |
| r<sub>f</sub> |  0.8  | 1.3  | 1.3  |

# Fe
The Fe potential is taken from 

Ref. 14:  M. M&#252;ller, P. Erhart and K. Albe, *J. Phys.: Condens. Matter*, **19**, 326220(2007); DOI: [10.1088/0953-8984/19/32/326220](http://dx.doi.org/10.1088/0953-8984/19/32/326220).

# Mo-Er
The Mo-Er potential is taken from 

Ref. 15:  Q. Q. Sun, T. Yang, L. Yang, S. M. Peng, X. G. Long, X. S. Zhou, X. T. Zu, and F. Gao, *Modelling Simul. Mater. Sci. Eng.*, **24**, 045018(2016); DOI: [10.1088/0965-0393/24/4/045018](http://dx.doi.org/10.1088/0965-0393/24/4/045018).

# Si & Ge
The Si and Ge potentials are taken from 

Ref. 16:  Brian Andrew Gillespie, *Bond Order Potentials for Group IV Semiconductors*, University of Virginia, 2009; URL: [https://www2.virginia.edu/ms/research/wadley/Thesis/BGillespiePhD.pdf](https://www2.virginia.edu/ms/research/wadley/Thesis/BGillespiePhD.pdf).
