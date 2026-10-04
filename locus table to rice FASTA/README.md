# Locus table to rice FASTA

[Open in Google Colab](https://colab.research.google.com/github/arif202536599-cloud/Genes_Ids/blob/main/locus%20table%20to%20rice%20FASTA/TBtools_Loci_to_FASTA_Colab.ipynb)

## Run the notebook

1. Open the Colab link and use a CPU runtime.
2. Run the cells in order and upload your TBtools locus table, such as CDS_TBTOOL.txt.
3. The notebook downloads the matching MSU/UGA Rice Release 7 complete genome and GFF3.
4. Download TBtools_Rice_FASTA_Results.zip when the final cell finishes.

The input is a headerless tab-separated TBtools table: chromosome, transcript ID, start, end, strand, followed by attribute key/value pairs including Parent. Coordinates must match the supplied annotation. Despite its filename, the tested CDS_TBTOOL.txt contains complete mRNA spans, not joined coding sequences.

## Outputs

| File | Sequence or contents |
| --- | --- |
| gene_genomic.fasta.gz | Complete annotated gene span, including introns |
| transcript_genomic.fasta.gz | Transcript genomic span, including introns |
| transcript_cdna.fasta.gz | Joined transcript exons |
| transcript_cds.fasta.gz | Joined annotated coding segments |
| gene_ids.txt | Selected gene IDs |
| transcript_ids.txt | Selected transcript IDs |
| gene_transcript_map.csv | Gene/transcript relationships and coordinates |
| ml_transcript_features.csv | Numerical features for a later labeled ML study |
| MOC1_genomic.fasta, MOC1_cdna.fasta, MOC1_cds.fasta | MOC1 sequences, when selected |
| provenance.json | Reference URLs, checksums and extraction rules |

The notebook extracts existing reference sequence; it does not predict bases or train an ML model. GFF coordinates are 1-based and inclusive; negative-strand sequences are reverse complemented. Gene spans, spliced cDNA and CDS are separate outputs.

## Validation

Tested using the supplied 66,338-row TBtools table and matching Release 7 references: 55,986 genes and 66,338 transcripts. Synthetic tests checked inclusive coordinates and negative-strand exon joining. The Release 7 MOC1 model LOC_Os06g40780.1 yielded 4,963 bp genomic span, 2,064 bp cDNA and 2,001 bp joined CDS.

These reference sequences alone do not establish expression in stem tissue or effects on lodging. RNA-seq alignment/quantification and a suitable experimental design are needed for those questions.
