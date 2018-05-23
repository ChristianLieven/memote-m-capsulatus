# iCL730: A genome-scale metabolic model of _Methylococcus capsulatus_ Bath

* Brief Model Description:

This repository contains the a metabolic model of _Methylococcus capsulatus_ Bath.

* Model KeyWords:

**GEM Category:** Species; **Utilisation:** maximising growth; **Field:** metabolic-network reconstruction; **Type of Model:** curated, reconstruction; **Model Source:** [BMID000000141026](https://www.ebi.ac.uk/biomodels-main/BMID000000141026); **Taxonomy:** _Methylococcus capsulatus_ Bath; **Metabolic System:** General Metabolism; **Bioreactor**

* Last update: 2017-09-18

* The model:

|Taxonomy | Template Model | Reactions | Metabolites| Genes |
|:-------:|:--------------:|:---------:|:----------:|:-----:|
|_Methylococcus capsulatus_ Bath|[BMID000000141026](https://www.ebi.ac.uk/biomodels-main/BMID000000141026)|898|877|730|

This repository is administered by Christian Lieven ([@ChristianLieven](https://github.com/ChristianLieven)), Center for Biosustainability, Technical University of Denmark, Kgs. Lyngby 2800

## Installation

### Required Software:

* The scripts were generated using the following environment configuration. Importing the model has only been tested with [cobrapy](https://github.com/opencobra/cobrapy), which we recommend for any work with the model.

```
System Information
==================
OS           Darwin
OS-release   16.7.0
Python        2.7.9

Package Versions
================
pip           9.0.1
setuptools   34.0.2
cobra         0.8.1
future       0.16.0
swiglpk       1.4.4
optlang       1.2.1
ruamel.yaml 0.14.12
pandas       0.22.0
numpy        1.14.0
tabulate      0.8.2
lxml          3.7.3
scipy        0.18.1
matplotlib    1.4.3
palettable    2.1.1
```

### Contribute To Development
You have several options to contribute to and ultimately improve the metabolic model of Methylococcus capsulatus Bath.

#### Provide Feedback (Simple)
1. Click on `Issues` in the top toolbar here on Github
2. Click on the green button `New issue` to open a new issue
3. Report errors or issues, provide feedback, or simply ask questions
4. Submit the issue by clicking `Submit new issue`

#### Participate (Advanced)
1. Fork the repository to your own Github account
2. Create a new branch from [`develop`](https://github.com/ChristianLieven/memote-m-capsulatus/develop).
3. Make changes to the model
    + [cobrapy](https://github.com/opencobra/cobrapy) is highly recommended for making changes
    + Make a Pull Request to the `devel` branch, including changed `txt`, `yml` and `xml` files

## Complementary Scripts

* `1. MappingMNXtoBIGG.ipynb`: Maps metabolite and reaction IDs from the MetaNetX namespace to the BiGG namespace semi-automatically using both the ver 1.0 as well as the ver 2.0 mapping dumps from MetaNetX. Moreover removes all formulas that contained brackets. Adds EC numbers based on MetaNetX reaction properties dump (MNXref Version 2015/09/03) and KEGG subsystem information.

* `2. Curation of the Energy Metabolism.ipynb`: Curates reactions involved in methane membrane diffusion and oxidation, and the respiratory chain.

* `3. Fixes to enable growth on Methane!.ipynb`: Curates unbalanced and inverted reactions. Adds diffusion reactions for water and oxygen. Gapfilling of amino acid biosynthesis reactions, whenever most of the genes of the corresponding pathway were present. Partially removes entities with MNX IDs that cannot be mapped.

* `4. Full-Scale Biomass Reaction And Further Corrections.ipynb`: Adds a more extensive biomass reaction, and further curates required precursor biosynthesis pathways including CoA & AcCoA, Iron, Even Fatty Acids, Odd Fatty Acids, Cyclopropane Fatty Acids, Ubiquinol, Lanosterol, FAD, FMN, Riboflavin, NAD, NADP, Heme, Glutathione, Cobalt, Cobalamine/ Vitamin B12, Thiamin, Myo-Inositol, Phospholipids (specifically Phosphatidylglycerol, Phosphatidylserine, Phosphatidylethanolamine and Phosphatidylcholine), Cardiolipin, and Peptidoglycan (adapted from the E.coli genome-scale model - iJO1366). Adds NGAM reaction.

* `5. Close Reaction Balances and Implement N-Assimilation.ipynb`: Closes the mass and charge balances of 133 reactions. Curates the Nitrogen metabolism, adds reactions related to the oxidation of ammonia, and adds the reduction of nitrate and nitrite.

* `6. Identifying Transport Reactions and Implementing the MIRIAM annotations.ipynb`: Removes all remaining reactions and metabolites from the MetaNetX namespace. Identifies transmembrane helices using TMHMM (http://www.cbs.dtu.dk/services/TMHMM/) and PsortB, and BLAST against TCDB. Moves annotations from the `notes` field to the `annotations` field, and reformats them to comply with the MIRIAM guidelines, specifically using MIRIAM URIs (https://co.mbine.org/standards/miriam).

* `7. Partial Validation with data from 'Growth yields of methanotrophs' by Leak and Dalton 1986.ipynb`: Curates various model reactions (i.e. TCA cycle) following evidence in literature and updates constraints accordingly. Defines an early validation scheme for the electron transfer modes.

* `8. Corrections to Validation.ipynb`: Further curation based on detailed reading of available literature. Closes ATP-generating loops. Constrains NGAM to fixed value. Removes or corrects reactions that bypass NH3 assimilation through GS/GOGAT or Alanine Dehydrogenase. Identifies genes without corresponding reactions and the portion of these genes that can be labeled with an EC number. These should be looked into in the future! Recaclulated the mass-balance and molecular weight of the biomass reaction. Defines another approach to validating the model using the electron transfer modes.

* `9. Finishing Touches.ipynb`: Fixes identifier suffixes in the BiGG namespace. Imports reaction annotation from iJO1366, iRC1080, iJN678, iHN637 and metabolite annotation from iJO1366, iRC1080, iYO844. Removes exchanges that are not required.

* `10. Transport Reactions.ipynb`: Adds transport reactions semi-automatically based on PsortB, TransportDB and TCDB classification and the genome annotation. The transporter mechanism was inferred from the BiGG database.

* `11. Metabolic Map.ipynb`: Adds nitrogenase reaction and transport for N2. Synchronises metabolic map identifiers with identifiers from the model.

* `12. ApplyMemoteDrivenCuration.ipynb`: Checks and corrects for metabolites without charge, reactions without GPR, imbalanced reactions, syntax inconsistencies, precursors that cannot be produced.

* `13. Fixing compartments.ipynb`: Fixes SBML error that occured due to metabolites being in a compartment that was not formally defined.

* `Model 15 Calculations.ipynb`: Interactive notebook to allow parameter exploration and growth in different conditions.

## Complementary Data

* `putative_transporter_genes_not_considered.xls`: Combined output from PsortB 3.0, TransportDB and TCDB for genes which were not pursued in this study either because the transport mechanism or the substrate(s) were unclear. In the future, these could be looked at when improving the model.

* `SupplementTable1.docx`: Stoichiometry of the biomass reaction in mcapsBath.

* `SupplementFigure1.png`: High-resolution export of the genome-scale [metabolic map](https://github.com/ChristianLieven/memote-m-capsulatus/blob/master/MetabolicMap/MethylococcusCapsulatusMetabolismMap.json) of the mcapsBath. The metabolic map was constructed using [escher](https://escher.github.io/).