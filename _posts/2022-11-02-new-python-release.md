---
layout: post
title:  "New release of stabilized-ica Python package (v2.0.0)"
author: Nicolas Captier
---

The new version 2.0.0 of the Python package <a href="https://stabilized-ica.readthedocs.io/en/latest/">stabilized-ica</a> has just been released. stabilized-ica is the computational core of BIODICA, but it can also be used as a standalone python tool for those who would like to integrate stabilized ICA into complex python pipelines.   

This new version is now fully compatible with <a href="https://scikit-learn.org/stable/">scikit-learn Python package</a> which is the standard library for machine learning in Python. It means that you can now use the base class of stabilized-ica as a sklearn transformer and include it into complex ML pipelines (see <a href="https://github.com/ncaptier/stabilized-ica/blob/master/examples/MNIST_classification.ipynb">this tutorial</a> for an illustration).   

stabilized-ica now comes with a complementary python toolbox called <a href="https://github.com/ncaptier/sica-omics">sica-omics</a> which contains several tools specific to the analysis of omics data (some of these tools are already available with BIODICA graphical user interface (Java implementation)). In particular, it proposes annotation functions to decipher the biological meaning of the extracted ica sources, as well as a wrapper to adapt stabilized-ica base code to the special case of Anndata format which is popular for dealing with single-cell gene expression data.   

Feel free to play with these two new pacakges ! If you have any questions or if you encounter problems do not hesitate to contact us or raise and issues on <a href="https://github.com/ncaptier/stabilized-ica">GitHub</a>. Any feedback would be greatly appreciated.

<div class="col-sm-6">
    <center><img  src="../../../../../assets/img/sica_logo.jpg" width="81%"></center>
</div>
<div class="col-sm-6">
    <center><img src="../../../../../assets/img/sicaomics_logo.png" width="74%"></center>
</div>
