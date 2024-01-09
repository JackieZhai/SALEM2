# ![SALEM2 Logo](assets/SALEM2-Logo.svg)

SA<u>LE</u>M<sup>2</sup>: Segment Anything in <u>L</u>ight and <u>E</u>lectron <b>M</b>icroscopy via <b>M</b>embrane Guidance

![SALEM2 Dataset Repository Overview](assets/SALEM2-Dataset.svg)
<br>
(This figure has been modified to match the text in "Datasets" section.)

Codes and data collections will be released upon publication.


### Comparison with General-purpose Methods

Quantitative comparison: [SAM](https://github.com/facebookresearch/segment-anything), [HQ-SAM](https://github.com/SysCV/sam-hq), [Mobile-SAM](https://github.com/ChaoningZhang/MobileSAM) (from HQ-SAM) and [Micro-SAM](https://github.com/computational-cell-analytics/micro-sam), as well as trained SAM and HQ-SAM in both LM and EM datasets.

![SALEM2 Compare General-purpose Methods](assets/Compare-GM.png)


### Comparison with Specialized Supervised Methods

Qualitative comparison: [CellPose](https://github.com/MouseLand/cellpose) in LM, [ilastik](https://www.ilastik.org/) (pretrained models from [https://bioimage.io/#/?partner=ilastik](https://bioimage.io/#/?partner=ilastik)) and [Superhuman](https://github.com/torms3/Superhuman) (onnx models from [https://github.com/seung-lab/DeepEM/releases](https://github.com/seung-lab/DeepEM/releases)) in EM.

#### Elongated cells in LM:

<table>
    <tr>
        <td><img src="assets/Elong-528-raw.jpg" width="200pt"></td>
        <td><img src="assets/Elong-528-label.jpg" width="200pt"></td>
        <td><img src="assets/Elong-528-CellPose.png" width="200pt"></td>
        <td><img src="assets/Elong-528-OmniPose.png" width="200pt"></td>
        <td><img src="assets/Elong-528.png" width="200pt"></td>
    </tr>
    <tr style="text-align:center">
        <td>Raw</td>
        <td>GT</td>
        <td>CellPose<br>(<a href="http://dx.doi.org/10.1038/s41592-020-01018-x">Nat. Methods 2021</a>)</td>
        <td>OmniPose<br>(<a href="http://dx.doi.org/10.1038/s41592-022-01639-4">Nat. Methods 2022</a>)</td>
        <td>SALM<sup>2</sup><br>(Ours)</td>
    </tr>
</table>

#### Weak boundaries in LM:

<table>
    <tr>
        <td><img src="assets/Weak-738-raw.jpg" width="200pt"></td>
        <td><img src="assets/Weak-738-label.jpg" width="200pt"></td>
        <td><img src="assets/Weak-738-CellPose.jpg" width="200pt"></td>
        <td><img src="assets/Weak-738.jpg" width="200pt"></td>
    </tr>
    <tr style="text-align:center">
        <td>Raw</td>
        <td>GT</td>
        <td>CellPose<br>(<a href="http://dx.doi.org/10.1038/s41592-020-01018-x">Nat. Methods 2021</a>)</td>
        <td>SALM<sup>2</sup><br>(Ours)</td>
    </tr>
</table>

#### CREMI-B (blur and misalignment) in EM:

<table>
    <tr>
        <td><img src="assets/NcremiB_origin.gif" width="200pt"></td>
        <td><img src="assets/NcremiB.gif" width="200pt"></td>
        <td><img src="assets/NcremiB_labels.gif" width="200pt"></td>
        <td><img src="assets/CREMI-B15-Superhuman.jpg" width="200pt"></td>
        <td><img src="assets/CREMI-B15.jpg" width="200pt"></td>
    </tr>
    <tr style="text-align:center">
        <td>Raw<br>(sections 12-18)</td>
        <td>Raw with preprocessing<br>(sections 12-18)</td>
        <td>GT<br>(sections 12-18)</td>
        <td>Superhuman (section 15)<br>(<a href="http://dx.doi.org/10.1038/s41592-021-01330-0">Nat. Methods 2022</a>)</td>
        <td>SAEM<sup>2</sup> (section 15)<br>(Ours)</td>
    </tr>
</table>

#### CREMI-C (blur and missing sections) in EM:

<table>
    <tr>
        <td><img src="assets/NcremiC_origin.gif" width="200pt"></td>
        <td><img src="assets/NcremiC.gif" width="200pt"></td>
        <td><img src="assets/NcremiC_labels.gif" width="200pt"></td>
        <td><img src="assets/CREMI-C103-ilastik.jpg" width="200pt"></td>
        <td><img src="assets/CREMI-C103.jpg" width="200pt"></td>
    </tr>
    <tr style="text-align:center">
        <td>Raw<br>(sections 100-106)</td>
        <td>Raw with preprocessing<br>(sections 100-106)</td>
        <td>GT<br>(sections 100-106)</td>
        <td>ilastik (section 103)<br>(<a href="http://dx.doi.org/10.1038/s41592-019-0582-9">Nat. Methods 2019</a>)</td>
        <td>SAEM<sup>2</sup> (section 103)<br>(Ours)</td>
    </tr>
</table>

More results can be found in Google Drive: [BBC039](https://drive.google.com/drive/folders/1VsXcneTsRx5YMzfkZyKcWtbndbpjnm1m?usp=sharing) and [NeurIPS22-CellSeg](https://drive.google.com/drive/folders/1BG9F-LRvL9JaDYOige8bn-S1TWCX1kDE?usp=sharing). We used CellPose and OmniPose with the configurations of `nuclei (flow_threshold=0.3)` for Bare Nuclei, `tissuenet (flow_threshold=0.6)` for Weak Boundary, `nuclei (flow_threshold=0.6)` and `omnipose (bact_phase_omni)` for Elongated. We used the open-sourced trained models of ilastik and Superhuman with default configurations.