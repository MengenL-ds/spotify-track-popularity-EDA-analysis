# spotify-track-popularity-EDA-analysis

## Overview
This project investigates how audio and contextual features influence the popularity of songs on Spotify.
The dataset was collated from Spotify’s API using two Python scripts to extract both popular and non-popular tracks, along with their associated audio (e.g., energy, danceability, valence) and descriptive features (e.g., artist, album, release date).

Through exploratory data analysis (EDA) and hypothesis testing, the project identifies which characteristics most strongly correlate with song popularity distinguishing between intrinsic musical properties and external contextual factors.

## Objectives
1. Assess data quality and feature completeness.
2. Explore the distribution and relationships of audio and contextual variables.
3. Conduct statistical hypothesis testing to evaluate which features significantly impact popularity.
4. Provide insights for modeling and forecasting track success on streaming platforms
   
## Dataset Source
Source: [Kaggle](https://www.kaggle.com/datasets/solomonameh/spotify-music-dataset?resource=download)
- Size: 1,686 tracks (balanced between popular and non-popular)
  - Features:
	- Audio: energy, danceability, valence, tempo, loudness,...
  - Descriptive: track_artist, track_album_name, playlist_genre, track_album_release_date,...
	- Target: track_popularity (numeric score, 0–100)

## Data Preparation
- Removed duplicate records by track_id.
- Handled missing values (only one missing album name).
- Standardized categorical fields and normalized text formatting.
- Converted data types (e.g: release_date → datetime).
- One-Hot/get_dummy Encoded categorical features such as playlist_genre and track_artist

## Exploratory Data Analysis (EDA)
1. Univariate Analysis
   - Histograms and boxplots reveal the distribution and outliers in energy, tempo, valence, and loudness.
2. Bivariate Analysis
  - Correlation matrices and pairplots highlight key relationships between audio features and popularity.
  - Popularity shows weak direct correlation with intrinsic audio features but notable dependence on genre and artist context.
3. Categorical Analysis
  - Boxplots and mean popularity comparisons demonstrate strong variation across genres and artists.
  - Some genres (e.g., Pop, Hip-hop) exhibit higher median popularity.

## Hypothesis Testing
| Hypothesis | Method | Result | Conclusion |
|-------------|---------|---------|-------------|
| **H1:** Pop vs. Hip-hop tracks have equal average popularity | Two-sample t-test | p < 0.05 | **Reject H_0** — Pop tracks significantly higher |
| **H2:** Higher energy levels correspond to higher popularity | Pearson correlation | p > 0.05 | **Fail to reject H_0** — No significant relationship |
| **H3:** Tracks by recognized artists achieve higher popularity | Two-sample t-test | p < 0.05 | **Reject H_0** — Artist recognition significantly impacts popularity |
**Key Insight**: Contextual attributes (e.g., genre, artist recognition) show stronger influence on popularity than intrinsic acoustic properties

## Conclusions
Genre and artist recognition are statistically significant predictors of track popularity.
- Audio energy and loudness are not strong individual determinants.
- Success on Spotify depends more on exposure and audience context than raw musical characteristics.
- These results will guide the next phase — predictive modeling using regression and ensemble techniques

## Tools Used
| Category           | Tools                                              |
|--------------------|----------------------------------------------------|
| **Data Extraction** | Spotify API, `spotipy`                             |
| **Analysis**        | Python (`pandas`, `numpy`, `scipy`, `seaborn`, `matplotlib`) |
| **Visualization**   | `matplotlib`, `seaborn`                            |
| **Notebook**        | Jupyter / VS Code                                 |
| **Export**          | `nbconvert`, LaTeX / Tectonic                     |

## Repository Structure
```
spotify-track-popularity-analysis-EDA
├── data/       
├── notebooks/         
└── README.md             
```

## Next Steps
- Develop predictive models (Regression, Gradient Boosting, Random Forest).
- Use feature importance and SHAP analysis for model interpretability.
- Extend dataset with streaming count and listener demographics.



