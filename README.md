                                                3D Pharmacophore Modeling for hERG Inhibition Liability
Project Overview:
This project focuses on the development and validation of a 3D pharmacophore model to identify inhibitors of the hERG potassium channel. hERG inhibition is a critical "anti-target" in drug discovery, as it can lead to long QT syndrome and sudden cardiac arrest.
Using MOE (Molecular Operating Environment), I developed a high-accuracy model to distinguish between active and inactive substrates, ensuring drug candidates meet FDA safety standards.

Methodology:
The workflow followed a rigorous computational drug design protocol:
1.	Database Preparation: Imported hERG inhibitor datasets and generated a packed conformational database (db_ConfPack).
2.	Template Selection: Selected Molecule 3 (EC50: 0.0267 nM) as the training template due to its high potency.
3.	Feature Selection: Identified key chemical features including Hydrogen Bond Donors, Acceptors, Hydrophobes, and Aromatic rings.
4.	Virtual Screening: Screened "Unknown" datasets to predict hERG liability in novel compounds.
The final model was optimized for the best balance between Sensitivity and Specificity.

Pharmacophore Query Configuration:
The query consists of four primary features strategically positioned to mimic the binding mode of highly active hERG inhibitors.
![Pharmacophore Search Setup](Screening_image.png)
Figure 1: Pharmacophore Query Editor and Search interface in MOE.

Validation & Performance:
The model was validated against a test set, achieving an Accuracy of 86.67%.
Confusion Matrix:
•	True Positives: 8 (Actives correctly identified)
•	True Negatives: 5 (In-actives correctly excluded)
•	Sensitivity: 88.89%
•	Specificity: 83.33%
![Validation Results](OutputPH4.png)
*Figure 2: Performance results showing hits ranked by RMSD and EC50 values.*

3. Structural Alignment (Stacking)
To confirm the reliability of the model, active conformations were aligned. Approximately 87% of compounds were identified in a similar spatial manner.
![Stacked Conformations](Stacked_Final.jpg)
*Figure 3: Overlaid conformations of active hits aligned with the 3D pharmacophore hypothesis.*

## Toxicity Prediction: Unknown Data
The model was used to predict the hERG liability of an unknown dataset. Two significant hits were identified:
Molecule Code	Conformation No.	RMSD	Status
Mol 1	1	0.6585	Rejected (hERG Liability)
Mol 7	28	0.3949	Rejected (hERG Liability)
![Unknown Set Hits](Val_output.png)
*Figure 4: Prediction hits identified from the unknown data set.*

Conclusion: 
Molecules/Hits 1 and 7 were declared disqualified for the next phases of virtual screening, as the models were developed for an anti-target hERG. The hit for the model implies that these are active substrate for hERG, so should not become a drug as per FDA standards. Because when they dissolve in blood stream, will react with hERG channels resulting in Torsades de-pointes (TdP) i.e., prolonged QT syndrome, and causes sudden cardiac arrest Therefore, mol 1 and 7 are rejected in this phase.


Tools Used:
•	Software: MOE (Molecular Operating Environment)
•	Tasks: Conformational Search, Pharmacophore Mapping, Virtual Screening, Database Management.

