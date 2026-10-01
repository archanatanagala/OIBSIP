# TASK 4: Unveiling the Android App Market (Google Play Store)

## Objective

To perform a comprehensive Exploratory Data Analysis (EDA) on the Google Play Store ecosystem by exploring app categories, ratings, sizes, installs, pricing trends, and user reviews to provide data-driven insights for app developers.

## Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Datasets Used

- `googleplaystore.csv` — Google Play Store app data
- `googleplaystore_user_reviews.csv` — Google Play Store user reviews

## Analysis Performed

- Loaded and inspected the datasets.
- Cleaned and prepared the data for analysis.
- Analyzed app categories and distributions.
- Analyzed app ratings.
- Examined app sizes and installation trends.
- Analyzed free and paid applications.
- Examined app pricing.
- Analyzed user reviews and sentiment-related information.
- Created visualizations to identify important patterns and trends.

## Visualizations

The project includes charts and visualizations to understand:

- App category distribution
- Ratings distribution
- Installation trends
- App size patterns
- Pricing patterns
- User review analysis

## Project Files

- `T ARCHANA_TASK4.ipynb` — Jupyter Notebook containing the complete analysis.
- `googleplaystore.csv` — Google Play Store dataset.
- `googleplaystore_user_reviews.csv` — User reviews dataset.
- `screenshots/` — Project screenshots and outputs.

  ### Key Insights
1. Top categories with highest number of apps are Family, Game, and Tools, but Games have the highest installs overall.
2. Apps with higher number of reviews and 4.5+ rating have 3x more installs - strong correlation between Rating and Installs.
3. 92% of apps are Free, and Free apps have significantly higher installs than Paid apps. Paid apps average price is $3.2.
4. App size and Android version have no major impact on installs, but apps updated recently (last 6 months) have higher ratings.
5. Content Rating: Everyone and Teen categories dominate the store, while Ad-supported and In-app purchases increase installs but slightly lower average rating.

### Business Recommendation 
Focus on Free-to-Play model with In-app purchases in Game and Family categories for maximum reach. Maintaining 4.5+ rating and regular updates (every 3-6 months) is critical for visibility and user trust on Play Store.

## Conclusion

This analysis provides an overview of the Google Play Store app market and helps understand patterns related to app categories, ratings, installations, pricing, and user reviews.
