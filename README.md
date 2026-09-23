# Spotify Data Analysis

An analysis of my personal Spotify listening habits from March 2020 to July 2026.

Based on a dataset of nearly 90,000 streaming records (filtered down from around 170,000 raw entries), this project explores the evolution of my music taste over the past ~ 6.5 years. It investigates if and how major life events, such as moving to a new country or switching to a new field of study from Humanities to Data Science, influenced my daily routines and listening behaviour.

---

## Table of Contents
1. [Data Cleaning & Pipeline](#data-cleaning--pipeline)
2. [Data Limitations](#data-limitations)
3. [Exploratory Data Analysis (EDA) & Findings](#exploratory-data-analysis-eda--findings)
   - [Q1: Devices Used for Listening](#q1-which-device-do-i-use-to-listen-to-music)
   - [Q2: Long-Term Streaming Volume Development](#q2-how-has-my-listening-volume-developed-in-the-past-65-years)
   - [Q3: Major Life Events & Shift in Routines](#q3-do-major-life-events-correlate-with-changes-in-listening-habits)
   - [Q4: Academic Cycles, Study Sessions & Seasonal Patterns](#q4-can-study-sessions-and-exam-phases-be-identified-in-the-data)
4. [Acknowledgements](#acknowledgements)
5. [License & Credits](#license--credits)


---

## Data Cleaning & Pipeline

Spotify provided raw streaming history split across multiple JSON files per year. To prepare the dataset for exploratory data analysis:

* **Merging Files:** Combined all annual JSON files into a unified master dataset.
* **Non-Music Filtering:** Excluded podcasts and audiobooks to focus purely on musical listening habits.
* **Duration Threshold (< 30 Seconds):** Filtered out entries played for less than 30,000 ms (30 seconds) to eliminate accidental clicks and skips. Playtimes were converted into minutes which reduced the total entries from **170,510 to 89,041 valid records**.
* **Missing Values:** Rows missing artist, track, or album names (likely removed from Spotify’s active catalog) were addressed and removed.
* **Duplicate Removal:** Removed 6,444 identical entries caused by overlapping annual file exports (frequently occurring during December).
* **Exclusion (2018 & 2019):** Excluded 2018 and 2019 from primary visualizations due to sparse data prior to adopting a Spotify Premium subscription.

---

## Data Limitations

* **Platform Anonymization:** Prior to October 2022, Spotify logged specific device names in the `platform` column. Afterwards, it transitioned to logging operating systems (e.g., `iOS`). As a result, distinguishing between iPads and iPhones is not possible in recent data, though macOS (`OSx`) remains distinct.
* **Track Length Outliers:** Individual tracks recorded continuous playback times of up to 40 minutes, indicating direct single-track repeat loops during intensive study sessions rather than long single files.

---

## Exploratory Data Analysis (EDA) & Findings

### Q1: Which device do I use to listen to music?

Device tracking reflects changing study environments. Desktop playback (macOS) clearly marks structured home-office, coding, and study environments, while mobile playback (`iOS`) dominates daily commutes.


### Q2: How has my listening volume developed in the past 6.5 years?

* **Spotify Premium Impact:** Acquiring a Spotify Premium subscription in September 2021 triggered a permanent increase in overall listening volume.
* *Fun Fact / Anecdote:* I was first introduced to Sleep Token when attending a sound festival with a university class. That evening, I listened to *"The Summoning"* and was initially unconvinced. Sleep Token has now been my **Top 1 Artist for three consecutive years**.


### Q3: Do major life events correlate with changes in listening habits?

#### Time-Series & Emotional Trends

* **Classic to Metal Transition:** Major life transitions, such as studying abroad, moving to Vienna, and switching from Humanities to Data Science, are clearly visible in time-series plots.
* **Fall 2023 (Study Abroad):** A measurable increase in Metal music served as a comforting constant during a demanding period marked by illness, grief, and stress abroad.
* **Late 2024 (Emotional Low):** A distinct drop in total streaming hours between November and December 2024 directly reflects a challenging emotional period.


#### All-Time Genre Correlation Heatmap

Analysis of the genre correlation matrix ($\text{vmin}=0, \text{vmax}=1$) showed exclusively non-negative values ($\ge 0.01$):
* **No Displacement Effects:** No single genre actively excluded or displaced another within the same month.
* **International Pop as a Anchor:** Pop acts as a consistent musical baseline, showing moderate to strong correlations with mainstream genres (Rock/Metal: $0.55$, RnB/Rap: $0.51$, K-Pop: $0.46$).
* **Rock/Metal & Pop Synergy:** Contrary to the assumption of isolated niche listening, Rock/Metal/Alternative correlates strongest with International Pop ($0.55$) and rarely coincides heavily with RnB/Rap ($0.21$).
* **Focus-Driven Niche Genres:** Classic/Cinematic and Jazz/Swing exhibit minimal correlation with other genres ($0.01$–$0.02$), functioning as dedicated background music for specific focus tasks.


#### Time-of-Day Routine Shifts

* **Earlier Daily Routine:** Relocating to Vienna for Data Science shifted listening activity significantly into the morning hours. Humanities lectures typically started around noon, whereas Data Science classes start early, requiring earlier morning commutes.
* **Peak Days:** Lecture days feature streaming peaks during early morning commutes, whereas non-lecture/study days show peak activity in the late morning and early evening.
* **Genre Distribution:** Rather than binding specific genres to fixed hours, listening across the day is fairly balanced. The main shift occurred across years: starting in 2022, Metal, Classic, and Jazz entered the distribution, superseding the earlier dominance of Pop.


### Q4: Can study sessions and exam phases be identified in the data, and how do genres shift across seasons?

#### Academic Cycles & Semester Plots

* **Exam Preparation Spikes:** Intensive study phases directly manifest as sharp increases in overall streaming volume due to multi-hour focus sessions.
* **Post-Exam Recovery:** Immediately following exam dates, streaming duration drops significantly, highlighting a recovery phase through the rest of the week.
* **Continuous Assessment Courses:** Subjects with ongoing weekly assignments display consistently high listening hours without major dips until final project deliveries.

---

## Acknowledgements

Built upon knowledge from university coursework and lessons. AI tools were used for debugging, syntax refactoring and code optimisation.

---

## License & Credits

Data provided by Spotify. Project created for personal portfolio analysis.
