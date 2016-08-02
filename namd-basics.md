
# NAMD Basic Workflow


## DNA Methylation Patch notes

To apply methylation patches to CYT, first generate the DNA model and then apply 5MC* patches to the corresponding bases. There are two types of 5MC*patches: 5MC1 and 5MC2.

### 5MC1 patch

> ! Patch to generate 5-methylcytosine (base only)
> ! use in generate statement
> ! checked for consistency with new NA params, adm jr.,  9/98

Taken from `toppar_all36_na_modifications.str` file. `5MC1` is used in psfgen `generate` command to create a **NEW** 5-methylcytosine. 

### 5MC2 patch

> ! Patch to convert cytosine in DNA to 5-methylcytosine
> ! use in PATCH statement followed by AUTOgenerate ANGLes DIHE

Taken from `toppar_all36_na_modifications.str` file. `5MC2` is used in psfgen `patch` command to **CONVERT** a CYT base to 5-methylcytosine.