
SAMtools
========

.. sidebar:: SAMtools
   
   :Version: 1.7
   :Dependencies: gcc/4.9.4
   :URL: https://github.com/samtools/samtools/releases/download/1.7/samtools-1.7.tar.bz2
   :Documentation: http://www.htslib.org/doc/samtools.html


SAM (Sequence Alignment/Map) format is a generic format for storing large nucleotide sequence alignments. SAM aims to be a format that is

- flexible enough to store all the alignment information generated by various alignment programs
- simple enough to be easily generated by alignment programs or converted from existing alignment formats
- compact in file size
- allows most of operations on the alignment to work on a stream without loading the whole alignment into memory
- allows the file to be indexed by genomic position to efficiently retrieve all reads aligning to a locus

SAM Tools provide various utilities for manipulating alignments in the SAM format, including sorting, merging, indexing and generating 	alignments in a per-position format.


Usage
-----

SAMtools can be activated using the module file::

    module load apps/SAMtools/1.7/gcc-4.9.4

Note: The module file also loads the compiler gcc/4.9.4.

Test
----

#. Download the following example files using:

   .. code-block:: bash
   
      cd some_directory
      cp -r /usr/local/packages/apps/SAMtools/1.7/gcc-4.9.4/examples .
      cd examples
      # sample data 
      # ex1.fa - contains 2 sequences cut from the human genome
      # ex1.sam.gz - contains MAQ alignments
      # 00README.txt contains instructions and description of results
      samtools #gives a list of options
      samtools faidx ex1.fa #index the reference FASTA
      samtools view -S -b -t ex1.fa.fai -o ex1.bam ex1.sam.gz #convert SAM to BAM
      samtools index ex1.bam #build index for BAM
      samtools view ex1.bam seq2:450-550 #view a portion of BAM file
      samtools tview -p seq2:450 ex1.bam exl.fa #visually inspect alignments at same location
      samtools mpileup -f ex1.fa ex1.bam #view data in pileup format
      samtools mpileup -vu -f ex1.fa ex1.bam > ex1.vcf #generate uncompressed VCF file of variants
      samtools mpileup -g -f ex1.fa ex1.bam > ex1.bcf #generate compressed VCF file of variants
      

Installation notes
------------------

SAMtools was compiled using the
:download:`install_SAMtools.sh </sharc/software/install_scripts/apps/SAMtools/1.7/gcc-4.9.4/install_SAMtools.sh>` script, the module
file is
:download:`/usr/local/modulefiles/apps/SAMtools/1.7/gcc-4.9.4 </sharc/software/modulefiles/apps/SAMtools/1.7/gcc-4.9.4>`.
