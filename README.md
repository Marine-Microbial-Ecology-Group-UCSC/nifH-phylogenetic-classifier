# nifH-phylogenetic-classifier using a Classification and Regression Tree (CART)

This script phylogenetically classifies _nifH_ gene (or amplicon) sequences using the Classification and Regression Tree (CART) from [Frank et al., 2016](https://doi.org/10.1111/1758-2229.12455).  

The scripts directory includes the original version by Frank for Python 2 as well as an updated version for Python 3. The updated version does not require you to specify the residue position in _Azotobacter vinelandii_ NifH (protein) where multiple sequence alignment starts. Instead the script calculates the start residue, knowing that first sequence in the alignment is NifH from _Azotobacter vinelandii_ (WP_012698955.1).  (A warning is issued if the first sequence does not appear to be from _A. vinelandii_.)  We recommend that you use the updated script or the automated alternative described below.

To use the CART classifier you must have installed Biopython.

You can verify the classifier with the included multiple sequence alignment:
```
python scripts/NifH_Clusters.py data/CART_Test_Atlantic.fasta
```
which outputs CART_Test_Atlantic_Clusters.fasta.


### Automated alternative

If you are working with _nifH_ amplicons, e.g. ASVs from DADA2, then consider using our CART classifier in [nifH_amplicons_DADA2](https://github.com/jdmagasin/nifH_amplicons_DADA2) as the ancillary script [NifHClustersFrank2016](https://github.com/jdmagasin/nifH_amplicons_DADA2/tree/master/scripts.ancillary/Annotation/NifHClustersFrank2016). This version predicts open reading frames (using FragGeneScan), performs a multiple sequence alignment (using MAFFT), and then runs the CART classifier.  All of the required external tools (including Biopython) are provided by the miniconda environment that you create when you install nifH_amplicons_DADA2.
