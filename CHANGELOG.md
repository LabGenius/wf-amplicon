# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).


## [v1.1.4]
### Changed
- Reconcile template with v5.3.0 and v5.3.1
- IGV output files are only output if `--igv` is used

## [v1.1.3]
### Fixed
- Automated basecaller detection failing in some circumstances.
### Changed
- Updated Ezcharts to v0.11.2.

## [v1.1.2]
### Fixed
- The workflow failing in _de novo_ mode when all reads for a sample came from the same strand.

### Changed
- The report now skips read length histograms etc. if there were no reads left after filtering.

## [v1.1.1]
### Changed
- Updated Medaka to v1.12.0.

### Removed
- The `--medaka_model` parameter as the appropriate Medaka model is now automatically determined from the input data.
- The now redundant `--basecaller_cfg` parameter as its value is now automatically detected from the input data on a per-sample basis.

### Added
- `--override_basecaller_cfg` parameter for cases where automatic selection fails or users wish to override the automatic choice.

## [v1.1.0]
### Fixed
- The `miniasm` process requesting too little memory in some cases.
- Spurious out-of-memory errors for the SPOA process.
- Variant calling mode with `--combine_results` failing with a single sample/barcode.

### Changed
- When there is at least one amplicon depth plot that shows more than one sample, the depth plots now use consistent colours for individual samples across the different amplicons.
- The workflow now uses the `fastcat` read length and quality histograms instead of the per-read stats in the report process.

### Added
- IGV config json file to the outputs (in order to visualise the alignments and called variants).

## [v1.0.4]
### Fixed
- The workflow failing when there were tab characters in the FASTA header lines of reference sequences.

### Changed
- The way the reference sequence IDs are sanitised to prevent issues with special characters.

## [v1.0.3]
### Fixed
- The workflow failing when there was a whitespace in the name of the reference file.

### Changed
- The report now consistently uses the sanitised reference sequence IDs throughout.
- Some formatting changes to github issue template.

## [v1.0.2]
### Fixed
- Incorrect CPU use specification for the `medakaVariant` process.

## [v1.0.1]
### Changed
- Default for `--reads_downsampling_size` to 1500 to limit memory usage.
- Default for `--medaka_target_depth_per_strand` to 150 as the workflow now supports longer amplicons.

### Fixed
- The workflow failing when a sample had only a single read.

## [v1.0.0]
### Added
- Memory requirements for each process.

### Changed
- Reworked docs to follow new layout.

## [v0.6.2]
### Fixed
- The de-novo QC stage failing when not a single input read re-aligns against the draft consensus.

## [v0.6.1]
### Changed
- More informative warnings for failed samples in the report intro section.

## [v0.6.0]
### Added
- Assembly step to de-novo consensus mode to handle longer amplicons. README was updated accordingly.

### Removed
- Default local executor CPU and RAM limits

## [v0.5.0]
### Changed
- Names of barcoded directories in the sample sheet now need to be of format `barcodeXY`.

### Added
- Support for specifying reference sequences for individual samples with an extra `"ref"` column in the sample sheet.

## [v0.4.1]
### Changed
- The workflow now also emits VCF index files as well as BAM / VCF index files for combined outputs when running with `--combine_results`.

### Fixed
- Emitting an empty consensus FASTA file when consensus generation failed in certain situations. Instead, no file is emitted.
- Now uses the downsampled BAM for `medaka annotate`.

### Removed
- Misleading allelic balance statistic in report.

## [v0.4.0]
### Added
- Running the workflow without a reference will switch the workflow to "no-reference mode" and will use SPOA to construct a consensus sequence _de novo_.

## [v0.3.5]
### Changed
- The workflow now also outputs BAM index files.

## [v0.3.4]
### Changed
- The workflow now downsamples reads for each amplicon to be in the suitable depth range for Medaka.

## [v0.3.3]
### Added
- MacOS ARM64 support.

## [v0.3.2]
### Changed
- Updated Medaka to 1.9.1.

## [v0.3.1]
### Changed
- No longer publishes empty result files (BAM, VCF, consensus FASTA) for samples which do not have any reads left after pre-processing and filtering.
- Now uses Medaka v1.8.2. Options for `basecaller_cfg` were updated accordingly. The default now is `dna_r10.4.1_e8.2_400bps_sup@v4.2.0`.
- The per-sample summary table in the report no longer shows sample metadata columns unless metadata was provided by the user via a sample sheet.

## [v0.3.0]
### Changed
- VCF files now use the sample alias as sample name instead of `SAMPLE`.
- The reference FASTA file with sanitized sequence headers (with `:`, `*`, and whitespace replaced with `_`) which is used by the workflow internally due to some tools not tolerating these symbols in the sequence IDs is now also published alongside the other results.

### Added
- Parameter `--combine_results` to also output merged BAM and VCF files.

## [v0.2.3]
### Fixed
- The workflow now prints a warning when there are no reads after filtering / preprocessing and produces a truncated report showing only the pre-processing stats table.

## [v0.2.2]
### Fixed
- Bug where the `mosdepth` process would fail if the length of a reference sequence was smaller than the number of depth windows requested.

## [v0.2.1]
### Changed
- GitHub issue templates
- Example command to use demo data.

## [v0.2.0]
### Changed
- Instead of dropping variants with `DP < min_coverage`, set their `FILTER` column to `LOW_DEPTH` in the results VCF.
- Bumped minimum required Nextflow version to 22.10.8.
- Enum choices are enumerated in the `--help` output.
- Enum choices are enumerated as part of the error message when a user has selected an invalid choice.

### Fixed
- Replaced `--threads` option in `fastqingress.nf` with hardcoded values to remove warning about undefined `param.threads`.

## [v0.1.3]
### Added
- Consensus sequences and BAM files as output files.

## [v0.1.2]
### Added
- Configuration for running demo data in AWS.
- Tags for `epi2melabs` desktop app.

## [v0.1.1]
### Fixed
- Reference not being required by the schema.
- Bug in documentation that prevented blog post from building.

## [v0.1.0]
* First release.

