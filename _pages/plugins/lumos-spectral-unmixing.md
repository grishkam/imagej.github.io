---
mediawiki: LUMoS_Spectral_Unmixing
name: "LUMoS Spectral Unmixing"
title: LUMoS Spectral Unmixing
categories: [Color Processing,Colocalization]
initial-release-date: "June 2019"
team-founder: 'Tristan McRae'
team-maintainer: 'Tristan McRae'
---

{% include info-box source=' [GitHub](https://github.com/tristan-mcrae-rochester/Multiphoton-Image-Analysis/blob/master/Spectral%20Unmixing/Code/ImageJ-FIJI/LUMoS_Spectral_Unmixing.java)' %}

# Introduction

Learning Unsupervised Means of Spectra (LUMoS) is a blind spectral unmixing method that uses k-means clustering to separate different features of a fluorescence microscopy image into a multi-channel image in which each output channel corresponds to a single fluorophore.

# Spectral Overlap

Due to the overlapping emission spectra of fluorophores, fluorescence microscopy images often have bleed-through problems, leading to a false positive detection. This problem is almost unavoidable when the samples are labeled with three or more fluorophores and completely unavoidable when fluorophores outnumber detection channels.

<figure><img src="/media/plugins/spectral-overlap.png" title="spectral_overlap.png" width="1000" alt="spectral_overlap.png" /><figcaption aria-hidden="true">spectral_overlap.png</figcaption></figure>

# *K*-means clustering

*K*-means is an unsupervised learning clustering technique. Given a set of input datapoints, *k*-means clusters the points into *k* different groups based on their values. K-means defines clusters by iteratively calculating the centroid of each cluster and assigning datapoints to the nearest cluster centroid. This process is depicted below:

<img src="/media/k-means.png" width="600"/>

# *K*-means for spectral unmixing

In the context of spectral unmixing, the inputs to *k*-means are individual pixels. Each pixel is represented by a *1 x n* vector where *n* is the number of detection channels in the image. This vector is referred to as the "spectral signature" of the pixel. Pixels with similar spectral signatures are grouped into the same cluster. Each cluster is then represented as an inividual channel in the output image. The output channels correspond to unmixed fluorophores. This process will also separate background, autofluorescence and colocalization into distinct output channels.

<figure><img src="/media/plugins/spectral-unmixing-example.png" title="spectral_unmixing_example.png" width="800" alt="spectral_unmixing_example.png" /><figcaption aria-hidden="true">spectral_unmixing_example.png</figcaption></figure>

# Usage

To install the plugin in your ImageJ or Fiji installation, add the update site LUMoS. The procedure to follow an update site [can be found here](/update-sites/following).

Alternatively, a full Fiji distribution with LUMoS already packaged can be downloaded. Unlike the update site, this packaged download is PC only. [PC only download](https://www.urmc.rochester.edu/MediaLibraries/URMCMedia/multiphoton-core/documents/Fiji-app-for-LUMoS-spectral-unmixing.zip).

A user guide for this plugin with step by step instructions can be found [ here](/media/plugins/spectral-unmixing-user-guide.pdf).

# See Also

The following are alternative spectral unmixing ImageJ plugins. These plugins both use linear algebra based approaches. Linear unmixing approaches are not applicable in cases where fluorophores outnumber detection channels. Additionally, they both require manual ROI selection or single-fluorophore references which can be laborious to acquire. Apart from these constraints, both of these plugins can be very useful tools in the right settings.

[Spectral Unmixing Plugins](https://imagej.net/ij/plugins/spectral-unmixing.html) by Joachim Walter

[Spectral Unmixing Plugin](https://imagej.net/ij/plugins/spectral-unmixing-plugin.html) by Seth Gammon

# References

If you use this program to generate a publication, please cite the following:

\[1\] McRae TD, Oleksyn D, Miller J, Gao Y-R (2019) Robust blind spectral unmixing for fluorescence microscopy using unsupervised learning. PLoS ONE 14(12): e0225410. https://doi.org/10.1371/journal.pone.0225410

  
