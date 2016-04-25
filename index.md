---
title       : A phylodynamics pipeline for pathogen sequence data 
subtitle    : HIV Dynamics & Evolution, 2016
author      : Mukarram Hossain
job         : University of Cambridge
framework   : revealjs        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : zenburn      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
revealjs:
  theme: serif
  transition: cube
  center: "false"
knit        : slidify::knit2slides
---

## Phylodynamics pipeline for pathogen sequence data
<br></br>
**Mukarram Hossain**  

Department of Veterinary Medicine  
University of Cambridge
  
<br></br>

<!--- <img src="assets/img/uc-colour-logo.jpg" width="30%" style="border: 0px">&nbsp; --->

---

### Phylodynamics
<br>
*"Viral phylodynamics is defined as the study of how epidemiological, immunological, and evolutionary processes act and potentially interact to shape viral phylogenies."*

<br>
[Volz, Koelle and Bedford (2013)](http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002947)

---

### Phylodynamic analysis
<br>
* Serially sampled virus sequences and phylogenies reveal phylodynamic properties
* Frequently use sophisticated software packages:
  + BEAST
  + MrBayes
* [BEAST](http://bmcevolbiol.biomedcentral.com/articles/10.1186/1471-2148-7-214) is cited ~7300 times
<br><br>
People use BEAST/MrBayes as a black box

--- 

<br><br><br><br><br><br>
<div style="font-size:60px">Phylodynamic analysis - issues</div>

--- &vertical

### Datasets with heterogeneity

<img src="assets/img/h1n1.rtt.png" width="60%" style="margin: 10px 10px">&nbsp;

***

### Heterogeneity in phylogeny

<img src="assets/img/h1n1.loc.png" width="100%" style="margin: 10px 10px">&nbsp;

---

### Resource requirements

<img src="assets/img/cwseqs.tree.png" width="60%" style="margin: 10px 10px">&nbsp;

<img src="assets/img/timing.png" width="100%" style="margin: 10px 10px">&nbsp;

---

### Incorrect model selection
<br>
* Poor model fit in phylodynamic studies may lead to incorrect estimation
  + [Reid et al. (2014)](http://sysbio.oxfordjournals.org/content/63/3/322.long)
  + [Holmes (2016)](http://jvi.asm.org/content/90/4/2155.full)
  + [Rambaut et al. (2016)](http://ve.oxfordjournals.org/content/2/1/vew007)

<br>**Prior analysis is recommended before running BEAST**

---

### BEAST 
<br>
* Rely on Markov Chain Monte Carlo (MCMC) to obtain posterior estimates 
* MCMC is slow to reach stationary distribution for large datasets
* BEAST is an ideal tool for confirmatory analysis
* Not ideal for:
  + model comparison
  + hypothesis testing using goodness of fit  

---

<br><br><br><br><br><br>
<div style="font-size:60px">Phylodynamic pipeline</div>

---

### Phylopipe
<br>
* For high throughput analysis of heterochronous pathogen sequence data
* Can be used for three purposes:
  + quality control step
  + exploratory tool to obtain rough estimates
  + to use these estimates as initial conditions in BEAST

---

### PhyloPipe - Tools
<Br>
The following tools are included in the pipeline:
* Alignment - [Pipelign](https://github.com/asmmhossain/pipelign), [Muscle](http://www.drive5.com/muscle/), [Mafft](http://mafft.cbrc.jp/alignment/software/)
* Phylogeny reconstruction - [ExaML](http://sco.h-its.org/exelixis/web/software/examl/index.html), [IQ-TREE](http://www.cibiv.at/software/iqtree/)
* Evolutionary rate estimation - [RTT](https://cran.r-project.org/web/packages/ape/index.html), [TREBLE](http://bioinformatics.oxfordjournals.org/content/23/2/169.full), [LSD](http://www.atgc-montpellier.fr/LSD/)
* Time-stamped phylogeny - [RTT](https://cran.r-project.org/web/packages/ape/index.html), [CHRONOS](https://cran.r-project.org/web/packages/ape/index.html), [LSD](http://www.atgc-montpellier.fr/LSD/)
* Demographic model selection - [GENIE](http://www.cecalc.ula.ve/BIOINFO/servicios/herr1/GENIE/manual.html)
* Population dynamics - [Phylodyn](https://github.com/mdkarcher/phylodyn)
* Detecting asymmetry - [treeImbalance](https://github.com/bdearlove/treeImbalance)

---

### PhyloPipe - workflow

<img src="assets/img/phylopipe.png" width="65%" class="centred" style="margin: 10px 10px"/>

---

<br><br><br><br><br><br>
<div style="font-size:60px">Case studies</div>

---

### Dengue virus type 1 (Vietnam)
<br>
<div width="350" style="float: left;">
<img src="assets/img/denv1.treefile.png" width="400px" height="400px" class="centred" style="margin: 10px 10px" />
</div>
<div width="450" style="float: right;">
<img src="assets/img/denv.png" width="400px" class="centred" style="margin: 10px 10px" />
</div>

---&vertical

### H3N2 influenza (HA) - Europe
<br>
<div width="350" style="float: left;">
<img src="assets/img/europe.treefile.png" width="400px" height="360px" class="centred" style="margin: 10px 10px" />
</div>
<div width="450" style="float: right;">
<img src="assets/img/europe.rtt.png" width="400px" height="360px" class="centred" style="margin: 10px 10px" />
</div>

***

### Europe - rates and tMRCA
<br>
<img src="assets/img/europe.rates.png" width="100%" class="centred" style="margin: 10px 10px" />

***

### Europe - molecular clock <br>
<br>
<img src="assets/img/europe.chronos.png" width="80%" class="centred" style="margin: 10px 10px" />

***

### Europe - demographic model
<br>
<img src="assets/img/europe.genie.png" width="100%" class="centred" style="margin: 10px 10px" />

***

### Europe - skyride
<br>
<img src="assets/img/europe.skyride.png" width="70%" class="centred" style="margin: 10px 10px" />

***

### Europe - asymmetry analysis
<br>
<img src="assets/img/europe.treeimbalance.png" width="70%" class="centred" style="margin: 10px 10px" />

***

### Europe - asymmetry analysis
<br>
<div width="350" style="float: left;">
<img src="assets/img/europe.cherries.hist.png" width="400px" height="360px" class="centred" style="margin: 10px 10px" />
<div style="font-size:20px">Distribution of number of cherries</div>
</div>
<div width="450" style="float: right;">
<img src="assets/img/europe.sackins.hist.png" width="400px" height="360px" class="centred" style="margin: 10px 10px" />
<div style="font-size:20px">Disribution of Sackin's index</div>
</div>

***

### Europe - initial conditions
<br>
<img src="assets/img/europe.rate.ess.png" width="60%" class="centred" style="margin: 10px 10px" />

---

### PhyloPipe - summary
<br>
* Quick and approximate phylodynamic estimation
* Compatible (??) estimation of parameters 
* Ease of use

---

### Future works
<br>
* Include more analysis tools 
* Set up web service with analysis summary
* Develop open platform distributed application

---

### Acknowledgements
<br>
* Simon Frost
* Bethany Dearlove
* Fei Xiang

---


<br>
<img src="assets/img/logos.png" width="100%" class="centred" style="margin: 10px 10px"/>

---

<br></br>
<img src="assets/img/questions.jpg" width="605px" class="centred" style="margin: 10px 10px"/>

