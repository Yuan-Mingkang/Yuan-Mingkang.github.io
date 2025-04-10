---
title: MPC-based multi-UAV trajectory tracking
summary: I use MPC-based control algorithms and the simulation environment of gym-pybullet-drones to implement trajectory tracking for multi-UAV simulations!
date: 2024-12-24
authors:
  - admin
tags:
  - MPC
  - trajectory tracking
  - multi-UAV
image:
---

Based on the open-source gym-pybullet-drones simulation environment, I developed a UAV simulation scenario that utilizes an MPC controller for trajectory tracking, supporting constraint definition and disturbances. I used the cf2 UAV model provided by gym-pybullet-drones, and I created UAV formation trajectories in Blender using the Skybrush plugin to facilitate algorithm verification. Ultimately, this resulted in a simulation effect of multiple UAVs tracking trajectories. 

## MPC

After finishing the training of the Distributed GAN, we collected the synthetic images from the Distributed GAN as the training set for different tasks. we use the trained Generator as a data provider to train DeepLab v3+ model for a semantic segmentation task on remote sensing images.

## Drone Swarm Choreography with Blender Skybrush

This project showcases professional drone light show creation using Blender Skybrush's specialized toolkit:  

**Workflow Implementation**:  
1. **Formation Design**:  
   - Built intricate 3D swarm patterns through Skybrush's node-based animation system  
   - Programmed synchronized maneuvers using keyframe-free procedural animation  

2. **Drone Path Baking**:  
   - Automated CSV trajectory exports for 30+ drones  
   - Maintained flight safety through built-in collision detection algorithms  

3. **Show Visualization**:  
   - Rendered photorealistic previsualizations with Blender's Eevee engine  
   - Generated real-time swarm previews with accurate LED color sequencing  

**Visual Display**:  
![](./1.gif)

**Technical Showcase**:  
- Timestamped CSV outputs for position (XYZ)   
- Automated path smoothing for fluid drone movements  
- Batch processing of 2000+ trajectory waypoints  

## Experiments

![](./data1.png)

Three different remote sensing datasets are used: City-OSM, WHU building dataset, and Kaggle Ship.The above figure shows that the image synthesis results are similar to traditional GAN.Distributed GAN networks can learn the data distribution of remote sensing images well.

![](./result1.png)

