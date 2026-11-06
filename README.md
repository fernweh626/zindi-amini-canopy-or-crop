# Amini Canopy or Crop Challenge — Competition Design, Partner Engagement & Benchmark

> **My role:** Competitions Lead at [Zindi](https://zindi.world) (April 2019 – November 2025). I owned this competition as a product and was the partner manager for the Amini relationship, which I led across 5 challenges.
> **Competition page:** https://zindi.world/competitions/amini-canopy-or-crop-challenge
> **Data (not redistributed here):** https://zindi.world/competitions/amini-canopy-or-crop-challenge/data
> **Winning solution write-up (I supported the winners in writing and publishing it):** https://zindi.world/learn/winning-solution-to-amini-canopy-or-crop-challenge

## The problem
Classify what is growing on the ground from satellite imagery: a **multiclass land-cover classification** problem (`0` = forest, `1` = cocoa, `2` = palm). Each sample is a single pixel observed across multiple time periods. Reliable crop and canopy maps support agricultural planning and monitoring.

- **Partner:** Amini, an Earth Observation (EO) data company
- **Evaluation metric:** multiclass **F1 score**, chosen because the classes are imbalanced, so plain accuracy would reward predicting the majority class.

## Product thinking
**The tension.** Earth Observation is a steep step for most data scientists: it needs new data sources, formats and tooling. We wanted something that engaged the whole community without being out of reach, but that was still more than a toy. We needed something "in between".

**The decision.** Amini chose to optimise for **community engagement** rather than a production-ready solution they could implement inside their company. That changed how I shaped the challenge:
- A well-posed tabular framing, where each pixel's time series is aggregated into features, so participants don't need deep EO tooling to submit.
- A learning path alongside the competition: **3 webinars co-hosted with Amini** that built EO skills step by step.
- A participation incentive: attend all three webinars *and* make a leaderboard submission to qualify for a 30-minute mentorship call with an Amini or Zindi EO specialist (code help, industry and job-market insight, interview tips, networking).

**Webinar series** (recordings: [1](https://www.youtube.com/watch?v=A4gkYY1vVwQ), [2](https://www.youtube.com/watch?v=AsCex-fsPok), [3](https://www.youtube.com/watch?v=fqQAT9nmGMM)):
1. Where and how to source EO data? (13 Feb 2025)
2. Processing EO data for machine learning (27 Feb 2025)
3. Building your pipeline: from data to model outputs (13 Mar 2025)

**Trade-offs I managed**
- A benchmark credible enough to build on but with headroom left for participants.
- Accessibility (free-tier compute, a simple tabular framing) vs. the richness of raw EO data.
- Partner goals (community reach) vs. a solution the partner could deploy.

## My contribution
- **Partner management:** led the Amini engagement across 5 challenges and aligned on this challenge's objective of community engagement over an implementable solution.
- **Challenge design:** scoped the task, the data format (long format, one `ID` per pixel over time), and the F1 metric given the class imbalance.
- **Participant enablement:** wrote the starter notebook and a benchmark solution, and co-ran the 3-part webinar series with the partner.
- **Community & outcomes:** supported the winning team in writing up and publishing their solution so the learning is public.

## Approach (benchmark)
| Step | Decision | Why |
|---|---|---|
| Data shape | Long format: one row per pixel per time step | Mirrors how satellite time series arrive |
| Feature engineering | Aggregate each band per pixel: mean, std, min, max, median | Collapses the time series into a fixed-length tabular vector |
| Model | `LightGBM` classifier | Fast, strong on tabular data, runs on free-tier compute |
| Validation | 80/20 stratified split | Preserves the class imbalance in both folds |
| Metric | Multiclass F1 | Robust to imbalance |

The starter notebook deliberately leaves **Feature Engineering** and **Modelling** as open prompts (time-series features, ensembling, speed vs. accuracy) to teach rather than hand over a solution.

## Results & impact
- Winning scores reached a **perfect score**, which we anticipated for a well-posed tabular framing.
- **Most successful challenge of the Amini partnership.** The partnership report credits pairing it with the webinars, because it took participants along the whole process and led to deep understanding.
- **Webinar registrations:** 227 (webinar 1), 107 (webinar 2) and 76 (webinar 3).
- **Partnership-wide reach** (Feb 2024 – Jul 2025, across the 5 Amini challenges): 3,367 users, 113 countries (42 African), 15% women, 19,766 submissions, and an estimated 90,000+ hours of data-science work.

**Lessons from the partnership:** challenges paired with webinars drove the deepest engagement, and the webinar series was a hit, so webinars should accompany every challenge. The one data-collection challenge was hard to structure and had low uptake, which pushed us toward more traditional modelling challenges. Intermediate-difficulty challenges let beginners get started and also attracted the top users. Amini became a known name on Zindi for engaging challenges.

## Repo contents
```
notebooks/starter_notebook.ipynb      # participant-facing starter
notebooks/multiclass_benchmark.ipynb  # benchmark solution (LightGBM)
data/                                 # empty — download from Zindi (link above)
```
Outputs are stripped from the notebooks. To run: download the data into `data/`, `pip install -r requirements.txt`, open the notebooks.

## Attribution & licensing
Notebooks were written by me while at Zindi for the competition. The competition data is © its owners and governed by the Zindi competition rules; it is not included here.
