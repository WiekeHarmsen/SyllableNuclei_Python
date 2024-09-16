# SyllableNuclei_Python
In this repository, we explain how to use the SyllableNucleiV3 script from de Jong et al. (2021) to compute oral reading fluency features.



## Getting started

Download two scripts (syllable_nuclei_v3.praat and filled_pauses.praat) from the webpages below (or use the ones I copy-pasted in this repository).

https://sites.google.com/site/speechrate/
https://sites.google.com/view/uhm-o-meter

In Behavior Research Methods, an explanation of how the script works and a validation can be found:

De Jong, N.H. & Wempe, T. (2009). Praat script to detect syllable nuclei and measure speech rate automatically. Behavior research methods, 41 (2), 385 - 390. [link](https://drive.google.com/file/d/1kff5Zp_zekVed10Xb6ZAXNwOVccNqmh0/view)


Note that the new and slightly better version of this script (v3) can be found here: https://sites.google.com/view/uhm-o-meter. This version includes an option to count filled pauses (uhm's). The algorithm and validation can be found here:

De Jong, N.H., Pacilly, J., & Heeren, W. (2021). PRAAT scripts to measure speed fluency and breakdown fluency in speech automatically, Assessment in Education: Principles, Policy & Practice, 28:4, 456-476, DOI: 10.1080/0969594X.2021.1951162 

## Run SyllableNucleiv3.praat from Python

See script `run_syllable_nuclei_v3_python.ipynb`

For the output, there are four options:
- TextGrid(s) only
- Praat Info window
- Save as text file
- Table

| Output option | Description|
|---|---|
| TextGrid(s) only | Creates in the `input_dir` one file for each audio file: a `.auto.TextGrid` file. |
| Praat Info window | Print file-level fluency measures in the console. |
| Save as text file | Creates in the `input_dir` one file for each audio file: a `.auto.TextGrid` file.  |
| Table | Creates in the `input_dir` two files for each audio file: a `.auto.Table` file and a `.auto.TextGrid` file. |

Explanations of the output files

`.auto.TextGrid`
Three tiers:

| Tier name | Description |
|---|---|
| PointTier "Nuclei" | The detected syllable nuclei |
| IntervalTier "Phrases" | Each interval is one phrase, dependent on the input variable `minimum pause duration` |
| IntervalTier "DFauto (Dutch)" | Intervals with filled pauses (they are not correct for child speech), one interval for each syllable nuclei ( + intervals in between) |

`.auto.Table`
This table contains the following acoustic features of each Syllable Nucleus:
type	ts	dur	durz	F0	F0z	F1	F1z	F2	F2z	F3	F3z	dF0	dF0z	dF1	dF1z	dF2	dF2z	dF3	dF3z	dqF0	dqF0z	dqF1	dqF1z	dqF2	dqF2z	dqF3	dqF3z	sdF0	sdF0z	sdF1	sdF1z	sdF2	sdF2z	sdF3	sdF3z	score

`File-level fluency measures (in console)`

| name |  nsyll |  npause |  dur(s) |  phonationtime(s) |  speechrate(nsyll/dur) |  articulation_rate(nsyll/phonationtime) |  ASD(speakingtime/nsyll) |  nrFP |  tFP(s) | 
| --- |  --- |  --- |  --- |  --- |  --- |  --- |  --- |  --- |  --- | 
| fn000049_first3sent |  24 |  3 |  10.00 |  7.84 |  2.40 |  3.06 |  0.327 |  8 |  1.386 | 
| fn000051_first3sent |  41 |  10 |  53.00 |  13.23 |  0.77 |  3.10 |  0.323 |  6 |  1.00 | 

