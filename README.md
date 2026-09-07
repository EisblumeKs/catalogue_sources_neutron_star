# Spin and Thermal Constraints for 144 Rapidly Rotating Neutron Stars

**Zeyue Wu and Zhiwei Chen · Version 1.0.0**

Repository: [EisblumeKs/catalogue_sources_neutron_star](https://github.com/EisblumeKs/catalogue_sources_neutron_star)

This catalogue compiles spin frequencies and thermal constraints for 144 rapidly rotating neutron stars: 18 accreting transients and 126 rotation-powered millisecond pulsars. Eight sources have two-sided surface-temperature estimates, and 136 have temperature ceilings. The tables include the adopted observational inputs, reference core-temperature coordinates, and source-level bibliographic links.

The catalogue accompanies *Lower Bounds on Crust–Core Slippage from Multimessenger Equation of State Inference and 144 Rapidly Rotating Neutron Stars*. It contains the selected sample used in that study. For sources with two-sided thermal estimates, inclusion requires overlap with the stable side of the representative r-mode boundary at crust–core slippage S = 1. The assumption of r-mode stability belongs to the analysis; it is not an observed classification of these objects.

## Files

| File | Contents |
|---|---|
| [data/catalogue.csv](data/catalogue.csv) | One row per source, with spin, temperature, provenance, and qualifications |
| [data/source_references.csv](data/source_references.csv) | Separate references for each source's adopted spin and thermal input |
| [data/field_dictionary.csv](data/field_dictionary.csv) | Column definitions, data types, and units |
| [references.bib](references.bib) | Bibliographic records for the cited data and envelope models |
| [CITATION.cff](CITATION.cff) | Citation metadata for this dataset |
| [RIGHTS.md](RIGHTS.md) | Source attribution and reuse information |
| [SHA256SUMS](SHA256SUMS) | File checksums for this version |

The CSV files use UTF-8 encoding, comma delimiters, and a single header row. The `source_id` column numbers the sources consecutively from 1 to 144; `canonical_source_id` identifies each physical object independently of this numbering. Numerical values use a decimal point; empty fields denote unavailable or inapplicable entries, never zero. Retained numerical precision reflects the compilation and conversions, not necessarily the precision of the original measurements.

## Finding a source

Open [data/catalogue.csv](data/catalogue.csv) and locate the object by `source_name` or its catalogue number, `source_id`. For example, IGR J00291+5934 is source 1. The same number in [data/source_references.csv](data/source_references.csv) gives separate links to the adopted spin and thermal inputs. Column definitions and units are listed in [data/field_dictionary.csv](data/field_dictionary.csv). The CSV files can also be downloaded and filtered by source name or number.

## Reading the thermal constraints

All temperature columns are in kelvin and refer to temperatures measured by a distant observer. Surface and core temperatures occupy separate columns. The `temperature_constraint` field distinguishes a two-sided estimate from an upper limit. For an upper limit, the representative temperature and upper endpoint contain the same ceiling, and the lower endpoint is empty.

The `thermal_basis` field preserves the qualifications of the input compilation:

| Value | Meaning | Sources |
|---|---|---:|
| `strict` | Two-sided surface-temperature estimate adopted from the cited thermal analysis | 4 |
| `conditional` | Two-sided estimate conditional on a spectral or surface-emission interpretation | 4 |
| `upper_limit` | Temperature ceiling adopted from a source study or literature compilation | 13 |
| `flux_ceiling` | Temperature ceiling derived by assigning the available X-ray luminosity to uniform surface emission | 123 |

These categories describe the thermal information, not the statistical confidence level or r-mode stability. The `interval_description` and `notes` columns record the relevant qualifications. In particular, some intervals reflect systematic variations rather than a specified probability, and one literature temperature is adopted as a conservative ceiling without a formal confidence level.

For luminosity-derived ceilings, the available luminosity may include polar-cap, magnetospheric, or intrabinary-shock emission. Assigning it to the whole surface therefore provides a conservative thermal budget. Such entries are not temperature detections.

## Reference core temperatures

The `core_temperature_inf_*` columns retain the coordinates used to display the sample in the study's stability window. They are derived from the surface inputs using stellar structure and heat-blanketing envelope models, including Potekhin, Chabrier and Yakovlev (1997; `PCY1997`). They should be distinguished from direct observational constraints on the core temperature.

For two-sided estimates, the representative coordinate uses a partially accreted envelope with a light-element column depth of 10^9 g cm^-2. The displayed lower and upper endpoints combine the surface-temperature endpoints with fully accreted and iron envelopes, respectively, and the reference stellar-structure range. Upper-limit coordinates use an iron envelope. These displayed ranges do not all have the same confidence level.

The surface-temperature inputs, rather than a single fixed core-temperature conversion, are used in the study's calculations over the EoS and mass samples. Temperatures tightened by the representative S = 1 boundary are separate model results and do not replace the observational inputs in this catalogue.

## Data sources and citation

Each source has separate `spin_reference` and `thermal_reference` keys, resolved in [references.bib](references.bib). These may identify a source study or a published compilation. The bibliography of the cited compilation should be consulted for the underlying observations. Row-level URLs are also provided in [data/source_references.csv](data/source_references.csv).

For rotation-powered pulsars, the catalogue locators retain line numbers from the Xu et al. living-table snapshot dated 2025-12-25 (`XuLive2025`). These identify the snapshot used in compiling the sample, rather than a guarantee that line numbers in the current website remain unchanged. The principal published compilation is Xu et al. (2025; `Xu2025`); source-specific thermal studies supersede its luminosity-based estimates where indicated.

Please cite this dataset together with the original studies or compilations supplying the values used in your analysis. Citation metadata are provided in [CITATION.cff](CITATION.cff). A dataset DOI has not yet been assigned.

## Version history

**1.0.0:** Initial public-data files for the final 144-source sample, numbered consecutively from 1 to 144. Spin frequencies, distances, temperature values, and interval endpoints are retained without numerical changes. Field names and explanatory notes have been edited for clarity. Legacy plotting classifications and internal bookkeeping fields are omitted. Model-derived slippage distributions are outside the scope of this catalogue release.
