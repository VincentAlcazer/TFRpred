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

<div class="datatables html-widget html-fill-item" id="htmlwidget-a84b6e7cc54e6c96a827" style="width:100%;height:auto;"></div>
<script type="application/json" data-for="htmlwidget-a84b6e7cc54e6c96a827">{"x":{"filter":"none","vertical":false,"extensions":["Buttons"],"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40","41","42","43","44","45","46","47","48","49","50"],["ENSG00000144115.18","ENSG00000126251.7","ENSG00000213901.11","ENSG00000162779.22","ENSG00000143512.13","ENSG00000171574.19","ENSG00000170949.18","ENSG00000182326.17","ENSG00000273820.2","ENSG00000219626.9","ENSG00000203814.7","ENSG00000223638.4","ENSG00000177181.15","ENSG00000138792.10","ENSG00000112984.12","ENSG00000196361.10","ENSG00000288859.2","ENSG00000164402.14","ENSG00000198176.13","ENSG00000139187.10","ENSG00000178665.16","ENSG00000258484.4","ENSG00000177380.14","ENSG00000118514.14","ENSG00000137802.15","ENSG00000184260.6","ENSG00000089558.9","ENSG00000176681.15","ENSG00000249437.8","ENSG00000215193.14","ENSG00000288825.1","ENSG00000049541.11","ENSG00000167695.15","ENSG00000172031.7","ENSG00000183019.9","ENSG00000130856.18","ENSG00000162438.12","ENSG00000125818.18","ENSG00000150760.13","ENSG00000186625.14","ENSG00000133026.14","ENSG00000110400.11","ENSG00000139168.9","ENSG00000005381.9","ENSG00000105219.10","ENSG00000293691.1","ENSG00000164037.17","ENSG00000198089.16","ENSG00000100150.20","ENSG00000117682.18"],[445,393,388,382,362,327,326,326,323,317,313,308,307,303,302,302,302,294,292,288,287,286,285,284,284,284,283,282,279,277,277,272,272,271,268,265,265,264,264,263,258,255,254,252,252,251,250,250,249,249],[-1.248727174336199,-1.198502153188701,-0.6116128295415628,-1.133230331488036,-1.18554487111357,0.4286835438892003,-0.2379316015459229,-0.5321349063870429,0.2543885290322624,-0.182134622840664,0.7322075822705321,1.027203242659737,-0.8569487696280242,1.139525032591282,0.9944549663069707,-0.968111095617297,0.5585064197007954,-0.2825360732066283,0.2456645601582327,-0.4282002177834952,0.4287358811676027,0.8150517703157691,-0.4077782995868289,-0.4893381979053566,-0.1909984272094225,0.5801521300863867,-1.611029866926444,-0.6000906761610365,0.7372279683684101,-0.1760371480470972,0.5077578368542426,0.2458983808017215,-0.575905377365834,-0.6503270104470483,0.5108162019823804,-0.3681783619052055,-0.5200757959375395,0.1831937161831335,-0.6165730253162823,-0.172265476506181,-0.7078893860810115,0.2840548623333103,-0.2023850637486373,0.6167861407067742,-0.5548415929867815,0.7799757815704945,-0.4902546964190729,-0.2174257405249971,-0.2084332211232704,-0.1754521635007096],["0.0118","0.0230","0.0178","0.0229","0.0184","0.0248","0.0294","0.0229","0.0317","0.0341","0.0214","0.0281","0.0287","0.0264","0.0242","0.0300","0.0258","0.0312","0.0286","0.0316","0.0293","0.0305","0.0275","0.0291","0.0301","0.0253","0.0152","0.0287","0.0314","0.0300","0.0263","0.0297","0.0269","0.0329","0.0297","0.0289","0.0343","0.0304","0.0315","0.0283","0.0279","0.0328","0.0270","0.0278","0.0328","0.0298","0.0315","0.0320","0.0331","0.0384"],[-2.47,-3.53,-1.23,-3.66,-2.97,0.93,-0.53,-1.1,0.58,-0.35,1.56,4.93,-2.4,3.66,2.75,-2.67,1.2,-0.58,0.53,-1,0.97,2.39,-0.91,-1.25,-0.35,1.3,-4.34,-1.3,1.96,-0.34,1.24,0.54,-1.35,-1.58,1.32,-0.9,-1.35,0.34,-1.52,-0.3,-1.93,0.64,-0.37,1.61,-1.23,2.01,-1.22,-0.41,-0.38,-0.36],["&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001","&lt;0.0001"],["chr2","chr19","chr2","chr1","chr1","chr19","chr19","chr12","chrX","chr2","chr1","chr19","chr1","chr4","chr5","chr19","chr1","chr5","chr13","chr12","chr7","chr15","chr19","chr6","chr15","chr1","chr17","chr17","chr5","chr22","chr1","chr7","chr17","chr1","chr19","chr18","chr1","chr20","chr10","chr6","chr17","chr11","chr12","chr17","chr19","chr5","chr4","chr22","chr22","chr1"],[88170295,35371068,219161465,179365720,222522258,58401504,53066606,6988259,49879484,24076526,149782689,55759097,42380792,110365733,138178719,11451326,149851061,132750819,113584721,8950044,55887456,68818221,49119544,134917393,41774434,149886918,42156891,46292733,70968166,18077923,149842218,74231499,732412,92029985,7677088,76822557,15438442,1113240,126905409,149594873,8474207,119623408,42312086,58269855,40222208,70487719,102885048,31488688,31753867,26432282],[88186636,35372962,219170095,179554735,222548104,58431736,53103434,7071032,49882558,24169640,149812373,55763421,42424232,110565285,138187723,11481046,149851652,132807241,113641473,9010760,55942530,68946811,49151026,134950115,41827855,149887411,42181142,46338077,71025339,18105396,149842750,74254458,742968,92063538,7679833,76972901,15449242,1189415,127452517,149648972,8631376,119729200,42326257,58280935,40226697,70491228,103019719,31618588,31908033,26471306],["+","+","-","+","-","+","-","+","+","+","-","+","+","+","+","-","+","-","+","+","+","+","+","-","+","+","-","+","-","+","-","-","+","+","+","+","+","+","+","-","-","-","-","-","-","+","-","+","+","+"],["ENSG00000144115.18","ENSG00000126251.7","ENSG00000213901.11","ENSG00000162779.22","ENSG00000143512.13","ENSG00000171574.19","ENSG00000170949.18","ENSG00000182326.17","ENSG00000273820.2","ENSG00000219626.9","ENSG00000203814.7","ENSG00000223638.4","ENSG00000177181.15","ENSG00000138792.10","ENSG00000112984.12","ENSG00000196361.10","ENSG00000288859.2","ENSG00000164402.14","ENSG00000198176.13","ENSG00000139187.10","ENSG00000178665.16","ENSG00000258484.4","ENSG00000177380.14","ENSG00000118514.14","ENSG00000137802.15","ENSG00000184260.6","ENSG00000089558.9","ENSG00000176681.15","ENSG00000249437.8","ENSG00000215193.14","ENSG00000288825.1","ENSG00000049541.11","ENSG00000167695.15","ENSG00000172031.7","ENSG00000183019.9","ENSG00000130856.18","ENSG00000162438.12","ENSG00000125818.18","ENSG00000150760.13","ENSG00000186625.14","ENSG00000133026.14","ENSG00000110400.11","ENSG00000139168.9","ENSG00000005381.9","ENSG00000105219.10","ENSG00000293691.1","ENSG00000164037.17","ENSG00000198089.16","ENSG00000100150.20","ENSG00000117682.18"],["THNSL2","GPR42","SLC23A3","AXDND1","HHIPL2","ZNF584","ZNF160","C1S","USP27X","FAM228B","H2BC18","RFPL4A","RIMKLA","ENPEP","KIF20A","ELAVL3","H2AC19","SEPTIN8","TFDP1","KLRG1","ZNF713","SPESP1","PPFIA3","ALDH8A1","MAPKBP1","H2AC20","KCNH4","LRRC37A","NAIP","PEX26","H2AC18","RFC2","TLCD3A","EPHX4","MCEMP1","ZNF236","CTRC","PSMF1","DOCK1","KATNA1","MYH10","NECTIN1","ZCRB1","MPO","CCNP","ENSG00000293691","SLC9B1","SFI1","DEPDC5","DHDDS"],["HGNC:25602","HGNC:4500","HGNC:20601","HGNC:26564","HGNC:25842","HGNC:27318","HGNC:12948","HGNC:1247","HGNC:13486","HGNC:24736","HGNC:24700","HGNC:16449","HGNC:28725","HGNC:3355","HGNC:9787","HGNC:3314","HGNC:29668","HGNC:16511","HGNC:11749","HGNC:6380","HGNC:22043","HGNC:15570","HGNC:9247","HGNC:15471","HGNC:29536","HGNC:4738","HGNC:6253","HGNC:29069","HGNC:7634","HGNC:22965","HGNC:4736","HGNC:9970","HGNC:29646","HGNC:23758","HGNC:27291","HGNC:13028","HGNC:2523","HGNC:9571","HGNC:2987","HGNC:6216","HGNC:7568","HGNC:9706","HGNC:29620","HGNC:7218","HGNC:25805",null,"HGNC:24244","HGNC:29064","HGNC:18423","HGNC:20603"],["OTTHUMG00000130314.6","OTTHUMG00000157124.3","OTTHUMG00000154616.9","OTTHUMG00000035266.8","OTTHUMG00000037545.4","OTTHUMG00000183533.3","OTTHUMG00000182854.3","OTTHUMG00000150305.5","OTTHUMG00000189037.3","OTTHUMG00000151901.4","OTTHUMG00000183159.2","OTTHUMG00000165449.2","OTTHUMG00000007335.5","OTTHUMG00000132546.4","OTTHUMG00000129195.4","OTTHUMG00000182030.4","OTTHUMG00000012097.1","OTTHUMG00000059735.15","OTTHUMG00000017388.7","OTTHUMG00000168277.3","OTTHUMG00000156175.4","OTTHUMG00000133321.4","OTTHUMG00000183213.3","OTTHUMG00000015623.5","OTTHUMG00000160227.3","OTTHUMG00000035825.2","OTTHUMG00000180106.4","OTTHUMG00000149841.4","OTTHUMG00000163318.7","OTTHUMG00000149970.5","OTTHUMG00000188678.1","OTTHUMG00000023239.8","OTTHUMG00000177491.6","OTTHUMG00000010114.2","OTTHUMG00000182440.2","OTTHUMG00000179331.3","OTTHUMG00000002255.2","OTTHUMG00000031656.13","OTTHUMG00000019249.4","OTTHUMG00000015787.5","OTTHUMG00000108195.4","OTTHUMG00000166177.4","OTTHUMG00000169382.2","OTTHUMG00000178922.3","OTTHUMG00000160481.5",null,"OTTHUMG00000161114.4","OTTHUMG00000030249.15","OTTHUMG00000030926.30","OTTHUMG00000003554.8"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>gene_id<\/th>\n      <th>n<\/th>\n      <th>mean_log2FC<\/th>\n      <th>mean_padj<\/th>\n      <th>best_log2FC<\/th>\n      <th>best_padj<\/th>\n      <th>seqname<\/th>\n      <th>start<\/th>\n      <th>end<\/th>\n      <th>strand<\/th>\n      <th>ENSID<\/th>\n      <th>gene_name<\/th>\n      <th>hgnc_id<\/th>\n      <th>havana_gene<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"dom":"Blfrtip","buttons":["copy","csv","excel","pdf","print"],"lengthMenu":[[10,25,50,-1],["10","25","50","All"]],"columnDefs":[{"className":"dt-right","targets":[2,3,5,8,9]},{"orderable":false,"targets":0},{"name":" ","targets":0},{"name":"gene_id","targets":1},{"name":"n","targets":2},{"name":"mean_log2FC","targets":3},{"name":"mean_padj","targets":4},{"name":"best_log2FC","targets":5},{"name":"best_padj","targets":6},{"name":"seqname","targets":7},{"name":"start","targets":8},{"name":"end","targets":9},{"name":"strand","targets":10},{"name":"ENSID","targets":11},{"name":"gene_name","targets":12},{"name":"hgnc_id","targets":13},{"name":"havana_gene","targets":14}],"order":[],"autoWidth":false,"orderClasses":false}},"evals":[],"jsHooks":[]}</script>

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
