<template>
  <div>
    <ClientOnly>
        <JBrowse :assembly="assembly" :tracks="tracks" />
    </ClientOnly>
  </div>
</template>


<script setup>
    import JBrowse from './JBrowse.vue';

    const assembly = {
        name: 'GRCh38',
        aliases: ['hg38'],
        sequence: {
        type: 'ReferenceSequenceTrack',
        trackId: 'GRCh38-ReferenceSequenceTrack',
        adapter: {
            type: 'BgzipFastaAdapter',
            fastaLocation: {
            uri: 'https://jbrowse.org/genomes/GRCh38/fasta/hg38.prefix.fa.gz',
            },
            faiLocation: {
            uri: 'https://jbrowse.org/genomes/GRCh38/fasta/hg38.prefix.fa.gz.fai',
            },
            gziLocation: {
            uri: 'https://jbrowse.org/genomes/GRCh38/fasta/hg38.prefix.fa.gz.gzi',
            },
        },
        displays: [
            {
            type: 'LinearReferenceSequenceDisplay',
            displayId:
                'GRCh38-ReferenceSequenceTrack-LinearReferenceSequenceDisplay',
            renderer: {
                type: 'DivSequenceRenderer',
            },
            },
        ],
        },
        refNameAliases: {
        adapter: {
            type: 'RefNameAliasAdapter',
            location: {
            uri: 'https://s3.amazonaws.com/jbrowse.org/genomes/GRCh38/hg38_aliases.txt',
            },
        },
        },
    }
    
    const tracks = [
        {
        type: 'BasicTrack',
        trackId:
            'GCA_000001405.15_GRCh38_full_analysis_set.refseq_annotation.sorted.gff',
        name: 'NCBI RefSeq Genes',
        assemblyNames: ['GRCh38'],
        category: ['Genes'],
        adapter: {
            type: 'Gff3TabixAdapter',
            gffGzLocation: {
            uri: 'https://s3.amazonaws.com/jbrowse.org/genomes/GRCh38/ncbi_refseq/GCA_000001405.15_GRCh38_full_analysis_set.refseq_annotation.sorted.gff.gz',
            },
            index: {
            location: {
                uri: 'https://s3.amazonaws.com/jbrowse.org/genomes/GRCh38/ncbi_refseq/GCA_000001405.15_GRCh38_full_analysis_set.refseq_annotation.sorted.gff.gz.tbi',
            },
            },
        },
        },
        {
        type: 'AlignmentsTrack',
        trackId: 'NA12878.alt_bwamem_GRCh38DH.20150826.CEU.exome',
        name: 'NA12878 Exome',
        assemblyNames: ['GRCh38'],
        category: ['1000 Genomes', 'Alignments'],
        adapter: {
            type: 'CramAdapter',
            cramLocation: {
            uri: 'https://s3.amazonaws.com/jbrowse.org/genomes/GRCh38/alignments/NA12878/NA12878.alt_bwamem_GRCh38DH.20150826.CEU.exome.cram',
            },
            craiLocation: {
            uri: 'https://s3.amazonaws.com/jbrowse.org/genomes/GRCh38/alignments/NA12878/NA12878.alt_bwamem_GRCh38DH.20150826.CEU.exome.cram.crai',
            },
            sequenceAdapter: {
            type: 'BgzipFastaAdapter',
            fastaLocation: {
                uri: 'https://jbrowse.org/genomes/GRCh38/fasta/hg38.prefix.fa.gz',
            },
            faiLocation: {
                uri: 'https://jbrowse.org/genomes/GRCh38/fasta/hg38.prefix.fa.gz.fai',
            },
            gziLocation: {
                uri: 'https://jbrowse.org/genomes/GRCh38/fasta/hg38.prefix.fa.gz.gzi',
            },
            },
        },
        }
    ]
</script>

