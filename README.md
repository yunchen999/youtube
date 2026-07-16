# YouTube Creator Analytics: Cross-Category Growth & Efficiency Analysis

Statistical analysis comparing subscriber growth efficiency across 75 top YouTube creators spanning three content categories, using the YouTube Data API, regression, and non-parametric hypothesis testing.

## Overview

Do some content categories convert video output into subscriber growth more efficiently than others? This project pulls public channel-level statistics for 75 top creators (25 each in **Education**, **Entertainment**, and **Science & Technology**), then tests whether video output predicts subscriber count and whether per-video subscriber efficiency differs meaningfully across categories.

## Data

- 75 channels, 25 per category, collected via the YouTube Data API v3
- Channel-level metrics: `subscriber_count`, `video_count`, `view_count`, plus derived `views_per_video` and `subs_per_video`

## Methodology & Results

1. **OLS regression** — `log(subscriber_count) ~ log(video_count)` → R² = 0.025. Upload volume alone explains almost none of the variation in subscriber count; growth is driven by factors other than sheer posting frequency.
2. **Kruskal-Wallis H-test** on `subs_per_video` across the three categories → H = 28.74, p < 0.001. A statistically significant difference in per-video subscriber efficiency between categories (chosen over one-way ANOVA since the metric is heavily right-skewed — e.g., MrBeast's 497M subscribers vs. a median creator in the low millions).
3. **Category summary** confirms the direction: Entertainment channels average ~44.5M subscribers and ~52,400 subs per video, Education averages ~29,000 subs per video, and Science & Technology trails at ~4,150 subs per video despite posting the most videos on average.
4. **Tableau dashboards** (`Tableau/`) visualize creator performance and the overall category landscape.

## Files

| File | Description |
|---|---|
| `frequency.ipynb` | Main analysis: data merge, OLS regression, Kruskal-Wallis test, category comparison |
| `*_seed_channels.csv` | Raw per-category channel pulls from the YouTube Data API |
| `youtube_creator_dashboard_channels.csv` | Combined 75-channel dataset with derived efficiency metrics |
| `youtube_creator_dashboard_category_summary.csv` | Category-level aggregated summary |
| `youtube_creator_dashboard_data.xlsx` | Dashboard-ready workbook |
| `Tableau/` | Tableau workbooks + dashboard screenshots |
| `YouTube_Creator_Analytics_1.pdf`, `youtube-presentation.pdf` | Written report and presentation deck |
| `matrix.png`, `video.png` | Supporting analysis visuals |

## Tech Stack

Python (pandas, statsmodels, scipy) · Tableau · YouTube Data API v3

## Notes

Analysis is based on a single snapshot of public YouTube channel statistics, not a longitudinal time series — results describe cross-sectional differences between categories at the time of data collection.
