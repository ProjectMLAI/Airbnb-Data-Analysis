# 🏨 Airbnb Data Analysis Project

## 📁 Dataset Overview

This project is based on two datasets:

* `listings.csv`: Contains information about listings such as `id`, `price`, `host_id`, `review_scores_rating`, etc.
* `reviews.csv`: Contains timestamps and listing references for user reviews.

---

## 📈 Task 1: Median Price Difference by Superhost

### Goal:

Identify neighbourhoods with the **highest median price difference** between superhosts and non-superhosts.

### Method:

* Cleaned `price` column to numeric.
* Grouped by `host_neighbourhood` and `host_is_superhost`, calculated median.
* Computed absolute differences and sorted to find maximum.

### Key Insight:

> Some neighbourhoods showed large price discrepancies, suggesting superhost status has a premium in certain areas.

---

## 📋 Task 2: Top Priced Neighbourhood

### Goal:

Find the **neighbourhood with the highest median price** overall.

### Method:

* Cleaned price data.
* Grouped by `host_neighbourhood`, calculated median.
* Sorted to find the highest.

### Key Insight:

> High-priced areas were often in central or historic locations.

---

## 📊 Task 3: Superhost Advantage in Top Reviewed Neighbourhoods

### Goal:

Among the top 5 neighbourhoods (by number of reviews), compare **average prices** between superhosts and non-superhosts.

### Method:

* Counted reviews per neighbourhood.
* Selected top 5 neighbourhoods.
* Grouped by `host_is_superhost` and calculated average price.

### Key Insight:

> Superhosts tend to charge more in high-traffic areas, though the difference varied by neighbourhood.

---

## ⏰ Task 4: Correlation Between Review Score and Price

### Goal:

Check correlation between `review_scores_rating` and `price` for listings with **at least 10 reviews**.

### Method:

* Counted number of reviews per listing using `reviews.csv`.
* Merged with `listings.csv` and filtered for listings with >=10 reviews.
* Ran `.corr()` between `price` and `review_scores_rating`.

### Result:

* Correlation = `+0.0935` (weak positive)

### Insight:

> High ratings are only slightly associated with higher price. Rating inflation may reduce its impact on pricing.

---

## 📊 Task 5: Most Frequently Reviewed Hosts

### Goal:

Identify hosts with the **shortest average time gap between reviews**.

### Method:

* Converted review dates to datetime.
* Merged listings with reviews to get `host_id` per review.
* Grouped by `host_id`, sorted by date, applied `.diff()` and averaged.

### Result:

* Top hosts had review gaps as low as 0–13 hours.

### Insight:

> These hosts are likely high-performing or running large-scale operations (e.g., multi-unit management).

---

## 🌍 Visual Analysis

### 🌐 Chart 1: Price vs Review Count (Colored by Rating)

![price\_vs\_reviews](./8dd333aa-79d1-4678-b6fd-6198865468f7.png)

**Insight:**

* Most listings with high review count are low to mid priced.
* High-rated listings are spread across all price tiers.
* High price doesn't guarantee high review volume.

---

### 🌐 Chart 2: Review Count vs Rating (Colored by Price)

![rating\_vs\_reviews](./c8aa87da-a111-4c0f-b2ed-447d489b9700.png)

**Insight:**

* Majority of listings cluster between 4.8–5.0 ratings.
* High-priced listings are sparse, mostly concentrated in high rating zones.
* Review score is not a strong predictor of review volume.

---

## 📄 Conclusion

This project explored how review metrics and superhost status relate to price and popularity in Airbnb listings. While **superhost status** and **location** influence price significantly, **review scores alone** show weak correlation with price. High review volumes are often tied to affordability and trust rather than luxury.

---

## 📢 Tools Used

* Python (Pandas, NumPy, Seaborn, Plotly)
* Jupyter Notebook / VS Code
* Airbnb Open Data

---

## 💪 Next Steps

* Build a price prediction model using review\_count, rating, and location.
* Analyze listing descriptions (NLP) to detect quality signals.
* Apply clustering to find listing archetypes.

---

> Designed for data science interview practice and real-world Airbnb analytics.
