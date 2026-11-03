# Amini Canopy or Crop Challenge — Competition Design & Benchmark

> **My role:** Competitions Lead at [Zindi](https://zindi.world) (April 2019 – November 2025) — I owned this competition as a product, from problem definition through launch, and built the starter notebook and benchmark solution that participants built from.
> **Competition page:** https://zindi.world/competitions/amini-canopy-or-crop-challenge
> **Data (not redistributed here):** https://zindi.world/competitions/amini-canopy-or-crop-challenge/data

## The problem
Classify what is growing on the ground from satellite imagery: a **multiclass crop / canopy classification** problem where each sample is a single pixel observed across multiple time periods. Reliable land-cover and crop maps feed agricultural planning, monitoring and food-security decisions.

- **Partner / sponsor:** TODO (e.g. Amini)
- **Intended users of the outcome:** TODO (who would use a model like this, and for what decision?)

## Product thinking
- **Users:** (1) data scientists on Zindi, mostly across Africa, ranging from first-timers to experts; (2) the partner who needs a usable model. TODO: confirm
- **Job to be done:** turn a real-world problem into a well-posed ML task that participants can start on in minutes and that produces a model the partner can use.
- **Success metrics:** participation and submission volume, score progression above the benchmark, solution quality for the partner. TODO: add actuals
- **Key trade-offs:** a benchmark strong enough to be credible but weak enough to leave headroom; free-tier compute vs model power; a raw-data realism vs a clean, learnable task.
- **Technical decisions I made or shaped:** data format and packaging, evaluation metric, validation split, benchmark model. TODO: confirm and add detail

## My contribution (product & delivery)
- Owned the competition lifecycle as product lead: scoping → data packaging → launch → community support → evaluation. TODO: edit to what you actually owned
- Designed the participant experience: a starter notebook that frames the data (each `ID` = one pixel over time), the target, and the open modelling questions, so first-time participants can submit quickly.
- Built a **benchmark solution** that sets a credible baseline without giving the whole game away.
- TODO: anything on metric choice, timeline, prizes, partner management, community engagement

## Approach (benchmark)
| Step | Decision | Why |
|---|---|---|
| Data shape | Long format: one row per pixel per time step | Mirrors how satellite time series arrive |
| Feature engineering | Aggregate each band per pixel: mean, std, min, max, median | Collapses the time series into a fixed-length tabular vector |
| Model | `LightGBM` classifier | Fast, strong on tabular data, runs on free-tier compute so it stays accessible |
| Validation | 80/20 stratified split | Preserves class balance |
| Metric | Weighted/multiclass **F1** | See notebook |

The starter notebook deliberately leaves **Feature Engineering** and **Modelling** as open prompts (time-series features, ensembling, speed vs accuracy) to teach rather than hand over a solution.

## Results & impact
- Participants: TODO
- Submissions: TODO
- Benchmark score → winning score: TODO
- Other outcomes (partner adoption, press, follow-ups): TODO

## Repo contents
```
notebooks/starter_notebook.ipynb      # participant-facing starter
notebooks/multiclass_benchmark.ipynb  # benchmark solution (LightGBM)
data/                                 # empty — download from Zindi (link above)
```
Outputs are stripped from the notebooks. To run: download the data into `data/`, `pip install -r requirements.txt`, open the notebooks.

## Attribution & licensing
Notebooks were written by me while at Zindi for the competition. The competition data is © its owners and governed by the Zindi competition rules; it is not included here.
