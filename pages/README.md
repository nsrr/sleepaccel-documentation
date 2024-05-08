## About

There are a number of consumer wearable devices purporting to track sleep on the market; however, the algorithms used to score sleep in these devices are rarely disclosed. On top of that, the raw sensor data from the devices are not usually available for use outside the manufacturer. This limits the usefulness of these devices in research and the clinic. We wrote an app to extract heart rate and accelerometer data from the Apple Watch. We collected data via the Apple Watch using this app from people undergoing polysomnography, as well as in the week leading up to the sleep lab recording. We then looked at the contributions of motion, heart rate, and a proxy for the circadian clock to the ability of classifiers to score sleep.

This project contains acceleration (in units of *g*) and heart rate (bpm, measured from photoplethysmography) recorded from the Apple Watch, as well as labeled sleep scored from gold-standard polysomnography. Data were collected at the University of Michigan from June 2017 to March 2019, and there are 31 subjects in total. Code to read and process these files is available on GitHub. The paper corresponding to the work is [Walch et al., "Sleep stage prediction with raw acceleration and photoplethysmography heart rate data derived from a consumer wearable device", SLEEP (2019)](https://pubmed.ncbi.nlm.nih.gov/31579900/).

## Methods

Subjects in this trial wore an Apple Watch to collect their ambulatory activity patterns for a week before spending one night in a sleep lab. During that night, acceleration (in *g*) and heart rate (in beats per minute, bpm) were collected from the Apple Watch while they underwent polysomnography. Each type of data recorded from the Apple Watch and the labeled sleep from polysomnography is saved in a separate file, tagged with a random subject identifier. 

For a full description of the methods, see [Walch et al. 2019](https://pubmed.ncbi.nlm.nih.gov/31579900/). To summarize, we recruited 39 subjects from the University of Michigan after approval by the University of Michigan Institutional Review Board. Subjects wore an Apple Watch for 7 - 14 days to collect their ambulatory steps. On the last day, they spent the night in the lab for an eight hour sleep opportunity, and we recorded acceleration and heart rate from their Apple Watch while they slept. Sample code to access these sensors on the Apple Watch is available here: https://github.com/ojwalch/sleep_accel. We excluded four people for errors with data transmission, three people for sleep apnea, and one person for REM sleep behavior disorder. In cases where the Watch ran out of battery in the middle of the night, data was cropped only to the window where valid collection occurred.

## Data de-identification

The data was deidentified in two ways: 

- First, all subject IDs used during the trial were replaced with a random integer 
- Next, specific times/dates were removed from the files by adjusting all times to be relative to the start of the PSG signal (0 = PSG start; all other times = seconds since PSG start)

## Data overview

**Download the full SleepAccel archive: [motion-and-heart-rate-from-a-wrist-worn-wearable-and-labeled-sleep-from-polysomnography-1.0.0.zip (563 MB)](#)**

The following types of data are provided: 

- motion (acceleration): Recorded from the Apple Watch and saved as txt files with the naming convention '[subject-id-number]_acceleration.txt'
	- Each line in this file has the format: *date (in seconds since PSG start), x acceleration (in g), y acceleration, z acceleration*<br><br>
- heart rate (bpm): Recorded from the Apple Watch and saved as txt files with the naming convention '[subject-id-number]_heartrate.txt'
	- Each line in this file has the format: *date (in seconds since PSG start), heart rate (bpm)*<br><br>
- steps (count): Recorded from the Apple Watch and saved in the format '[subject-id-number]_steps.txt'
	- Each line in this file has the format: *date (in seconds since PSG start), steps (total in bin from this timestamp to next timestamp)*<br><br>
- labeled sleep: Recorded from polysomnography and saved in the format '[subject-id-number]_labeled_sleep.txt'
	- Each line in this file has the format: *date (in seconds since PSG start) stage (0-5, wake = 0, N1 = 1, N2 = 2, N3 = 3, REM = 5)*

## Access and usage restrictions

The SleepAccel dataset is open access. There are no access and usage restrictions.

## Citation and acknowledgement

When using this dataset, users must cite the following:

> [Zhang GQ, Cui L, Mueller R, Tao S, Kim M, Rueschman M, Mariani S, Mobley D, Redline S. The National Sleep Research Resource: towards a sleep data commons. J Am Med Inform Assoc. 2018 Oct 1;25(10):1351-1358. doi: 10.1093/jamia/ocy064. PMID: 29860441; PMCID: PMC6188513.](https://pubmed.ncbi.nlm.nih.gov/29860441/)
> 
> [Walch O, Huang Y, Forger D, Goldstein C. Sleep stage prediction with raw acceleration and photoplethysmography heart rate data derived from a consumer wearable device. Sleep. 2019 Dec 24;42(12):zsz180. doi: 10.1093/sleep/zsz180. PMID: 31579900; PMCID: PMC6930135.](https://pubmed.ncbi.nlm.nih.gov/31579900/)

Users must include the following text in any Acknowledgements:

> The National Sleep Research Resource was supported by the U.S. National Institutes of Health, National Heart Lung and Blood Institute (R24 HL114473, 75N92019R002).

## Changelog

*May 2024*

- Make SleepAccel dataset available for data requests

## References

- SleepAccel full archive download (.zip, 563 MB): [motion-and-heart-rate-from-a-wrist-worn-wearable-and-labeled-sleep-from-polysomnography-1.0.0.zip](#)
- Motion and heart rate from a wrist-worn wearable and labeled sleep from polysomnography: https://physionet.org/content/sleep-accel/
- SleepAccel GitHub Documentation: https://github.com/nsrr/sleepaccel-documentation

## Acknowledgements

This work was supported by the Exercise & Sport Science Initiative University of Michigan; Mobile sleep and circadian rhythm assessment for enhanced athletic performance (U056400) M-Cubed; Analyzing light, human sleep and circadian rhythms through smartphones (U049702), and NSF DMS 1714094. Thanks to Mallory Newsted, Jennifer Zollars, and the University of Michigan Sleep and Circadian Research Laboratory for their assistance.

## Usage notes

Python code to process the data is available on http://www.github.com/ojwalch/sleep_classifiers/. The paper describing this work is available open-access here.

We encourage others to validate our work and build on it by applying novel analytical methods. In particular, our methods treat each epoch of sleep in isolation, which yields "blips" of sleep, wake, REM, and NREM. The global structure of sleep is not well captured by this approach. Alternative approaches that cluster nearby epochs or incorporate the probability of sleep stage transitions would be great directions for new work. 

Additionally, our work looked only at Wake vs Sleep and Wake/NREM/REM sleep. We encourage others to look at more four or five class classification; e.g. Wake/N1/N2/N3/REM, or Wake/N1+N2/N3/REM. 

## Conflicts of interest

Dr. Walch has given talks at Unilever events and received honorariums/travel expenses. She is the CEO of Arcascope, a company that makes circadian rhythms software. Arcascope did not sponsor this research. Dr. Goldstein receives royalties from UpToDate.

## Unshared data

Demographics data for the individual participants will not be shared in order to further ensure de-identification. 

## Questions?

Please reach out to us at support@sleepdata.org or in the [Forum](https://sleepdata.org/forum) if you have questions.
