cd /network/storage01/ino/projects/2014hack/mock-5-ecoli
reads=reads/Sorted*R1*.fasta.gz
gis='556503834 407479587 15829254 91209055 215485161'
out=~/git/2014hack/data/mock-5-ecoli/ecoli_pair_counts.csv
echo reads,${gis//\ /,} > $out
parallel -k zcat {1} '|' grep -c "'>'"gi"'|'"{2} ::: $reads ::: $gis \
    | paste -d, <(for r in $reads; do echo $r; done) - - - - - \
  >> $out
