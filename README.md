# Bar Surfing
This project used test particle simulations to understand if a cluster can survive being at a stable Lagrange point in the rotating frame as it moves outward towards the solar circle.

# Table of Contents
1. [Introduction](#Introduction)
2. [Data Collection](#Data-Collection)
3. [Modeling Approach](#Modeling-Approach)
4. [Conclusions and Future Directions](#Conclusions-and-Future-Directions)
5. [Description of Repository](#Description-of-Repository)
6. [Movies](#Movies)

## Introduction
Star clusters are classified as either open or globular clusters. The stars in these clusters have similar chemical components presumably due to the stars being born from the fragments of the same molecular cloud (Harris & Pudritz, 1994). The mass of clusters decrease over time due to evaporation (Binney & Tremaine, 2008). 

Using **tracer particle simulations**, I want to answer the following questions:
* Does the decelerating galactic bar affect the orbits of stars in these clusters?
* Does the cluster survive the growth and deceleration of the bar?
  *  What percentage of stars remain in the cluster?

## Data Collection
The data was created using <tt>[`galpy`](http://github.com/jobovy/galpy)</tt>. The data consists of the Cartesian and cylindrical coordinates and their respective velocities of each particle in the cluster.
* Cartesian coordinate (x, y, z)
* Cartesian velocity (v<sub>x</sub>, v<sub>y</sub>, v<sub>z</sub>)
* Cylindrical coodinate (R, $\phi$, z)
* Cylindrical velocity (v<sub>R</sub>, v<sub>$\phi$</sub>, v<sub>z</sub>)

**Steps to obtaining data for initial conditions:**
* Step 1: Generate the data
  * [Import](https://github.com/oliviamcauley/Bar_Surfing/blob/8029fd29a6e5ee13e61e3ac0c9f9f7e2848357f8/Cluster_IC/McAuley_Imports.ipynb) necessary packages
  * Add [scaling factors](https://github.com/oliviamcauley/Bar_Surfing/blob/8029fd29a6e5ee13e61e3ac0c9f9f7e2848357f8/Cluster_IC/McAuley_ScaleFactors.ipynb) that will convert galpy's internal units to physical units and vice versa
  * Create sample of particles that will be the cluster using the [Plummer potential](https://github.com/oliviamcauley/Bar_Surfing/blob/8029fd29a6e5ee13e61e3ac0c9f9f7e2848357f8/Cluster_IC/McAuley_PlummerPotential.ipynb)
* Step 2: [Integrate](https://github.com/oliviamcauley/Bar_Surfing/blob/8029fd29a6e5ee13e61e3ac0c9f9f7e2848357f8/Cluster_IC/McAuley_IntegrateIC.ipynb) the data
* Step 3: [Save](https://github.com/oliviamcauley/Bar_Surfing/blob/8029fd29a6e5ee13e61e3ac0c9f9f7e2848357f8/Cluster_IC/McAuley_SaveOrbitsIC.ipynb) the data

Following the steps above, run the the Jupyter notebook called [McAuley_Run.ipynb](https://github.com/oliviamcauley/Bar_Surfing/blob/45c5897bb3743ddbf32652d97a424be89b58d2a9/Cluster_IC/McAuley_Run_IC.ipynb) in the *Cluster_IC* folder to create the initial conditions of the cluster.

**Steps to obtaining data for the growing bar simulations:** <br />
*This contains the M, MP, MB, and MBP simulations*
* Step 1: Generate the data
  * [Import]() necessary packages
* Step 2: Define appropriate timestep
* Step 3: Integrate the data
* Step 4: Save the data

**Steps to obtaining data for the growing and decelerating bar simulations:** <br />
*This contains the MS and MSP simulations*
* Step 1: Generate the data
* Step 2: Define appropriate timestep
* Step 3: Integrate the data
* Step 4: Save the data
## Modeling Approach


## Conclusions and Future Directions

## Description of Repository
This repository consists of the *Cluster_IC* folder which creates the initial conditions for the simulations and the *Slowing-Bar* folder which is the prescription we use to decelerate the growing bar.

## Movies
The animation for a cluster shifted to be at the L4/5 (if a bar pertubation was to be added) integrated over the:

**Milky Way potential (M simulation):**

https://github.com/oliviamcauley/Bar_Surfing/assets/54736303/b01ab85d-41fa-4720-9863-6fa1e5dd8df7

**Milky Way and Plummer potentials (MP simulation):**

https://github.com/oliviamcauley/Bar_Surfing/assets/54736303/8808c58c-979e-478e-a749-ef83ee747ef2

The animation for a cluster shifted to be at the L4/5 integrated over the:

**Milky Way and Bar potentials (MB simulation):**

https://github.com/oliviamcauley/Bar_Surfing/assets/54736303/e3ac74fc-7fad-4190-862d-b51b3e35e946

**Milky Way, Dehnen Bar, and Plummer potentials (MBP simulation):**

https://github.com/oliviamcauley/Bar_Surfing/assets/54736303/1dfc3554-8ead-4ade-b00f-0e3016eadd84

**Milky Way and Growing \& Slowing Dehnen Bar (MS simulation)**

[MS_224kms_4Gyr.mp4.zip](https://github.com/user-attachments/files/15992819/MS_224kms_4Gyr.mp4.zip)

**Milky Way, Growing \& Slowing Dehnen Bar, and Plummer (MSP simulation)**

[MSP_224kms_4Gyr.mp4.zip](https://github.com/user-attachments/files/15979888/MSP_224kms_4Gyr.mp4.zip)
