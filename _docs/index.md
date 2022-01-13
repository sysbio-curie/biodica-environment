---
title: Welcome
permalink: /docs/home/
redirect_from: /docs/index.html
---

### Running BIODICA Navigator
To launch BIODICA Navigator, go to your terminal and run the following command in your root folder for BIODICA:

```
java -jar BIODICA_GUI.jar
```

<center><img src="../../assets/img/welcome_1.png" width="75%"></center>

You can also open BIODICA Navigator by cliking on the corresponding *BIODICA_GUI.jar* file in your root folder of BIODICA.

### BIODICA modules
BIODICA pipeline is composed of 8 main computational modules. They are all accessible with BIODICA Navigator by cliking on the following icons:   


<div class="row">
  <div class="col-sm-4">
  <center><img src="../../assets/img/run_ica_icon.png" width="60%"></center>
  </div>
  <div class="col-sm-8">
  <p><b>Run stabilized ICA</b> - This module runs a stabilized version of Independent Component Analysis on a transcriptomic data set. The stability of the independent components is estimated through several runs of an ICA solver with random initializations. The results of the different runs are clustered and the centrotype compoents are considered to be the correct/stabilized ones.</p>
  </div>
</div> 
<br>
<div class="row">
  <div class="col-sm-4">
  <center><img src="../../assets/img/gsea_icon.png" width="45%"></center>
  </div>
  <div class="col-sm-8">
  <p><b>GSEA analysis</b> - This module applies Gene Set Enrichment Analysis to each stabilized ICA component. As input it uses the natural ranking given by the projection of each component in the "gene space" (i.e for each independent component, each gene is associated with a weight which reflects its importance in the definition of the component; this set of weights naturally ranks gene for the given component).</p>
  </div>
</div> 
<br>
<div class="row">
  <div class="col-sm-4">
  <center><img src="../../assets/img/toppgene_icon.png" width="40%"></center>
  </div>
  <div class="col-sm-8">
    <p><b>ToppGene analysis</b> - This module applies ToppGene functional enrichment analysis to each stabilized ICA component. As input it uses the "top contributing genes" of each component (i.e the genes associated with the highest weights in the gene space).</p>
  </div>
</div> 
<br>
<div class="row">
  <div class="col-sm-4">
  <center><img src="../../assets/img/often_icon.png" width="45%"></center>
  </div>
  <div class="col-sm-8">
  <p><b>OFTEN analysis</b> - This module finds optimally functionnaly enriched subnetworks associated with the gene rankings provided by each stabilized ICA component. It uses PPI networks from the <b>knowledge/undirected</b> folder, and the methodology descirbed in <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3449386/">Kairov et al. 2O13</a>.</p>
  </div>
</div> 
<br>
<div class="row">
  <div class="col-sm-4">
  <center><img src="../../assets/img/navicell_icon.png" width="50%"></center>
  </div>
  <div class="col-sm-8">
  <p><b>Navicell visualization</b> - This module mapps the input transcriptomic data and/or the stabilized ICA components onto biological network maps, browsable with NaviCell tool. See <a href="https://navicell.vincent-noel.fr/">this link</a> for more details.</p>
  </div>
</div> 
<br>
<div class="row">
  <div class="col-sm-4">
  <center><img src="../../assets/img/metagene_icon.png" width="50%"></center>
  </div>
  <div class="col-sm-8">
  <p><b>Metagene annotation</b> - This module provides additional tools to annotate and interpret the stabilized ICA components via their projection in the "gene space" (i.e metagenes). It can correlate metagenes to certain gene properties (numerical or categorical) as well as to reference metagenes.</p>
  </div>
</div>
<br>
<div class="row">
  <div class="col-sm-4">
  <center><img src="../../assets/img/metasample_icon.png" width="50%"></center>
  </div>
  <div class="col-sm-8">
  <p><b>Metasample annotation</b> - This module provides tools to annotate and interpret the stabilized ICA components via their projection in the "sample space" (i.e metasamples). It correlates the metasamples with additional sample annotations/features, using Spearman correlation for numerical features and Wilcoxon tests for categorical ones.</p>
  </div>
</div> 
<br>
<div class="row">
  <div class="col-sm-4">
  <center><img src="../../assets/img/rbh_icon.png" width="45%"></center>
  </div>
  <div class="col-sm-8">
  <p><b>Meta-analysis with RBH graph</b> - This module allows comparing all components extracted from different data sets Constructing a Reciprocally Best Hit (RBH) graph, representing reciprocal correlation relations between components extracted from different data sets.</p>
  </div>
</div> 

### BIODICA user guide

For more detailed descritpions about BIODICA main functions, please refer to the <a href="https://raw.githubusercontent.com/LabBandSB/BIODICA/master/doc/ICA_pipeline_general_description_v0.9.pdf">BIODICA user guide</a>. It is also accessible locally on your computer in the root folder of BIODICA **doc/ICA_pipeline_general_description_v0.9.pdf**.   

We also advise to refer to the <a href="https://stabilized-ica.readthedocs.io/en/latest/user_guide.html">user guide</a> of the stabilized-ica python package for those who want to understand better how the computational core of BIODICA for ICA works or for those who would like to use stabilized-ica as a standalone tool.



