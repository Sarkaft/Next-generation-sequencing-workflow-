Comprehensive Next-Generation Sequencing (NGS) Workflow
​Next-Generation Sequencing (NGS), also known as massively parallel sequencing, has revolutionized genomics by allowing the simultaneous sequencing of millions of DNA fragments. As an expert in genetics and genomics, it is essential to understand the intricate steps that ensure data accuracy, high throughput, and biological relevance.
​I. Pre-Sequencing: Sample Preparation & Quality Control (QC)
​Before the sequencing reaction begins, the biological sample must be meticulously prepared to ensure high-quality input.
​Nucleic Acid Extraction: Isolation of DNA (genomic, cfDNA) or RNA (total RNA, mRNA) using chemical or magnetic bead-based methods.
​Quantification & Purity Check:
​Fluorometric: (e.g., Qubit) for precise concentration measurement.
​Spectrophotometric: (e.g., NanoDrop) to assess protein (A_{260}/A_{280}) and carbohydrate/phenol (A_{260}/A_{230}) contamination.
​Fragmentation: Breaking high-molecular-weight DNA into specific size ranges.
​Mechanical: Covaris (ultrasonic) for precise, random shearing.
​Enzymatic: Tagmentation (transposases) or fragmentases.
​II. Library Preparation
​The goal is to transform fragments into a format compatible with the sequencing platform.
​End-Repair & A-Tailing: * Overhangs resulting from fragmentation are filled or chewed back to create blunt ends.
​A single "A" base is added to the 3' end to prevent self-ligation and facilitate adapter attachment.
​Adapter Ligation: Synthetic double-stranded DNA molecules are ligated to both ends. These contain:
​P5/P7 Sequences: For flow cell attachment.
​Index (Barcodes): Typically 6–10 bp codes allowing sample multiplexing.
​Sequencing Primer Binding Sites (SBS): Where the sequencing reaction initiates.
​PCR Enrichment (Optional): Amplification of the library to ensure sufficient concentration, though "PCR-free" workflows are preferred for avoiding GC-bias.
​Final Library QC: Using a Bioanalyzer or TapeStation to verify the size distribution (fragment length) and molarity.
​III. Cluster Generation (Template Preparation)
​To generate a detectable signal, individual library molecules must be amplified into clonal clusters.
​Bridge Amplification (Illumina): Library fragments hybridize to the flow cell surface. Through repeated cycles of isothermal denaturation and synthesis, "clusters" of ~1,000 identical copies are formed in situ.
​Emulsion PCR (Ion Torrent): DNA fragments are attached to beads and amplified within oil droplets.
​Nanoball Generation (MGI): Rolling circle amplification creates long single-stranded DNA "nanoballs" which are then patterned onto a flow cell.
​IV. Sequencing Chemistries
​1. Sequencing by Synthesis (SBS - Illumina)
​The industry standard. Fluorescently labeled, reversibly terminated nucleotides are added one by one.
​Step: Incorporate \rightarrow Image \rightarrow Cleave/Wash \rightarrow Repeat.
​Data: High accuracy (>Q30), short reads (50–300 bp).
​2. Single Molecule Real-Time (SMRT - PacBio)
​A polymerase is anchored at the bottom of a Zero-Mode Waveguide (ZMW). As it incorporates labeled bases, the pulses of light are recorded.
​Benefit: Long reads (up to 100kb+), detects base modifications (epigenetics).
​3. Nanopore Sequencing (Oxford Nanopore)
​Measures the disruption in electrical current as a single strand of DNA passes through a biological nanopore.
​Benefit: Ultra-long reads, portable devices, real-time data streaming.
​V. Bioinformatic Analysis Pipeline
​Data processing is categorized into three distinct phases:
​Phase 1: Primary Analysis (Base Calling)
​Conversion of raw signals (light pulses or ionic current changes) into digital text format.
​Output: FASTQ files (Sequence + Quality scores).
​QC: FastQC or MultiQC to assess Phred scores (Q = -10 \log_{10} P).
​Phase 2: Secondary Analysis (Alignment & Variant Calling)
​Alignment: Mapping reads to a reference genome (using BWA-MEM or Bowtie2).
​Deduplication: Removing PCR duplicates (Picard).
​Variant Calling: Identifying SNPs, Indels, and Structural Variants (GATK, FreeBayes).
​Output: BAM/CRAM (Alignment) and VCF (Variants).
​Phase 3: Tertiary Analysis (Interpretation)
​Annotation: Using databases (ClinVar, dbSNP, gnomAD) to determine the impact of variants.
​Filtering: Narrowing down candidates based on inheritance patterns or allele frequency.
​Clinical Reporting: Synthesis of findings into a diagnostic or research report.
​VI. Summary of Key File Formats
