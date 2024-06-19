## B250_diricore

This is the official Diricore documentation.

# Prerequisites

Define a BASE_DIR.
Diricore was built with Python 2.7.18. Build a new conda environment with the packages in the file
```
diricore_packages.txt
```

Please download necessary index data from:

```
https://hub.dkfz.de/s/Xooc4SCF6YpRfLD
```

Store the data at:

```
$BASE_DIR/static/${species}/
```

# Metadata Input
Diricore analyses require the input of two metadata files:

```
$PROJECT_DIR/analysis/input/metadata/rpf_density_samplenames.tsv
$PROJECT_DIR/analysis/input/metadata/rpf_density_contrasts.tsv
```
In which your PROJECT_DIR is the combined BASE_DIR and dataset name:

```
PROJECT_DIR="$BASE_DIR/$dataset_id"
```

The 'samplenames' file is 3-column, tab-separated.
1st column: Your samplename, 2nd column: Your samplename, 3rd column: Hex colour code

```
Batch1_S1_NC_DMSO       Batch1_S1_NC_DMSO       #EC28FA
```

The 'contrasts' file is 3-column, tab-separated.
1st column: Your test-group samplename, 2nd column: Your control-group samplename, 3rd column: Hex colour code

```
Batch1_S2_NC_Torin      Batch1_S2_NC_Torin      #7CBA4C
```


# Subsequence Analysis
Based on your file and data architecture, the subsequence analysis requires additional arguments:
$1: Dataset ID or name; $2: The reference genome (hg19 or mm10); $3: Min read count per transcript; $4: all/ all_unique (Reads with or without duplicates)

```
$BASE_DIR/software/diricore/subsequence_analysis.sh 20910 mm10 50 all_unique
```

# 5' Density Analysis
$1: Dataset ID or name; $2: The reference genome (hg19 or mm10); $3: Min read count per transcript; $4: all/ all_unique (Reads with or without duplicates)

```
$BASE_DIR/software/diricore/rpf_density_analysis.sh 20910 mm10 50 all_unique
```

