---
layout: page
title: Metagene annotation using BIODICA
permalink: /docs/tutorials/tuto_metagene/
author: Altynbek Zhubanchaliyev, Nicolas Captier
---

<div class = "container">
    <h2>{{ page.title }}</h2>
    <p>{% if page.author %}{{ page.author }}{% endif %}</p>
</div>
<br>

The aim of this tutorial is to demonstrate how BIODICA can find associations between gene properties (numerical and categorical) and metagenes associated with identified stabilized Independent Components (IC's). We will use 30 IC's extracted from OVCA-transcriptomic dataset in <a href="{{ "/docs/tutorials/tuto_sica/" | relative_url }}">the ICA decomposition tutorial</a>.

**Warning :** When running this tutorial, please keep in mind that the ranking of the IC's will not necessarily be the same as indicated here, since BIODICA uses ICA decomposition algorithm with random initializations. For instance, IC5 we refer to in this tutorial may correspond to an IC with a ranking other than 5 in your case.   

------------

### Running metagene annotation analysis

1. Open Metagene Annotation

    <center><img src="https://codimd.math.cnrs.fr/uploads/upload_c1ecdaf6a6334bee166655397cd281a1.png" style="width:700px;height:auto;" ></center>
    <br>
2. Specify Data table (e.g. BIODICA/data/OVCA_TCGA/transcriptome/OVCA.txt). 

    <center><img src="https://codimd.math.cnrs.fr/uploads/upload_2c7e4dc0c3d53c59bc015cb46b2892e3.png" style="width:900px;height:auto;" ></center>
    <br>
3. First, run the MetaGene Annotation with the selected option '**Metagene associations**' (BIODICA/knowledge/geneproperties/genes.txt). The web-browser tab will open. You can close it.

4. Then run the MetaGene Annotation with an option '**Compare to previously defined metagenes**' (BIODICA/knowledge/metagenes).

    <center><img src="https://codimd.math.cnrs.fr/uploads/upload_dbe36e049873f3eed0ec4212712cc53a.png" style="width:900px;height:auto;" ></center>
    <br>
    **Note :** We can load any previously defined metagenes. The folder should contain one .rnk file for each metagene. Each file should contain two columns, the first one with the gene names and the second one with the associated gene weights. See the BIODICA/knowledge/metagenes folder for more details.

The MetaGene Annotation web-browser tab will look as follows :

<center><img src="https://codimd.math.cnrs.fr/uploads/upload_02dae706eeefa791200b98fc1937ebdb.png" style="width:700px;height:auto;" ></center>
<br>
The files are stored in the newly created directory (BIODICA/work/OVCA_MGENE).

---------------

### Annotation results

For the association of the metagenes with gene annotations, either categorical ones or numerical ones, BIODICA uses the same method as the one used for the metasample annotation. 

#### Association with categorical features

For a categorical gene annotation, its association with a metagene is computed by calculating the p-value of the Wilcoxon test between all pairs of categories and the metagene weights. The minimum p-value between all pair-wise comparisons is assigned to the association test.   

Inside the categorical gene annotation TYPE we have several categories describing the origin of the transcript (e.g. protein_coding, lncRNA, snoRNA...). The –log10(p-value) values of the associations between each metagene and the gene feature TYPE are reported in the association table.

<center><img src="https://codimd.math.cnrs.fr/uploads/upload_f9b230900bea772e8e7da49e6d65f079.png" style="width:1100px;height:auto;" ></center>
<br>
Clicking on the number of the IC13 shows the following charts:

<center><img src="https://codimd.math.cnrs.fr/uploads/upload_30cf1f56d1ada7e0936e8ea513baed5e.png" style="width:1100px;height:auto;" ></center>
<br>
We can see that 'protein_coding' and 'snoRNA' categories have the biggest difference between their means.

#### Association with numerical features

For a numerical gene annotation, its association with a metagene is computed by the Spearman correlation coefficient.   

In this tutorial, GC-content is the only numerical gene annotation we have. IC27 has the highest correlation to GC-content, and it equals 0.19.

<center><img src="https://codimd.math.cnrs.fr/uploads/upload_ebf1a4815ce63eb62c2c1561565d6758.png" style="width:1100px;height:auto;" ></center>
<br>
#### Associaion with known metagenes

The associations with previously known metagenes are computed with the Spearman correlation coefficient. 

<center><img src="https://codimd.math.cnrs.fr/uploads/upload_9281673584eeea3cfcf251edce8f819b.png" style="width:1100px;height:auto;" ></center>
<br>
IC5 recieved a strong (0.62) correlation with a previously identified M7_CELLCYCLE. GSEA and ToppGene analyses from previous tutorials suggested a strong association of this metagene with genes involved in the process of cell cycle, generating the consistency of findings about this independent component.

<center><img src="https://codimd.math.cnrs.fr/uploads/upload_c6d297327a4af56c361b2d93f0a61eee.png" style="width:500px;height:auto;" ></center>
