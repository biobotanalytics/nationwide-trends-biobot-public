# Nationwide trends in COVID-19 cases and SARS-CoV-2 RNA wastewater concentrations in the United States

This repo contains the raw data underlying the results reported in Duvallet et al 2022.

For any questions, please open an issue in this repo (preferred) or email claire@biobot.io and hello@biobot.io.

## biobot_kits_quant_data_duvalletetal2022.csv

Data file containing kit-level results for each wastewater sample reported. This file can be used to reproduce the analyses and figures in the paper.

- Kit_ID: the unique ID representing a single wastewater sample collected on one day from one location
- sampling_date: sampling date for that sample. If composite, this is the sample collection (end) data. If grab, this is the 
- sampling_location: anonymized sampling location name.
- flow_mgd: flow provided by the sampling facility in millions of gallons per day. If flow on the day of sampling was provided, this field represents that value. Otherwise, we used a facility-reported average yearly flow.
- normalized_conc_copies_per_L: the normalized concentration in copies/L, calculated as the sarscov2_copies_per_mL_kit_raw / pmmv_copies_per_mL_kit_raw * reference_pmmv
- pmmv_copies_per_mL_kit_raw: raw PMMoV concentration, calculation as the average across all tubes for that kit
- sarscov2_copies_per_mL_kit_raw: raw SARS-CoV-2 sewage concentration, calculated as the average of N1 and N2 across all tubes analyzed for that kit
- lab_protocol_version: which lab protocol version was used to generate this kit's data. "mixed" means that the kit includes data from both methods (eg one tube was run with one method, and the other was run with the other)
- rolling_average_new_cases_centered: a centered 7-day rolling average of new cases, used in time series correlation analyses in the paper
- fig1_label: this location's subplot label in Figure 1 of the paper
- sampling_method: type of sample collected, as provided by the sampling facility.

## biobot_tubes_quant_data_duvalletetal2022.csv

Data file containing results for all individual samples and subsamples analyzed by qPCR.

- Kit_ID: the unique ID representing a single wastewater sample, and which can be used to connect the values in this file to the values in the kitwise data
- Tube_ID: the subsample analyzed for that kit. 
- file: an anonymized string indicating which qPCR batch this result comes from. The majority of samples were analyzed for all targets (N1, N2, and PMMV) in the same batch; some early samples were split across batches.
- lab_protocol_version: which lab protocol version was used to generate this data
- N1: the average wastewater concentration across all N1 replicates (copies/mL)
- N2: the average wastewater concentration across all N2 replicates (copies/mL),
- PMMV: wastewater concentration across all PMMoV replicates (copies/mL)
- sars-cov-2: the average of the N1 and N2 concentrations (copies/mL)
