---
title: Reporting Growth Mixture Models
author: ~
date: '2018-12-17'
slug: 
categories: ["GMM", "Mixture Modeling", "Reporting"]
tags: []
image:
  caption: ''
  focal_point: ''
linktitle: Reporting GMM
menu:
  post:
    parent: Posts
    weight: 2
---

I am currently wrapping up my work on a project investigating the alcoholic tendencies of adolesences.
The data come from a data study in the United Kingdom, and I was brought on the project to help with the analysis.
For this study, the aim was to investigate the presence of unobserved heterogeneity on the growth trajectories of this construct of 'alcoholic tendencies.' 
For this analysis, I implemented a Growth Mixture Model (GMM). 
A GMM is a very complex model that allows for the greatest flexibility in terms of statistical modeling. 
The aim is to uncover the presence of unobserved groups of people with qualitatively distinct growth patterns.
The term growth may be a little misleading as the pattern may be negative or no change may occur.
I will not dive into the complexities of the modeling of GMMs in this post.
The aim of this post is to show what I have found to be the most useful in terms of reporting GMMs from my readings. 

The source for these guidelines come from textbooks on GMMs such Grimm, Ram and Estabrook (2017) and the great article van de Schoot et al. (2017). 


1.	Descriptive statistics of observed variables. For dichotomous items, report the proportion of 1’s or proportion of high responses. 

2.	Measurement model, meaning how the four items measured over time relate to the construct of alcoholic tendencies, why a high value on this trait is bad because of a high value on each of these items. 

3.	Measurement invariance – this is where one of the first major limitations, statistical speaking, crops up. Measurement invariance cannot be completely investigated with dichotomous indicators. Below is a brief write-up I started on this topic a few months ago. This should get you started and includes some key references on this topic of measurement invariance with categorical variables. Also, the Grimm et al. (2017) book has some good sections on testing measurement invariance in Mplus (see pgs. 347-350, 381-389).  

4.	Describe the idea of linear growth on this latent trait. Where the growth model aims to describe the growth trajectory of the latent variable across the measurement occasions. We only investigated a linear growth curve. Now another limitation: the latent variable may have a non-linear growth trajectory. A nonlinear growth trajectory could be disguised as the presence of a latent class or this could hide the presence of latent classes do to an improperly specified growth pattern. 

5.	Methods of mixture modeling – idea that more than one latent class underlies these data. This is one of the main points that needs to be described as we are doing a growth mixture model (GMM). The GMM aims to described qualitatively different trajectories in growth on the latent trait over time. This is also where to describe how in our model, we are allowing for class specific intercepts and slopes in the growth model. Meaning that the classes on average have unique average growth trajectories and unique starting points on the latent trait. 

6.	Model selection – along with model summary across class enumerations. We will have estimated the class 1 through class 5 GMMs. We will need to report the log-likelihood, number of parameters, AIC, BIC, ssBIC, LMR-LRT. Along with information on which models had potential convergence issues. Although, hopefully there won’t be much convergence issues once we use more starts…. Anyways, that leads me into a important limitation: estimation of GMM, and mixture models in general, are notorious for being estimated at a local maximum on the likelihood surface and thus we may not have the true optimal solution for this model. We should note how the scale of the latent variable is also arbitrary and therefore the meanstructure was established based on the metric of the observed data and then rescaled to an arbitrary metric for presentation.  This will help us to describe which model is best fitting when looking at profile plots:

    a.	Profile plots will include two types. 1) class average trajectories and 2) class profiles for all individuals by panels of the “raw” factor scores across time. I wrote an R script for you that does this based on two pieces of information the file name and number of classes. This only works for converged models where factor scores were reported. 
    
7.	Model results to report of final model:

    a.	Class sizes
    
    b.	Entropy
    
    c.	Plot of the factor scores across time by each class
    
    d.	Class intercepts and slopes with associated standard errors (SE)
    
    e.	Effect of interventions across each class and associated SE

## References

1. Rens van de Schoot, Marit Sijbrandij, Sonja D. Winter, Sarah Depaoli \& Jeroen K. Vermunt (2017). The GRoLTS-Checklist: Guidelines for Reporting on Latent Trajectory Studies, Structural Equation Modeling: A Multidisciplinary Journal, 24:3, 451-467, DOI: 10.1080 /10705511.2016.1247646

2. Kevin J. Grimm, Nilam Ram \& Ryne Estabrook (2017). Growth modeling: Structural equation and multilevel modeling approaches. New York, NY. Guilford Press.

