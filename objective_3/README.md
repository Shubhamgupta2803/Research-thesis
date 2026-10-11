This Python script performs donor demultiplexing and quality-control refinement for a multiplexed single-cell dataset, using two sources of donor identity information:
- HTO (hashtag oligonucleotide) data: identifies donor labels from hashtag counts.
- SNP data: assigns donor identities using genetic variants.
Its goal is to reconcile these assignments, identify likely doublets and negative/unassigned cells, and generate a refined donor label for each cell.
