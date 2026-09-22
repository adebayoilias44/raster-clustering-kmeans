# Raster Clustering with K-Means

A lightweight, dependency-minimal pipeline for applying unsupervised machine learning to multispectral raster imagery. This project demonstrates how to convert a geospatial raster into a machine-learning-ready feature matrix and apply K-means clustering to reveal spatial patterns without any labeled training data.

## Overview

Most geospatial machine learning workflows rely on labeled training data (supervised learning) and often require pulling imagery from platforms like Google Earth Engine. This project takes a different approach: it uses a locally available multi-band GeoTIFF and applies unsupervised clustering, making it a fast, reproducible entry point into raster-based ML with zero external authentication or API dependencies.

## What it does

1. Reads a multi-band GeoTIFF using `rasterio`
2. Reshapes the raster from its native (bands, height, width) array structure into a 2D feature matrix, where each row is one pixel and each column is one spectral band
3. Applies K-means clustering to group pixels by spectral similarity, with no ground truth or labels required
4. Reshapes the cluster assignments back into spatial form and visualizes the result alongside the original image

## Why unsupervised clustering

Unlike supervised classifiers (e.g., Random Forest), K-means requires no training labels. It groups pixels purely based on similarity in spectral feature space, which makes it useful for:
- Quick exploratory analysis of new imagery before ground truth data is available
- Identifying natural spectral groupings (e.g., water, vegetation, bare soil, built-up) as a first-pass land cover assessment
- Learning the raster-to-ML pipeline mechanics independent of labeling effort

## Tech stack

- Python
- rasterio (raster I/O and geospatial metadata handling)
- NumPy (array reshaping and manipulation)
- scikit-learn (K-means clustering)
- Matplotlib (visualization)

## Key concepts demonstrated

- Reading and interpreting raster band structure and geospatial metadata
- Converting 3D raster arrays into 2D ML feature matrices (and back)
- Unsupervised learning fundamentals (K-means, cluster initialization, convergence)
- Visual comparison as an evaluation approach in the absence of labeled data

## Limitations

K-means clusters are unlabeled by nature — cluster identities (e.g., "vegetation" vs. "water") must be manually inferred by visual inspection, and cluster numbering is not consistent across runs. This project is intended as a foundational exercise, not a production-grade land cover classification tool.

## Next steps

Planned extensions include applying this same pipeline to Sentinel-2 imagery over Ikeja, Lagos, and comparing unsupervised clustering results against supervised Random Forest classification on the same scene.

## Author

Adebayo — Postgraduate researcher in GIS and remote sensing, Federal University of Technology, Akure (FUTA)
