# Bar Surfing
Bars are non-axisymmetric perturbations that are drivers of changes in the shape of isolated galaxies over time.

The goal of this project is to use test particle simulations[^1] to understand if a cluster can survive being at a stable point in a barred galaxy as the stable point moves outward towards the solar circle[^2] due to a decelerating bar. 

The wrapper used to slow the bar was created by [Dr. Kathryne "Kate" Daniel](https://github.com/katedaniel/Slowing-Bar).

[galpy: A Python Library for Galactic Dynamics, Jo Bovy (2015), Astrophys. J. Supp., 216, 29 (arXiv/1412.3451)](https://iopscience.iop.org/article/10.1088/0067-0049/216/2/29/pdf)

[^1]: A type of simulation where particles interact with the potential(s) imposed on them.
[^2]: The radius at which the Sun orbits around the center of the galaxy.

# Table of Contents
1. [Introduction](#Introduction)
2. [Data Collection](#Data-Collection)
3. [Data Analysis](#Data-Analysis)
4. [Simulations](#Simulations)
5. [Conclusions and Future Directions](#Conclusions-and-Future-Directions)
6. [Description of Repository](#Description-of-Repository)
7. [Movies](#Movies)

## Introduction
Star clusters are classified as either open or globular clusters. The stars in these clusters have similar chemical components presumably due to the stars being born from the fragments of the same molecular cloud (Harris & Pudritz, 1994). The mass of clusters decrease over time due to evaporation (Binney & Tremaine, 2008).

Using **tracer particle simulations**, I want to answer the following questions:
* Does the decelerating galactic bar affect the orbits of stars in these clusters?
* Does the cluster survive the growth and deceleration of the bar?
  *  What percentage of stars remain in the cluster?

## Data Collection
The data was created using <tt>[`galpy`](http://github.com/jobovy/galpy)</tt> v.1.8.1.dev0. The data consists of the phasespace &mdash; the Cartesian and cylindrical coordinates and their respective velocities &mdash; of each particle in the cluster.
* Cartesian phasespace (x, y, z, v<sub>x</sub>, v<sub>y</sub>, v<sub>z</sub>)
  * Cartesian coordinate (x, y, z)
  * Cartesian velocity (v<sub>x</sub>, v<sub>y</sub>, v<sub>z</sub>)
* Cylindrical phasespace (R, $\phi$, z, v<sub>R</sub>, v<sub>$\phi$</sub>, v<sub>z</sub>)
  * Cylindrical coodinate (R, $\phi$, z)
  * Cylindrical velocity (v<sub>R</sub>, v<sub>$\phi$</sub>, v<sub>z</sub>)

**Steps to obtain data for initial conditions:**
* Step 1: Generate the data
  * [Import](https://github.com/oliviamcauley/Bar_Surfing/blob/8029fd29a6e5ee13e61e3ac0c9f9f7e2848357f8/Cluster_IC/McAuley_Imports.ipynb) necessary packages
  * Add [scaling factors](https://github.com/oliviamcauley/Bar_Surfing/blob/8029fd29a6e5ee13e61e3ac0c9f9f7e2848357f8/Cluster_IC/McAuley_ScaleFactors.ipynb) that will convert galpy's internal units to physical units and vice versa
  * Create sample of particles that will be the cluster[^3] using the [Plummer potential](https://github.com/oliviamcauley/Bar_Surfing/blob/8029fd29a6e5ee13e61e3ac0c9f9f7e2848357f8/Cluster_IC/McAuley_PlummerPotential.ipynb)
* Step 2: [Integrate](https://github.com/oliviamcauley/Bar_Surfing/blob/8029fd29a6e5ee13e61e3ac0c9f9f7e2848357f8/Cluster_IC/McAuley_IntegrateIC.ipynb) the data
* Step 3: [Save](https://github.com/oliviamcauley/Bar_Surfing/blob/8029fd29a6e5ee13e61e3ac0c9f9f7e2848357f8/Cluster_IC/McAuley_SaveOrbitsIC.ipynb) the data
Following the steps above, run the the Jupyter notebook called [McAuley_Run.ipynb](https://github.com/oliviamcauley/Bar_Surfing/blob/45c5897bb3743ddbf32652d97a424be89b58d2a9/Cluster_IC/McAuley_Run_IC.ipynb) in the *Cluster_IC* folder to create the initial conditions of the cluster.

[^3]: See Appendix A in PhD Dissertation for derivation of the scaling Plummer parameter.

**Steps to obtain data for the growing bar simulations:** <br />
> [!NOTE]  
> *This contains the M, MP, MB, and MBP simulations*
* Step 1: Generate the data
  * [Import](https://github.com/oliviamcauley/Bar_Surfing/blob/e696f1c08b686e9fa6dde2825e7f9b9b7d8a8349/Growing-Bar/McAuley_Imports.ipynb) necessary packages
* Step 2: Set up [Growing Bar](https://github.com/oliviamcauley/Bar_Surfing/blob/e696f1c08b686e9fa6dde2825e7f9b9b7d8a8349/Growing-Bar/McAuley_DehnenBar.ipynb)
* Step 3: Upload [initial conditions](https://github.com/oliviamcauley/Bar_Surfing/blob/e696f1c08b686e9fa6dde2825e7f9b9b7d8a8349/Growing-Bar/ICs_File.ipynb) file &mdash; You just created a cluster!
> [!Warning]
> Make sure you input the correct path directory since the saved data from Step 3 of **Steps to obtain data for initial conditions** is being uploaded here.
* Step 4: Define appropriate [timestep](https://github.com/oliviamcauley/Bar_Surfing/blob/e696f1c08b686e9fa6dde2825e7f9b9b7d8a8349/Growing-Bar/Timescale_Calculator.ipynb)
* Step 5: Find [stable point](https://github.com/oliviamcauley/Bar_Surfing/blob/e696f1c08b686e9fa6dde2825e7f9b9b7d8a8349/Growing-Bar/FindL5.ipynb)
* Step 6: Define single particle that [Plummer potential](https://github.com/oliviamcauley/Bar_Surfing/blob/e696f1c08b686e9fa6dde2825e7f9b9b7d8a8349/Growing-Bar/MovePlummer.ipynb) will follow
* Step 7: [Integrate](https://github.com/oliviamcauley/Bar_Surfing/blob/e696f1c08b686e9fa6dde2825e7f9b9b7d8a8349/Growing-Bar/IntegrateSingleParticle.ipynb) orbit of the single particle
>[!Warning]
> Make sure you are integrating over the correct potential and that the correct folders are in the correct directory.
* Step 8: [Shift](https://github.com/oliviamcauley/Bar_Surfing/blob/e696f1c08b686e9fa6dde2825e7f9b9b7d8a8349/Growing-Bar/ShiftClusterOrbit.ipynb) cluster to be at the stable point
* Step 9: [Integrate](https://github.com/oliviamcauley/Bar_Surfing/blob/e696f1c08b686e9fa6dde2825e7f9b9b7d8a8349/Growing-Bar/IntegrateClusterOrbit.ipynb) the orbit of the shifted cluster
* Step 10: Save the data (This is done in the previous step for you)

Following the steps above, run the the Jupyter notebook called [Run_IntegrateClusterDifferentPotentials.ipynb](https://github.com/oliviamcauley/Bar_Surfing/blob/e696f1c08b686e9fa6dde2825e7f9b9b7d8a8349/Growing-Bar/Run_IntegrateClusterDifferentPotentials.ipynb) in the *Growing-Bar* folder to create the M, MP, MB, and MBP simulations.

**Steps to obtain data for the growing and decelerating bar simulations:** <br />
*This contains the MS and MSP simulations*
* Step 1: Generate the data
* Step 2: Define appropriate timestep
* Step 3: Integrate the data
* Step 4: Save the data

## Data Analysis
The following plots show the fraction of the number of bound stars in the cluster as a function of time in Gyr (1 Gyr = 1 billion years) for the (left/top on mobile) M; MP; MB; and MBP, and (right/bottom on mobile) M; MP; MS; and MSP simulations. <br /> The gray vertical line denotes the time that the bar is fully grown. 
The data shows that the Plummer potential is the key factor holding the cluster together. Including a bar gives the cluster an additional binding factor. It was found that the cluster retains 95% of its star members in the MBP and MSP simulations. <br />
![bound_fraction_GrowBar_image](https://github.com/user-attachments/assets/ea375403-d3fe-45f2-96fc-ee305c682940)
![bound_faction_SB_image](https://github.com/user-attachments/assets/3c153eb2-e4f6-461b-a49f-80feb94d89fc)


## Simulations
There are 6 simulations that I created based on getting inital conditions from a distribution function and placing the cluster at the stable point in the barred disk. The cluster was placed in 6 different conditions. The conditions and results were:
* A disk galaxy, created using an underlying Milky Way potential, where it sheared. This is dubbed the **M simulation**.
* A disk galaxy with a Plummer potential that increased the number of particles that stayed within the 95th percentile radius of the cluster. This is called the **MP simulation**.
* A growing barred disk galaxy where the cluster sheared a little, but was still held together. This is the **MB simulation**.
* A growing barred disk galaxy with a Plummer potential where the cluster was held tight together with leading and trailing arms. This is named the **MBP simulation**.
* A growing and slowing barred disk galaxy where the orbit of the stars moved outward for a couple million years before leaving the stable region and shearing. This is labeled the **MS simulation**.
* A growing and slowing barred disk galaxy with a Plummer potential where the cluster was held together with leading and trailing arms after leaving the stable region. This is the **MSP simulation**.

## Conclusions and Future Directions
This study found that the cluster was able to surf the bar. The decelerating bar was able to move the stellar orbits residing at this stable region radially outward for an extended time. The focus of this project was to create 6 simulations where the cluster interacted with different potentials. The behavior of the stellar orbits in these different environments were recorded via movies with data analysis that supported what was seen in the movies. Next steps would be adding a vertical component to the position of the cluster to observe if the cluster could exhibit a tighter orbit about the stable point. 

## Description of Repository
This repository consists of the *Cluster_IC* folder which creates the initial conditions for the simulations, the *Growing-Bar* folder which creates the growing bar simulations, and the *Slowing-Bar* folder which is the prescription we use to decelerate the growing bar.

## Movies
The animation for a cluster shifted to be at the stable point (if a bar pertubation was to be added) integrated over the:

* **Milky Way potential (M simulation):**

https://github.com/oliviamcauley/Bar_Surfing/assets/54736303/b01ab85d-41fa-4720-9863-6fa1e5dd8df7

* **Milky Way and Plummer potentials (MP simulation):**

https://github.com/oliviamcauley/Bar_Surfing/assets/54736303/8808c58c-979e-478e-a749-ef83ee747ef2

* **Milky Way and Bar potentials (MB simulation):**

https://github.com/oliviamcauley/Bar_Surfing/assets/54736303/e3ac74fc-7fad-4190-862d-b51b3e35e946

* **Milky Way, Dehnen Bar, and Plummer potentials (MBP simulation):**

https://github.com/oliviamcauley/Bar_Surfing/assets/54736303/1dfc3554-8ead-4ade-b00f-0e3016eadd84

* **Milky Way and Growing \& Slowing Dehnen Bar (MS simulation)**

[MS_224kms_4Gyr.mp4.zip](https://github.com/user-attachments/files/15992819/MS_224kms_4Gyr.mp4.zip)

* **Milky Way, Growing \& Slowing Dehnen Bar, and Plummer (MSP simulation)**

[MSP_224kms_4Gyr.mp4.zip](https://github.com/user-attachments/files/15979888/MSP_224kms_4Gyr.mp4.zip)
