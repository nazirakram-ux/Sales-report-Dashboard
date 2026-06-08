# Sales-report-Dashboard
Project Title: Global Dining Insights & Operational Performance Optimization

Short Description
An enterprise-grade business intelligence solution developed to decode Zomato's multinational footprint. By auditing operational metrics, consumer engagement, and localized service features across 15 countries from the Clean Zamoto Data.csv file, this project transforms raw restaurant metadata into actionable commercial strategies, specifically highlighting how table booking and delivery services drive premium customer engagement.

Key Business Questions Answered
Q1: How does the adoption of digital convenience features (Online Delivery vs. Table Booking) affect restaurant performance and user engagement?

Q2: How can management isolate true quality ratings without letting unrated locations skew global benchmarks?

Q3: What is our culinary portfolio distribution, and where are the market penetration opportunities?

Q4: How are pricing tiers distributed across different international hubs, and do higher prices correlate with better customer satisfaction?

Dashboard Features & Highlights
Normalized Data Governance: Implements structural alerts regarding cross-currency contamination in global metrics.

True Quality Filtering: Intelligently isolates unrated entries to prevent standard deviation and mean reporting distortion.

Feature Matrix Impact Analysis: Quantifies the commercial value of feature adoption to justify vendor-side subscription push models.

Scannable C-Suite Layouts: High-level scorecard KPIs paired with deep-dive breakdown matrices optimized for swift executive decision-making.

DAX Measures Library
1. Total Restaurants (Platform Scale)
Visualization Used: KPI Card

DAX Code:

Code snippet
Total Restaurants = COUNTROWS('Clean Zamoto Data')

#### 2. Geographic Market Footprint
* *Visualization Used:* **KPI Card / Multi-Row Card**
* *DAX Code:*
  ```dax
  Total Countries = DISTINCTCOUNT('Clean Zamoto Data'[Country])
Code snippet
Total Cities = DISTINCTCOUNT('Clean Zamoto Data'[City])
3. True Average Rating (Excluding "Not Rated" Zeros)
Visualization Used: Gauge Chart or KPI Card

DAX Code:

Code snippet
True Average Rating = 
CALCULATE(
    AVERAGE('Clean Zamoto Data'[Aggregate rating]), 
    'Clean Zamoto Data'[Aggregate rating] > 0
)

#### 4. Total Votes (User Engagement)
* *Visualization Used:* **KPI Card**
* *DAX Code:*
  ```dax
  Total Votes = SUM('Clean Zamoto Data'[Votes])
5. Top-Tier Supply Count
Visualization Used: KPI Card

DAX Code:

Code snippet
Top Tier Restaurants = 
CALCULATE(
    COUNTROWS('Clean Zamoto Data'), 
    'Clean Zamoto Data'[Rating text] IN {"Excellent", "Very Good"}
)

#### 6. Share of Top-Tier Restaurants
* *Visualization Used:* **Gauge Chart**
* *DAX Code:*
  ```dax
  % Top Tier Restaurants = DIVIDE([Top Tier Restaurants], [Total Restaurants], 0)
7. Online Delivery Penetration Rate
Visualization Used: Donut Chart / KPI Card

DAX Code:

Code snippet
Online Delivery % = 
DIVIDE(
    CALCULATE(COUNTROWS('Clean Zamoto Data'), 'Clean Zamoto Data'[Has Online delivery] = "Yes"), 
    [Total Restaurants], 
    0
)

#### 8. Table Booking Adoption Rate
* *Visualization Used:* **Donut Chart / KPI Card**
* *DAX Code:*
  ```dax
  Table Booking % = 
  DIVIDE(
      CALCULATE(COUNTROWS('Clean Zamoto Data'), 'Clean Zamoto Data'[Has Table booking] = "Yes"), 
      [Total Restaurants], 
      0
  )
9. Engagement Density Per Unit
Visualization Used: Card Metric

DAX Code:

Code snippet
Avg Votes per Restaurant = DIVIDE([Total Votes], [Total Restaurants], 0)

---

### Visualizations Map & System Architecture

| Visualization Title
| Native Visualization Used
| Key Fields / Slicers Mapped
| Executive Management Purpose |
| :--- | :--- | :--- | :--- |
| **Global Expansion Blueprint** |
Bubble Map / Filled Map
| **Location:** `Country`<br>**Bubble Size:** `[Total Restaurants]` 
| High-level geographical representation of global operations and scaling efforts.  
| Donut Chart 

Screenshort :- https://github.com/nazirakram-ux/Sales-report-Dashboard/blob/main/sales%20image.png
