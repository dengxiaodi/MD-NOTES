
# Charmm36 patches

## 1. RNA to DNA patch

Patches are needed to convert RNA to DNA. Two patches are needed in charmm36 force field files: `DEOX` and `DEO5`

> !2010/2011 additions
> ! ejd, 2010 RNA update
> ! adm, 2011 DNA update
> !  For DNA update, new atom type required for P of DNA. This required
> !  replication of a number of parameters and the creation of new
> !  patches, DEOX and DEO5, to convert RNA to DNA, such that previous
> !  CHARMM scripts to generate DNA will no longer work.  Note that the
> !  atom type change to P3 ONLY applies to the phosphodester linkage in
> !  DNA and NOT to terminal phosphates, DMP etc.

> !example of new generate/patch combination to generate DNA
> !
> !read sequence card
> !* 1bna, strand 1
> !*
> !3
> !cyt gua cyt
> !
> !generate a first 5ter last 3ter setup warn
> !
> !patch deo5 a 1 setup warn !special patch for 5-terminal deoxy residue
> !patch deox a 2 setup warn !new patch to convert RNA to DNA
> !patch deox a 3 setup warn !no special patch required for 3-terminal deoxy residue
> !
> !`autogenerate angles dihedrals` !**Use of AUTOGENERATE is essential**

### DEOX patch

> ! Patch to make non 5-terminal DEOXyribose nucleotides
> ! Follow with AUTOGENERATE ANGLES DIHEDRALS 

`DEOX` patch is used to convert non 5-terminal RNA to DNA residue. **this patch is also used to patch 3-terminal residue**.

### DEO5 patch 

> ! Patch to make the 5-terminal nucleotide into DEOXYribose
> ! Follow with AUTOGENERATE ANGLES DIHEDRALS 

`DEO5` patch is used to convert 5-terminal RNA residue to DNA residue. 



## 2. DNA Methylation Patch notes

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