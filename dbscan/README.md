# NYC Taxi Pickup Clustering with DBSCAN

## Overview

This project uses the **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** algorithm to identify clusters of taxi pickup locations in New York City.

The project focuses on discovering areas with high concentrations of taxi pickups using latitude and longitude coordinates.

## Dataset

The dataset contains NYC taxi trip records, including pickup location coordinates.

For computational efficiency, a **random sample of 10,000 trips** was used for clustering.

## Approach

1. Selected 10,000 random taxi trips.
2. Extracted pickup latitude and longitude.
3. Converted coordinates from degrees to radians.
4. Applied DBSCAN using the **Haversine distance**.
5. Experimented with `eps` and `min_samples`.
6. Analyzed cluster sizes and noise points.
7. Calculated the geographic center of each cluster.
8. Visualized the clusters and their centers.

## Algorithm

**DBSCAN** groups points based on their spatial density and identifies points that do not belong to sufficiently dense regions as noise.

The final configuration used:

* `eps = 0.0001` radians
* `min_samples = 10`
* `metric = 'haversine'`

The Haversine metric was used because latitude and longitude represent geographic coordinates on the Earth's surface.

## Key Findings

The clustering revealed several areas with concentrated taxi pickup activity, including areas around Manhattan, Brooklyn, Queens, and major airport regions.

DBSCAN also identified a small number of pickup locations as noise, meaning they did not belong to sufficiently dense clusters.

## Tools & Libraries

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Jupyter Notebook

## Project Goal

The goal of this project was to practice unsupervised machine learning, particularly density-based clustering and the use of geographic data.

