---
layout: page
title: ICA decomposition using BIODICA Navigator
permalink: /docs/tutorials/tuto_often/
author: Altynbek Zhubanchaliyev, Nicolas Captier
---

<div class = "container">
    <h2>{{ page.title }}</h2>
    <p>{% if page.author %}{{ page.author }}{% endif %}</p>
</div>
<br>

After ICA decomposition, each metagene could be associated to a subnetwork in a global network of pairwise interactions such as protein-protein interactions (PPI).
This tutorial aims to demonstrate how BIODICA can perform OFTEN analysis [(Kairov et al. 2012)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3449386/) - "a method for selecting a number of genes in a ranked gene list such that this set forms the Optimally Functionally Enriched Network (OFTEN), formed by known physical interactions between genes or their products".

**Warning :** When running this tutorial, please keep in mind that the ranking of the IC's will not necessarily be the same as indicated here, since BIODICA uses ICA decomposition algorithm with random initializations. For instance, IC5 we refer to in this tutorial may correspond to an IC with a ranking other than 5 in your case.

----------------

### Launching OFTEN analysis

OFTEN analysis applied to an IC metagene consists in several steps: 1) For the k top weighted/top ranked genes in the metagene, it maps them on the interaction graph and measure the size C(k') of the largest component of the subnetwork formed by the k' genes among the k top genes found in the interaction graph; 2) k' genes are then randomly sampled and the size of the largest component of the subnetwork they form is measured R(k') - this step is repeated **NumberOfPerms** times; 3) Finally a percolation score is computed S(k) = (1/k')*(C(k') - Mean(R(k'))) to assess whether the largest component of the subnetwork formed by the top ranked genes of the metagene is highly non-random or not.

These 3 steps are repeated for a number of top ranked genes k going from **Min** to **Max** with a step of size **Step**. At the end, the largest number k_opt after which the percolation score goes down is selected and the largest component of the connected subnetwork is associated to the IC metagene.   

1. Open OFTEN analysis tool in BIODICA

    <center><img src="https://codimd.math.cnrs.fr/uploads/upload_7f79714c41dc3fda7eabc8302fc76f84.png" style="width:700px;height:auto;" ></center>
    <br>

2. In the OFTEN window:

    * Select a metagene table from previous ICA decomposition by pressing ‘**Browse**’ in front of **Specify metagene table S**. Here we will use decomposition of OVCA dataset from previous tutorials, located in BIODICA/work/OVCA_ICA/OVCA_ica_S.xls.

    * **Specify PPI network** with the following path BIODICA/knowledge/networks/undirected/hprd9_pc_clicks.xgmml

    <center><img src="https://codimd.math.cnrs.fr/uploads/upload_5031fc9033afbd19b3aa92f6009fdd90.png" style="width:900px;height:auto;" ></center>
    <br>

    **Parameters of OFTEN** are:
    * **Min** - minimal number of top genes in the ranking selected for testing (50 is the default value)
    * **Step** - step with which the scanning is performed (100 is the default value)
    * **Max** - maximal number of top genes in the ranking selected for testing (600 is the default value)
    * **NumberOfPerms** - number of random network samples constructed in order to estimate a statistical significance of the OFTEN score (100 is the default value)


3. Press '**Run**' and '**OK**' when the process is successfully done. The following window will open up in your browser.

    <center><img src="https://codimd.math.cnrs.fr/uploads/upload_c1897bddcd03e682031b95fc508d3aea.png" style="width:700px;height:auto;" ></center>
    <br>

The analysis is done for 3 possible rankings defined by the component: from the positive side (PLUS), from the negative side (MINUS) and from the absolute values of gene contributions (ABS).

For each side, we have the following categories:
* **_GENES** - number of genes found in the interaction graph
* **_N** - optimal number of genes forming the network
* **_SC** - percolation score
* **_PVAL** - p-value of the association of genes to a subnetwork of PPI

If we scroll down, there will be a list of available files to download.

<center><img src="https://codimd.math.cnrs.fr/uploads/upload_d2f1a783135f62ba11c2eba6fe72522b.png" style="width:700px;height:auto;" ></center>
<br>

All the files from OFTEN analysis can be found in the newly created BIODICA/work/OVCA_OFTEN folder.

----------------------

### Interpreting the results

#### The network

By clicking on the number in the column _N, we can look at the constructed optimally functionally enriched network associated to an IC component. 

For this tutorial we will focus on the network constructed for IC5 of OVCA_dataset. There are 69 genes at the PLUS_N and p-value = 0. The network looks like this: 

<center><img src="https://codimd.math.cnrs.fr/uploads/upload_c4a6f56d35c7b096ba96e50b78798e04.png" style="width:900px;height:auto;" ></center>
<br>

The brighter a node is, the larger its weight in the metagene (i.e its contribution to the metagene) is.

The graph looks slightly crowded, with CDK1 in the center. Additionally we can see genes as MYBL2, E2F1, CCNB1, AURKA and others, which are involved in the cell cycle, either directly controlling it or playing a crucial role in associated processes. In previous tutorials, using metagene annotation tools, we have identified, that genes from our IC5 component are associated with the process of cell cycle. Using OFTEN we can observe meaningful interactions among these genes. This network is interactive and the user can pull the nodes and zoom-in to take a closer look.

### The score

By clicking on the number in the column PLUS_SC for the IC5 we will find the following figure, representing the percolation score for the number of genes inside IC5.

<center><img src="https://codimd.math.cnrs.fr/uploads/upload_71fdf03f4fb7f6e1a95a426ef1e7e2c3.png" style="width:1000px;height:auto;" ></center>
<br>

**Note :** The networks are stored as .xgmml files and can be opened with appropriate softwares (e.g. Cytoscape). 
