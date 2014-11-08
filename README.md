2014 Hackathon at Newton Institute
==================================

## Day1
- Added concoct StrainMock mappings and contigs
- extracted 5 E Coli strains reads from StrainMock
- get counts per ecoli genome

```
cd /network/storage01/ino/projects/2014hack/mock-5-ecoli
reads=reads/Sorted*R1*.fasta.gz
gis='556503834 407479587 15829254 91209055 215485161'
parallel -k zcat {1} '|' grep -c "'>'"gi"'|'"{2} ::: $reads ::: $gis \
    | paste -d, <(for r in $reads; do echo $r; done) - - - - - \
    > ~/git/2014hack/data/mock-5-ecoli/ecoli_pair_counts.csv
```
