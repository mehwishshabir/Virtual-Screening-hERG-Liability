# 3D Pharmacophore Modeling for hERG Inhibition Liability

## Project Overview
This project focuses on the development and validation of a 3D pharmacophore model to identify inhibitors of the **hERG (human Ether-à-go-go-Related Gene)** potassium channel. hERG inhibition is a critical "anti-target" in drug discovery, as it can lead to long QT syndrome and sudden cardiac arrest. 

Using **MOE (Molecular Operating Environment)**, I developed a high-accuracy model to distinguish between active and inactive substrates, ensuring drug candidates meet FDA safety standards.

## Methodology
The workflow followed a rigorous computational drug design protocol:
1. **Database Preparation:** Imported hERG inhibitor datasets and generated a packed conformational database (`db_ConfPack`).
2. **Template Selection:** Selected **Molecule 3** (EC50: 0.0267 nM) as the training template due to its high potency.
3. **Feature Selection:** Identified key chemical features including Hydrogen Bond Donors, Acceptors, Hydrophobes, and Aromatic rings.
4. **Virtual Screening:** Screened "Unknown" datasets to predict hERG liability in novel compounds.

The final model was optimized for the best balance between Sensitivity and Specificity.

## Pharmacophore Query Configuration
The query consists of four primary features strategically positioned to mimic the binding mode of highly active hERG inhibitors.

![Pharmacophore Search Setup](images/Features.png)
*Figure 1: 3D Pharmacophore model showing the spatial arrangement of identified features: F1: Don&Acc (pink), F2: Hyd (green), F3: Aro (orange), and F4: Acc2 (cyan). Inter-feature distances (Å) are provided to define the specific geometry required for hERG interaction.*

## Performance of Model
The model has distinguished between active and inactive compounds. The model gave 86.67% accuracy with 1 false positive and 1 false negative compound. The model correctly predicted 8 actives as actives, so there are 8 true positives and 5 in-actives as in-actives, so there are 5 true negatives. 
The confusion matrix of the final model is as:

### Confusion Matrix
| Actual \ Predicted | Active (hERG Inhibitor) | In-active (Safe) |
| :--- | :---: | :---: |
| **Active** | 8 (True Positive) | 1 (False Negative) |
| **In-active** | 1 (False Positive) | 5 (True Negative) |

### Statistical Summary
* **Sensitivity:** 88.89% (High reliability in identifying hERG inhibitors)
* **Specificity:** 83.33% (Ability to correctly identify non-inhibitors)
* **True Positives:** 8 | **True Negatives:** 5

## Structural Alignment (Stacking)
To confirm the reliability of the model, active conformations were aligned. Approximately **87% of compounds** were identified in a similar spatial manner, confirming the hypothesis.

![Validation Results](images/OutputPH4.png)

*Figure 2: Performance results showing hits ranked by RMSD and EC50 values.*

![Stacked Conformations](images/Stacked_Final.png)

*Figure 3: Overlaid conformations of active hits aligned with the 3D pharmacophore hypothesis.*

## Toxicity Prediction: Unknown Data
The model was used to predict the hERG liability of an unknown dataset. Two significant hits were identified:

| Molecule Code | Conformation No. | RMSD | Status |
| :--- | :--- | :--- | :--- |
| **Mol 1** | 1 | 0.6585 | **Rejected** (hERG Liability) |
| **Mol 7** | 28 | 0.3949 | **Rejected** (hERG Liability) |

![Unknown Set Hits](images/Val_output.png)

*Figure 4: Prediction hits identified from the unknown data set.*

## Conclusion
Molecules/Hits 1 and 7 were declared disqualified for the next phases of virtual screening, as the models were developed for an anti-target hERG. The hit for the model implies that these are active substrate for hERG, so should not become a drug as per FDA standards. Because when they dissolve in blood stream, will react with hERG channels resulting in Torsades de-pointes (TdP) i.e., prolonged QT syndrome, and causes sudden cardiac arrest Therefore, mol 1 and 7 are rejected in this phase.

## Tools Used
* **Software:** MOE (Molecular Operating Environment)
* **Tasks:** Conformational Search, Pharmacophore Mapping, Virtual Screening, Database Management.
