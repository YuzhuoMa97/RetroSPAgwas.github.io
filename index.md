---
layout: default
title: Overview
nav_order: 1
description: "Overview of Restropective saddlepoint approximation (SPA) methods in GWAS."
has_children: false
has_toc: false
---

# Overview of restropective saddlepoint approximation (SPA) methods in GWAS

The restropective saddlepoint approximation (SPA) methods are mainly designed to conduct **genome-wide association studies (GWAS)** in terms of both single-variant and set-based analysis. 

## Genome-wide association studies

All retrospective-SPA-based GWAS approaches share the same analysis framework including the following two steps

- Step 1: Fit a null model using trait, covariates, and GRM (if applied).
- Step 2: Conduct single-variant or set-based tests to identify marker or marker-set (e.g. gene) significantly associated with the trait of interest.


##  Genome-wide gene-environment interaction (GxE) studies

All retrospective-SPA-based GxE approaches share the same analysis framework including the following two steps

- Step 1: Fit a genotype-independent (covariates-only) model using trait, covariates, and GRM (if applied).
- Step 2: Conduct single-variant or set-based tests to identify marker or marker-set (e.g. gene) significantly associated with the trait of interest.



# RetroSPAgwas Project Timeline

## Overview
This is the timeline of key milestones in the RetroSPAgwas project.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RetroSPAgwas Timeline</title>
    <style>
        .timeline {
            position: relative;
            max-width: 600px;
            margin: 0 auto;
        }
        .timeline::after {
            content: '';
            position: absolute;
            width: 6px;
            background-color: #ddd;
            top: 0;
            bottom: 0;
            left: 50%;
            margin-left: -3px;
        }
        .container {
            padding: 10px 40px;
            position: relative;
            background-color: inherit;
            width: 50%;
        }
        .container::after {
            content: '';
            position: absolute;
            width: 25px;
            height: 25px;
            right: -17px;
            background-color: white;
            border: 4px solid #FF9F55;
            top: 15px;
            border-radius: 50%;
            z-index: 1;
        }
        .left { left: 0; }
        .right { left: 50%; }
        .content {
            padding: 20px 30px;
            background-color: #fff;
            position: relative;
            border-radius: 6px;
        }
        .time { display: block; color: grey; }
    </style>
</head>
<body>
    <div class="timeline">
        <div class="container left">
            <div class="content">
                <p>March 2021</p>
                <span class="time">Came up with the idea of retrospective SPA</span>
            </div>
        </div>
        <div class="container right">
            <div class="content">
                <p>October 2021</p>
                <span class="time">Design of SPAmix algorithm completed</span>
            </div>
        </div>
        <div class="container left">
            <div class="content">
                <p>October 2021 - February 2022</p>
                <span class="time">Design of SPAGxE algorithm started</span>
            </div>
        </div>
        <div class="container right">
            <div class="content">
                <p>May 2022</p>
                <span class="time">Master's thesis completed</span>
            </div>
        </div>
    </div>
</body>
</html>

## Detailed Timeline

### March 2021
- **Event**: Came up with the idea of retrospective SPA.
- **Description**: This concept laid the foundation for future projects.

### October 2021
- **Event**: Design of SPAmix algorithm completed.
- **Description**: After months of effort, the SPAmix algorithm was finally completed, marking an important milestone in the research.

### October 2021 - February 2022
- **Event**: Design of SPAGxE algorithm started.
- **Description**: During this period, you and your team began exploring and designing the SPAGxE algorithm, a complex task that ultimately led to significant achievements.

### May 2022
- **Event**: Master's thesis completed.
- **Description**: After a long period of research and writing, your master's thesis was finally completed in May 2022, marking an important milestone in your academic journey.






```markdown
# Timeline of My Academic and Technical Adventures

## March 2021
- I had the inspiration to think about a retrospective Single Page Application (SPA).

## October 2021
- I successfully designed the SPAmix algorithm.

## October 2021 - February 2022
- I began working on the SPAGxE algorithm.

## May 2022
- I completed my Master's thesis.
```









<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Project Overview</title>
</head>
<body>

<h1>Project Overview</h1>

<!-- Embed the timeline -->
<iframe src="timeline.html" style="width:100%; height:500px; border:none;"></iframe>

</body>
</html>

