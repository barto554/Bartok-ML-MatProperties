<h1 align="center"><strong>- Aletta Bartok Machine Learning Final Project Spring 2026 -</strong></h1>
<h2 align="center"><strong>ML to Predict Material Properties with CGCNN [Xie et al. 2018]</strong></h2>

Crystal Graph Convolutional Neural Networks (CGCNN) are used to predict material properties of periodically crystalline materials and to predict potentially stable materials for materials science and engineering applications. CGCNN allows for higher accuracy and speed, generalization, and scale compared to traditional methods of materials design, like Density Functional Theory (DFT). This repository includes the data used for the model training, validation, testing, and prediction of material properties for the final project for CHEM 2920: Machine Learning for Chemistry. All the `.cif` files have been downloaded from the Materials Project Database.

In this repository, there are three unique folders:

**root_dir_smallset:** All molecules provided by Xie et al. (2018) plus 5 new molecules.

- $NaCl$, $KCl$, $ZnS$, $BaTiO_3$, $TiO_2$, $C$ $(Graphite)$, $CsCl$, $Ge$, $Si$, $C$ $(Diamond)$

- $LiH$, $NaH$, $HBr$, $FeH$, $SnO$

**root_dir_largeset:** All molecules (from Xie et al. (2018), the small dataset, plus 15 new molecules).

- $NaCl$, $KCl$, $ZnS$, $BaTiO_3$, $TiO_2$, $C$ $(Graphite)$, $CsCl$, $Ge$, $Si$, $C$ $(Diamond)$

- $LiH$, $NaH$, $HBr$, $FeH$, $SnO$

- $LiP$, $CrF_6$, $NaAs$, $UCl_6$, $ZnAs_2$, $CuGe_2P_3$, $FeO$, $CoF_2$, $KN_3$, $KSb$, $VO_2$, $Zr_2Ni$, $TiGa$, $Co_3Ni$, $Ag$

**predict_dir:** 5 molecules for predicting, used for each best model to test MAE, same across all datasets for consistent testing.

- $KH$, $CaS$, $Ti_6O$, $CuO$, $Rb_2O$

Within each folder, two files are included: `id_prop.csv` and `atom_init.json`. The band gap values from the Materials Project Database are placed into a file named `id_prop.csv`, which is the "answer key" for the model, which is the file the model checks after it predicts the value. Through this file, the model is able to learn, in this case, the band gap, based on the structure of the molecule. Another file, `atom_init.json`, is also included in the file, which assigns a vector to each element, which is how the model essentially "knows" what a specific atom is before it even looks at the bonds.

Using the CGCNN model from Xie et al. (2018), a model to predict band gaps is created, varying the following conditions:

    **1.** Number of convolutional layers (1-5)
    
    **2.** Comparing the Xie et al. (2018) pre-trained band gap model (trained on over 46,000 materials from the Materials Project Database)

    **3.** Varying the train/validation/test split from 6/2/2 to 7/2/1

    **4.** Varying the batch size (2, 4, and the original 256)

Through these, it is possible to gain a better understanding of how the CGCNN model works to predict these material properties, how varying these parameters affects the CGCNN model, and why this model is the best for materials science and design.
