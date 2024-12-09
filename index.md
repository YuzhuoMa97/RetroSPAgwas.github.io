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





# 我的时间轴示例

<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>时间轴示例</title>
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
                <p>2021年3月</p>
                <span class="time">retrospective SPA概念诞生</span>
            </div>
        </div>
        <div class="container right">
            <div class="content">
                <p>2021年10月</p>
                <span class="time">SPAmix算法设计完成</span>
            </div>
        </div>
        <div class="container left">
            <div class="content">
                <p>2021年10月 - 2022年2月</p>
                <span class="time">SPAGxE算法设计</span>
            </div>
        </div>
        <div class="container right">
            <div class="content">
                <p>2022年5月</p>
                <span class="time">硕士学位论文完成</span>
            </div>
        </div>
    </div>
</body>
</html>
