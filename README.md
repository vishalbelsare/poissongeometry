[![Python](https://img.shields.io/pypi/pyversions/poissongeometry.svg?style=plastic)]()
[![PyPI](https://badge.fury.io/py/poissongeometry.svg)](https://pypi.org/project/poissongeometry/)
[![Documentation](https://img.shields.io/badge/api-reference-blue.svg)](https://colab.research.google.com/drive/1XYcaJQ29XwkblXQOYumT1s8_00bHUEKZ) 
[![License](https://img.shields.io/badge/license-MIT-blue)](https://github.com/git/git-scm.com/blob/master/MIT-LICENSE.txt)
![GitHub last commit](https://img.shields.io/github/last-commit/appliedgeometry/poissongeometry)

---

# `PoissonGeometry`
A Python module for (local) Poisson-Nijenhuis calculus on Poisson manifolds, with the following functions:

| **poisson_bracket**         | **hamiltonian_vf**              | **lichnerowicz_poisson_operator**  |
|:---------------------------:|:-------------------------------:|:----------------------------------:|
| **modular_vf**              | **curl_operator**               | **flaschka_ratiu_bivector**        |
| **sharp_morphism**          | **bivector_to_matrix**          | **jacobiator**                     |
| **one_forms_bracket**       | **gauge_transformation**        | **is_unimodular_homogeneous** *    |
| **linear_normal_form_R3**   | **isomorphic_lie_poisson_R3**   | **is_in_kernel** *                 |
| **is_poisson_tensor** *     | **is_casimir** *                | **is_poisson_vf** *                | 
|                             | **is_poisson_pair** *           |                                    |


**Remark.** We  have  indicated  with  an  asterisk  (*)  the  six  methods  whose  implementations  require  testing  whether  a  symbolic  expression  is  zero.   These  are naturally limited by theoretical computational constraints.


This repository accompanies our paper ['On Computational Poisson Geometry I: Symbolic Foundations'](https://arxiv.org/abs/1912.01746).

<!-- For more information you can read the [wiki](https://github.com/mevangelista-alvarado/poisson_geometry/wiki) this project. or the our [documentation]()-->

## Motivation
Some of the functions in this module have been used to obtain the results in these articles:

 * L.  C.  Garcia-Naranjo,  P.  Suárez-Serrato & R.  Vera, <br/>
 [Poisson Structures on Smooth 4-Manifolds](https://link.springer.com/article/10.1007/s11005-015-0792-8), <br/> 
   Lett. Math. Phys. 105, 1533-1550 (2015)
   
 * P. Suárez-Serrato & J. Torres-Orozco, <br/>
 [Poisson Structures on Wrinkled Fibrations](https://link.springer.com/article/10.1007/s40590-015-0072-8),  <br/>
   Bol. Soc.Mat. Mex. 22, 263-280 (2016)
   
 * P. Suárez-Serrato, J. Torres Orozco, & R. Vera, <br/>
 [Poisson and Near-Symplectic Structures on Generalized Wrinkled Fibrations in Dimension 6](https://link.springer.com/article/10.1007/s10455-019-09651-2),  <br/>
   Ann. Glob. Anal. Geom. (2019) 55, 777-804 (2019)
   
 * M. Evangelista-Alvarado, P. Suárez-Serrato, J. Torres-Orozco & R. Vera, <br/>
 [On Bott-Morse Foliations and their Poisson Structures in Dimension 3](http://journalofsingularities.org/volume19/article2.html),  <br/>
   Journal of Singularities 19, 19-33 (2019)

## 🚀
<!--- #### Testing: --->
 * __Run our tutorial on Colab__ [English](https://colab.research.google.com/drive/1XYcaJQ29XwkblXQOYumT1s8_00bHUEKZ) / [Castellano](https://colab.research.google.com/drive/1F9I2TcrhSz0zRZSuALEWldxgw-AL6pOK)
   
 * __Run on your local machine__
   * Clone this repository on your local machine.
   * Open a terminal with the path where you clone this repository.
   * Create a virtual environment,(see this [link](https://gist.github.com/mevangelista-alvarado/8ee2fd663e7446e543fc04eacce0f303))
   * Install the requirements:
      ```
      (venv_name) C:Users/dekstop/poisson$ pip install poissongeometry
      ```
   * Open python terminal to start:
      ```
      (venv_name) C:Users/dekstop/poisson$ python
      ```
   * **Import PoissonGeometry module:**
      ```
      >>> from poisson.poisson import PoissonGeometry
      ```  
<!--  * Testing the class.
     For example we want convert to matriz the bivector <a href="https://www.codecogs.com/eqnedit.php?latex=$$\pi=x_{3}\frac{\partial}{\partial&space;x_{1}}\wedge\frac{\partial}{\partial&space;x_{2}}&space;-&space;x_{2}\frac{\partial}{\partial&space;x_{1}}\wedge\frac{\partial}{\partial&space;x_{3}}&space;&plus;&space;x_{1}\frac{\partial}{\partial&space;x_{2}}\wedge\frac{\partial}{\partial&space;x_{3}}$$" target="_blank"><img src="https://latex.codecogs.com/gif.latex?$$\pi=x_{3}\frac{\partial}{\partial&space;x_{1}}\wedge\frac{\partial}{\partial&space;x_{2}}&space;-&space;x_{2}\frac{\partial}{\partial&space;x_{1}}\wedge\frac{\partial}{\partial&space;x_{3}}&space;&plus;&space;x_{1}\frac{\partial}{\partial&space;x_{2}}\wedge\frac{\partial}{\partial&space;x_{3}}$$" title="$$\pi=x_{3}\frac{\partial}{\partial x_{1}}\wedge\frac{\partial}{\partial x_{2}} - x_{2}\frac{\partial}{\partial x_{1}}\wedge\frac{\partial}{\partial x_{3}} + x_{1}\frac{\partial}{\partial x_{2}}\wedge\frac{\partial}{\partial x_{3}}$$" /></a>
     then <a href="https://www.codecogs.com/eqnedit.php?latex=\pi" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\pi" title="\pi" /></a> is equivalent to ```{(1,2): 'x3', (1,3): '-x2', (2,3): 'x1'}``` in this class.
     ```
     >>> from poisson import PoissonGeometry
     >>> # We instantiate the Poisson class for dimension 3
     >>> pg = PoissonGeometry(3)
     >>> pg.bivector_to_matrix({(1,2): 'x3', (1,3): '-x2', (2,3): 'x1'})
     Matrix([
     [  0,  x3, -x2],
     [-x3,   0,  x1],
     [ x2, -x1,   0]])
     ```
    
    This function has an option for output is in latex format string, for this, we change the flag latex_format to True (its default value is False) as shown below.
    
    ```
     >>> print(pg.bivector_to_matrix({(1,2): 'x3', (1,3): '-x2', (2,3): 'x1'}, latex_format=True))
       \left[\begin{array}{ccc}0 & x_{3} & - x_{2}\\- x_{3} & 0 & x_{1}\\x_{2} & - x_{1} & 0\end{array}\right]
    ```
    <!--For more information to how use this class you can read the [documentation]() or the our [wiki](https://github.com/mevangelista-alvarado/poisson_geometry/wiki)-->

<!--## TO DO
Calculate Poisson Cohomology with linear coefficients.-->

## Bugs & Contributions
Our issue tracker is at https://github.com/appliedgeometry/poissongeometry/issues. Please report any bugs that you find. Or, even better, if you are interested in our project you can fork the repository on GitHub and create a pull request.

## Licence 📄
MIT licence

## Authors ✒️
This work is developed and maintained by:
 * **Miguel Evangelista Alvarado** - [@mevangelista-alvarado](https://github.com/mevangelista-alvarado)
 * **Jose C. Ruíz Pantaleón** - [@jcrpanta](https://github.com/jcrpanta)
 * **Pablo Suárez Serrato** - [@psuarezserrato](https://github.com/psuarezserrato)

## Thanks for citing our work if you use it! 🤓 ##

```
@articleInfo{Evangelista-Alvarado Miguel Ángel 2021 Journal of Geometric Mechanics,
title = {On computational Poisson geometry I: Symbolic foundations},
journal = {Journal of Geometric Mechanics},
volume = {13},
number = {4},
pages = {607-628},
year = {2021},
issn = {1941-4889},
doi = {10.3934/jgm.2021018},
url = {/article/id/a7acc48a-54f1-4348-8b45-f5a31428bd29},
author = {Evangelista-Alvarado Miguel Ángel and Ruíz-Pantaleón José Crispín and Suárez-Serrato Pablo},
}
```
## Acknowledgments
This work was partially supported by the grants CONACyT, “Programa para un Avance Global e Integrado de la Matemática Mexicana” CONACyT-FORDECYT 26566 and "Aprendizaje Geométrico Profundo" UNAM-DGAPA-PAPIIT-IN104819. JCRP wishes to also thank CONACyT for a postdoctoral fellowship held during the production of this work.

---

<p align="center">
  <img src="https://www.matem.unam.mx/++theme++im-theme-blue/images/escudo_unam.png">
  <img src="https://www.matem.unam.mx/++theme++im-theme-blue/images/logo_imunam.png">
</p>

<!-- 
## Do not forget.
* Comment to others about this project 📢
* Cite this project if you use it 🤓.
* Finally, if you know one of the authors, invite him a beer🍺.
-->
