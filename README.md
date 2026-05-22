TFR prediction using RNAseq
================
Vincent Alcazer
22 mai, 2026

    ## [1] TRUE

**DEVELOPMENT AND EXTERNAL VALIDATION OF A TRANSCRIPTOME-BASED
MULTIVARIABLE PREDICTION MODEL FOR TREATMENT-FREE REMISSION IN CHRONIC
MYELOID LEUKEMIA**

*Vincent ALCAZER, Stéphanie DULUCQ, Isabelle MOSNIER, Kaddour CHABANE,
Pauline BERTIN-MOUROT, Sandrine DERRUAU, Marie BALSAT, Hélène
LABUSSIERE-WALLET, Pierre SUJOBERT, François-Xavier MAHON, Gabriel
ETIENNE, Franck NICOLINI, Sandrine HAYETTE*

[Alcazer V. et al. Journal of Clinical Oncology
2026](https://www.jco.org)

**Purpose:** Treatment-free remission (TFR) is a major therapeutic
objective in chronic myeloid leukaemia (CML). However, nearly 50% of
patients relapse after tyrosine kinase inhibitor (TKI) discontinuation,
and no robust predictive biomarker is currently available.

**Methods:** We profiled peripheral blood cell transcriptomes at
imatinib (IMA) discontinuation in patients from the multicenter STIM2
trial (n=96) to develop a transcriptome-based model predicting TFR by 2
years. A DESEQ2-based machine learning approach was compared to
classical machine learning algorithms. The signature was then externally
validated in an independent real-world cohort of patients attempting IMA
or nilotinib (NIL) cessation (n=70). The biological processes associated
with the signature were further explored.

**Results:** We identified a 50-gene signature discriminating patients
with sustained 2-year TFR from those experiencing molecular relapse
(AUROC 0.83 \[95% CI, 0.73–0.93\] and 0.75 \[95% CI, 0.55–1.00\] in the
training and internal validation cohorts, respectively). The
discriminative performance was confirmed in the external test cohort,
both as a binary predictor of 2-year TFR (AUROC 0.71 \[95% CI,
0.58–0.83\] overall; 0.77 \[95% CI, 0.61–0.92\] in IMA-treated patients)
and as a time-to-event predictor (log-rank p=0.0042). The high
TFR-signature group showed a higher proportion of myeloid immune cells
and natural killer T-cells, with an enrichment in Hedgehog signaling,
whereas the low TFR-signature group demonstrated a higher proportion of
lymphoid cells with an enrichment in mTOR signaling and a trend for
oxidative phosphorylation activation. T-cell receptor and immunoglobulin
heavy-chain repertoire analyses showed significantly greater
polyclonality in the high TFR-signature group.

**Conclusion:** These findings demonstrate that transcriptomic profiling
at TKI discontinuation can predict TFR outcomes in patients with CML and
provide biological insights into the mechanisms underlying sustained
TFR.

# Repository presentation

This repository provides the complete code required to reproduce the
figures related to signature computation and TFR prediction presented in
the paper. For legal and ethical reasons, raw data from the STIM2 cohort
cannot be provided, and only data from the external test cohort are
publicly available.

# Data

Data from the external test cohort are provided here:  
**- meta_external_test.tsv:** Meta data  
**- TFR_salmon_TPM_external_test.rds:** Salmon’s TPM normalized count
with Log2(x+1) transformation

Additional data (salmon’s raw output as txi file, DESEQ2 VST normalized
count, raw counts…) can be provided upon request.  
Raw fastQ data can be found on the European Nucleotide Archive (ENA)
under the accession number PRJEB111426.

Clinical and transcriptomic data from the STIM2 cohort originate from a
regulated clinical trial and are subject to ethical, legal, and
contractual restrictions related to patient consent and data protection;
therefore, individual-level clinical data from STIM2 cannot be made
publicly available. Access to these data may be considered upon
reasonable request and subject to approval by the relevant data
governance bodies, under a data transfer agreement.

## Table 1

Baseline characteristics according to TFR by 2 years in the external
test cohort

<div class="Rtable1"><table class="Rtable1-zebra">
<thead>
<tr>
<th class='rowlabel firstrow lastrow'></th>
<th class='firstrow lastrow'><span class='stratlabel'>No<br/><span class='stratn'>(N=29)</span></span></th>
<th class='firstrow lastrow'><span class='stratlabel'>Yes<br/><span class='stratn'>(N=41)</span></span></th>
<th class='firstrow lastrow'><span class='stratlabel'>Overall<br/><span class='stratn'>(N=70)</span></span></th>
<th class='firstrow lastrow'><span class='stratlabel'>P-value</span></th>
</tr>
</thead>
<tbody>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>Age_at_TKI_stop</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>Mean (SD)</td>
<td>62.6 (13.7)</td>
<td>61.3 (13.0)</td>
<td>61.9 (13.2)</td>
<td>0.921</td>
</tr>
<tr>
<td class='rowlabel lastrow'>Median [Q1, Q3]</td>
<td class='lastrow'>65.0 [52.0, 72.0]</td>
<td class='lastrow'>62.0 [56.0, 68.0]</td>
<td class='lastrow'>63.0 [54.0, 71.0]</td>
<td class='lastrow'></td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>Sex</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>F</td>
<td>9 (31.0%)</td>
<td>20 (48.8%)</td>
<td>29 (41.4%)</td>
<td>0.332</td>
</tr>
<tr>
<td class='rowlabel lastrow'>M</td>
<td class='lastrow'>20 (69.0%)</td>
<td class='lastrow'>21 (51.2%)</td>
<td class='lastrow'>41 (58.6%)</td>
<td class='lastrow'></td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>TKI</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>IMA</td>
<td>14 (48.3%)</td>
<td>22 (53.7%)</td>
<td>36 (51.4%)</td>
<td>0.906</td>
</tr>
<tr>
<td class='rowlabel lastrow'>NIL</td>
<td class='lastrow'>15 (51.7%)</td>
<td class='lastrow'>19 (46.3%)</td>
<td class='lastrow'>34 (48.6%)</td>
<td class='lastrow'></td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>TKI_line</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>1st</td>
<td>24 (82.8%)</td>
<td>34 (82.9%)</td>
<td>58 (82.9%)</td>
<td>1</td>
</tr>
<tr>
<td class='rowlabel lastrow'>2nd</td>
<td class='lastrow'>5 (17.2%)</td>
<td class='lastrow'>7 (17.1%)</td>
<td class='lastrow'>12 (17.1%)</td>
<td class='lastrow'></td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>Sokal</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>High</td>
<td>3 (10.3%)</td>
<td>2 (4.9%)</td>
<td>5 (7.1%)</td>
<td>0.712</td>
</tr>
<tr>
<td class='rowlabel'>Intermediate</td>
<td>6 (20.7%)</td>
<td>9 (22.0%)</td>
<td>15 (21.4%)</td>
<td></td>
</tr>
<tr>
<td class='rowlabel'>Low</td>
<td>5 (17.2%)</td>
<td>14 (34.1%)</td>
<td>19 (27.1%)</td>
<td></td>
</tr>
<tr>
<td class='rowlabel lastrow'>Missing</td>
<td class='lastrow'>15 (51.7%)</td>
<td class='lastrow'>16 (39.0%)</td>
<td class='lastrow'>31 (44.3%)</td>
<td class='lastrow'></td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>ELTS</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>Intermediate</td>
<td>6 (20.7%)</td>
<td>3 (7.3%)</td>
<td>9 (12.9%)</td>
<td>0.148</td>
</tr>
<tr>
<td class='rowlabel'>Low</td>
<td>5 (17.2%)</td>
<td>19 (46.3%)</td>
<td>24 (34.3%)</td>
<td></td>
</tr>
<tr>
<td class='rowlabel'>High</td>
<td>0 (0%)</td>
<td>1 (2.4%)</td>
<td>1 (1.4%)</td>
<td></td>
</tr>
<tr>
<td class='rowlabel lastrow'>Missing</td>
<td class='lastrow'>18 (62.1%)</td>
<td class='lastrow'>18 (43.9%)</td>
<td class='lastrow'>36 (51.4%)</td>
<td class='lastrow'></td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>ACA</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>No</td>
<td>26 (89.7%)</td>
<td>39 (95.1%)</td>
<td>65 (92.9%)</td>
<td>0.682</td>
</tr>
<tr>
<td class='rowlabel lastrow'>Yes</td>
<td class='lastrow'>3 (10.3%)</td>
<td class='lastrow'>2 (4.9%)</td>
<td class='lastrow'>5 (7.1%)</td>
<td class='lastrow'></td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>transcript_type_2</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>e13a2</td>
<td>10 (34.5%)</td>
<td>7 (17.1%)</td>
<td>17 (24.3%)</td>
<td>0.247</td>
</tr>
<tr>
<td class='rowlabel lastrow'>e14a2</td>
<td class='lastrow'>19 (65.5%)</td>
<td class='lastrow'>34 (82.9%)</td>
<td class='lastrow'>53 (75.7%)</td>
<td class='lastrow'></td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>TKI_overall_months</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>Mean (SD)</td>
<td>96.7 (51.3)</td>
<td>101 (53.2)</td>
<td>99.0 (52.1)</td>
<td>0.951</td>
</tr>
<tr>
<td class='rowlabel lastrow'>Median [Q1, Q3]</td>
<td class='lastrow'>84.0 [59.0, 130]</td>
<td class='lastrow'>77.0 [60.0, 131]</td>
<td class='lastrow'>78.5 [59.3, 131]</td>
<td class='lastrow'></td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>MR4.5_duration</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>Mean (SD)</td>
<td>66.1 (52.1)</td>
<td>61.3 (46.6)</td>
<td>63.3 (48.6)</td>
<td>0.928</td>
</tr>
<tr>
<td class='rowlabel'>Median [Q1, Q3]</td>
<td>53.0 [28.0, 85.0]</td>
<td>47.0 [31.3, 84.5]</td>
<td>48.0 [30.0, 89.0]</td>
<td></td>
</tr>
<tr>
<td class='rowlabel lastrow'>Missing</td>
<td class='lastrow'>2 (6.9%)</td>
<td class='lastrow'>3 (7.3%)</td>
<td class='lastrow'>5 (7.1%)</td>
<td class='lastrow'></td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>cohort</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel lastrow'>Test</td>
<td class='lastrow'>29 (100%)</td>
<td class='lastrow'>41 (100%)</td>
<td class='lastrow'>70 (100%)</td>
<td class='lastrow'>&lt;0.001</td>
</tr>
<tr>
<td class='rowlabel firstrow'><span class='varlabel'>follow_up</span></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
<td class='firstrow'></td>
</tr>
<tr>
<td class='rowlabel'>Mean (SD)</td>
<td>NA (NA)</td>
<td>59.0 (20.3)</td>
<td>59.0 (20.3)</td>
<td>1</td>
</tr>
<tr>
<td class='rowlabel'>Median [Q1, Q3]</td>
<td>NA [NA, NA]</td>
<td>64.9 [48.0, 73.5]</td>
<td>64.9 [48.0, 73.5]</td>
<td></td>
</tr>
<tr>
<td class='rowlabel lastrow'>Missing</td>
<td class='lastrow'>29 (100%)</td>
<td class='lastrow'>0 (0%)</td>
<td class='lastrow'>29 (41.4%)</td>
<td class='lastrow'></td>
</tr>
</tbody>
</table>
</div>

## Factor associated with TFR

Univariate cox models of baseline factors associated with TFR in the
external test cohort

<img src="README_files/figure-gfm/TFR pred factors-1.png" alt="" width="3000" style="display: block; margin: auto;" />

# DESEQ2

The raw results of the DESEQ2 bootstraps are provided in the repository
(data/DESEQ2_bootstrap_salmon_pc_0.75_reslist.rds).

## Overall results

<img src="README_files/figure-gfm/Overall res-1.png" alt="" width="3600" style="display: block; margin: auto;" /><img src="README_files/figure-gfm/Overall res-2.png" alt="" width="3600" style="display: block; margin: auto;" /><img src="README_files/figure-gfm/Overall res-3.png" alt="" width="3600" style="display: block; margin: auto;" />

## Final model

**Filters:**  
n=500 bootstraps  
FDR \< 0.1  
FC_cutoff: 0  
Min presentation: 50% of overall models

<img src="README_files/figure-gfm/Best model-1.png" alt="" width="3000" style="display: block; margin: auto;" />

# TFR prediction

## ROC curves

<img src="README_files/figure-gfm/ROC Curves-1.png" alt="" width="3000" style="display: block; margin: auto;" />

## Kaplan Meier

<img src="README_files/figure-gfm/KM curves-1.png" alt="" width="3000" style="display: block; margin: auto;" />

## Cox model

Multivariate cox model computed on the external test set

<img src="README_files/figure-gfm/Cox model-1.png" alt="" width="3000" style="display: block; margin: auto;" />

# Conclusion

<!-- Finir par le code suivant pour lister les versions des libraries -->

    ## R version 4.6.0 (2026-04-24 ucrt)
    ## Platform: x86_64-w64-mingw32/x64
    ## Running under: Windows 11 x64 (build 26200)
    ## 
    ## Matrix products: default
    ##   LAPACK version 3.12.1
    ## 
    ## locale:
    ## [1] LC_COLLATE=French_France.utf8  LC_CTYPE=French_France.utf8    LC_MONETARY=French_France.utf8 LC_NUMERIC=C                   LC_TIME=French_France.utf8    
    ## 
    ## time zone: Europe/Paris
    ## tzcode source: internal
    ## 
    ## attached base packages:
    ## [1] parallel  stats4    stats     graphics  grDevices utils     datasets  methods   base     
    ## 
    ## other attached packages:
    ##  [1] survminer_0.5.2             ggpubr_0.6.3                survival_3.8-6              pROC_1.19.0.1               MASS_7.3-65                
    ##  [6] MetBrewer_0.2.0             plotROC_2.3.3               doParallel_1.0.17           iterators_1.0.14            foreach_1.5.2              
    ## [11] BiocParallel_1.46.0         DESeq2_1.52.0               SummarizedExperiment_1.42.0 Biobase_2.72.0              MatrixGenerics_1.24.0      
    ## [16] matrixStats_1.5.0           GenomicRanges_1.64.0        Seqinfo_1.2.0               IRanges_2.46.0              S4Vectors_0.50.1           
    ## [21] BiocGenerics_0.58.1         generics_0.1.4              gtools_3.9.5                ggrepel_0.9.8               lubridate_1.9.5            
    ## [26] forcats_1.0.1               stringr_1.6.0               dplyr_1.2.1                 purrr_1.2.2                 readr_2.2.0                
    ## [31] tidyr_1.3.2                 tibble_3.3.1                ggplot2_4.0.3               tidyverse_2.0.0            
    ## 
    ## loaded via a namespace (and not attached):
    ##  [1] gridExtra_2.3       rlang_1.2.0         magrittr_2.0.5      otel_0.2.0          compiler_4.6.0      vctrs_0.7.3         crayon_1.5.3       
    ##  [8] pkgconfig_2.0.3     fastmap_1.2.0       backports_1.5.1     XVector_0.52.0      labeling_0.4.3      rmarkdown_2.31      markdown_2.0       
    ## [15] tzdb_0.5.0          bit_4.6.0           xfun_0.57           cachem_1.1.0        litedown_0.9        jsonlite_2.0.0      DelayedArray_0.38.1
    ## [22] broom_1.0.13        R6_2.6.1            bslib_0.11.0        stringi_1.8.7       RColorBrewer_1.1-3  car_3.1-5           jquerylib_0.1.4    
    ## [29] Rcpp_1.1.1-1.1      knitr_1.51          Matrix_1.7-5        splines_4.6.0       timechange_0.4.0    tidyselect_1.2.1    rstudioapi_0.18.0  
    ## [36] abind_1.4-8         yaml_2.3.12         ggtext_0.1.2        codetools_0.2-20    lattice_0.22-9      withr_3.0.2         S7_0.2.2           
    ## [43] evaluate_1.0.5      xml2_1.5.2          pillar_1.11.1       BiocManager_1.30.27 carData_3.0-6       DT_0.34.0           vroom_1.7.1        
    ## [50] hms_1.1.4           commonmark_2.0.0    scales_1.4.0        glue_1.8.1          tools_4.6.0         locfit_1.5-9.12     ggsignif_0.6.4     
    ## [57] table1_1.5.1        forestmodel_0.6.2   grid_4.6.0          crosstalk_1.2.2     Formula_1.2-5       cli_3.6.6           S4Arrays_1.12.0    
    ## [64] gtable_0.3.6        rstatix_0.7.3       sass_0.4.10         digest_0.6.39       SparseArray_1.12.2  htmlwidgets_1.6.4   farver_2.1.2       
    ## [71] htmltools_0.5.9     lifecycle_1.0.5     gridtext_0.1.6      bit64_4.8.2
