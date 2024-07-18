# E-Commerce Click-Through Rate (CTR) Analysis and Foreacst

# Introduction

This project focuses on a detailed time series analysis of the Click-Through Rate (CTR) for an e-commerce platform. By examining CTR data over various time periods, the aim is to uncover trends, seasonal patterns, and anomalies that can help in improving marketing strategies and enhancing user experience.

## Business Questions and Tasks

* **Trend and Time Series Analysis**
  * **Seasonal Trends:** Identify patterns over different times of the year (Year, Month) to understand high and low traffic periods.
  * **Time Series Forecasting:** Use models like ARIMA, SARIMA, or STDLR to predict future web traffic metrics.

## Data cleaning and preparatrion

After cleaning, preparing and understanding the data found the following notes

1) The dataset includes 1461 records.
2) No missing values.
3) Outliers detected in the **Clicks** column.
4) Outliers fixed with the **imputation** with the **median** value for each column.
5) New features were generated **Year, Month, Day and Weekday/Weekend**.
6) KPIs and Metrics calculated (**total_impressions, total_clicks and click_through_rate(CTR)**).
7) The dataset contains **8** features.

## Data Features

| Column | Count | Type |
| ------ | ----- | ---- |
| Date | 1461 | DATE |
| Impressions | 1461 | NUMBER |
| Clicks | 1461 | NUMBER |
| Year | 1461 | NUMBER |
| Month | 1461 | TEXT |
| Day | 1461 | TEXT |
| CTR | 1461 | PERCENTAGE |
| Weekday/Weekend | 1461 | TEXT |

## Conclusions
1) key performance indicators (KPIs):
    * total_impressions: 39,389,213 impressions.
    * total_clicks: 2,145,829 clicks.
    * click_through_rate: 5.45%.
    
2) By inspecting the characteristics of the data features we found the following:
    ![click_and_impressions_correlation](https://github.com/ahadel943/e-commerce_click_through_rate_ctr_analysis_and_forecast/blob/main/charts/1.click_and_impressions_correlation.jpg)
    * A moderate positive linear relation between **Clicks** and **Impressions** with a correlation coefficient of **0.68**.
    * No outliers were found in the CTR data series.
    * **CTR** data is almost normally ditributed the **average** is **5.45%** and the **median** is **5.50%**.
    * The minimum CTR value is **1.00%** and the maximum value is **10.00%**.
    * The overall standard deviation is **2.59%**.
    
3) After analyzing the CTR data by year the following insights were found:
    * From **2020** to **2021** there was a dip by **-1.55%** followed by a **0.35%** increase in **2022** then another slight increase in **2023** by **0.41%**.
    * **2020** has an average of **5.50%**.
    * **2021** has a average of **5.41%**.
    * **2022** has a average of **5.43%**.
    * **2023** has a average of **5.45%**.
    
4) Based on the monthly average CTR data from 2020 to 2023 here are some insights:
    * **High** CTR Months:
        * **2020**: **March** (5.86%), **June** (5.76%), **August** (6.29%), **October** (5.91%).
        * **2021**: **January** (5.66%), **April** (5.69%), **December** (5.74%).
        * **2022**: **April** (6.06%), **June** (6.04%), **September** (5.77%), **December** (5.86%).
        * **2023**: **June** (6.14%), **October** (5.91%), **December** (5.86%).
    * **Low** CTR Months:
        * **2020**: **April** (4.60%), **September** (4.90%), **November** (5.09%).
        * **2021**: **May** (5.17%), **October** (4.95%), **November** (4.95%).
        * **2022**: **May** (4.71%), **October** (4.81%).
        * **2023**: **January** (4.74%), **September** (4.98%).
    * **June** consistently shows high CTR across all years, which is also reflected in the highest S.I. (**1.08**). This indicates that **June** is a strong month for user engagement.
    * Other months like **April**, **August**, and **December** also show high performance in specific years but are not as consistently high as **June**.
    * **Low** performance in months like **April** **2020** (**4.60%**) and **May** **2022** (**4.71%**) suggests possible external factors affecting these months.
    
5) Based on the daily average CTR data from 2020 to 2023 the following insights were found:
    * **High** and **Low** CTR Days:
        * **2020**: Highest CTR on **Thursday** (6.14%), lowest on **Tuesday** (5.02%).
        * **2021**: Highest CTR on **Tuesday** (5.79%), lowest on **Sunday** (5.19%).
        * **2022**: Highest CTR on **Friday** (5.87%), lowest on **Tuesday** (5.00%).
        * **2023**: Highest CTR on **Tuesday** (6.07%), lowest on **Friday** (4.78%).
    * **Thursday** tends to have high CTRs consistently, peaking at **6.14%** in **2020** and maintaining above **5%** in other years.
    * **Tuesday** shows notable peaks in **2021** (**5.79%**) and **2023** (**6.07%**).
    * **Friday** generally shows lower CTRs, particularly in **2021** (**5.04%**) and **2023** (**4.78%**).
    * **Tuesday** in **2022** also has a relatively low CTR (**5.00%**).
    * **Thursday** (**1.032**), indicating the **best** performance relative to other days.
    * **Friday** (**0.953**), indicating consistently **lower** performance.

6) Based on the segmentation of our CTR data by weekdays and weekends, here are some insights:
    * **2020**: **Weekends** have a higher CTR than **weekdays** (5.61% vs. 5.45%).
    * **2021**: **Weekdays** have a slightly higher CTR than **weekends** (5.46% vs. 5.30%).
    * **2022**: **Weekdays** and **weekends** have almost the same CTR (5.44% vs. 5.40%).
    * **2023**: **Weekends** have a significantly higher CTR than **weekdays** (5.63% vs. 5.38%).
    * **2020** and **2023**: Weekends consistently show higher CTRs compared to **weekdays**, suggesting that users are more engaged during weekends in these years. This could be due to users having more free time to browse and engage with content.
    * In **2021**, **weekdays** performed better than **weekends**. This anomaly could be investigated to understand if there were specific campaigns, content, or external factors influencing user behavior during weekends in that year.
    * **2022** shows minimal difference between **weekdays** and **weekends**, indicating a balanced user engagement throughout the week.
    * The higher weekend CTR in 2023 (5.63%) suggests a strong opportunity to focus on weekend campaigns and promotions.
    
7) The following insights were uncovered during our CTR monthly forecast:
    * I used a Seasonal Trend Decomposition using Linear Regression (**STDLR**) model bioh approaches, **Multiplicative** and **Additive** models, The monthly data prefered the **Multiplicative** model (with a **MAPE** of **5.71%**) over the **Additive** model (with a **MAPE** of **19.54%**).
    * Given the lower **MAPE** of the **Multiplicative** model (**5.71%**), rely on these forecasts for planning and strategy development, The forecasted data for 2024 aligns well with historical trends, providing a reliable basis for decision-making.
    * The **forecasted** data follows the same pattern of the **seasonality indices**.
    * The month of **June** historically and forecasted as the **highest** engagement month.
    * **December**, With consistent **high** engagement due to holiday activities, prioritize holiday promotions, special offers, and festive content to drive clicks and engagement.
    * **May** and **November**, Since these months show **lower** CTR historically and forecasted consider enhancing user experience through personalized offers and interactive content.
    
## Recommendations
1) Based on the insights found from our Year-over-Year analysis we recommend the following:
    * Focus on improving user experience across all touchpoints, including the website, mobile app, and marketing communications. Enhanced user engagement typically leads to higher CTR.
    * Implement personalized marketing strategies to better target users based on their preferences and behavior.
    * Establish feedback loops with our audience to gather insights on what they find engaging. Use this feedback to tailor our content and marketing strategies.
    * Use real-time monitoring tools to track CTR and other key performance metrics, Quickly adapt strategies based on the data to address any issues or capitalize on positive trends.
    * Stay agile and be prepared to pivot strategies based on emerging trends and insights.

2) Based on the insights found from the monthly CTR analysis we recommend the following:
    * **June**: Given its consistently high CTR across all years and the highest Seasonality Index (S.I.), prioritize major campaigns, product launches, and promotional activities during June. This month presents a strong opportunity to capitalize on increased user engagement.
    * **April, August, December**: These months also show high performance in specific years, Tailor our content strategy to align with what historically works well during these months. Analyze past successful campaigns and replicate elements that resonate with our audience.
    * **April and May**: These months have shown lower CTRs in some years. Investigate external factors such as seasonal changes, holidays, or competitive pressures that may impact user behavior and adjust our strategies accordingly.
    * Consider adjusting the timing of campaigns or promotions to mitigate the impact of external factors. For instance, if May tends to be a lower-performing month, plan lighter campaigns or focus on different target segments.
    * Ensure our content remains relevant and valuable to our audience. Analyze trends and user feedback to stay updated with changing preferences and interests throughout the year.

3) Based on the insights found from our CTR analysis by day we recommend the following:
    * Thursday: Plan major campaigns, product launches, or promotional activities on Thursdays to leverage the consistently high CTR. This day shows strong engagement across all analyzed years.
    * Tuesday Peaks: In years like 2021 and 2023, capitalize on the notable peaks on Tuesdays (5.79% and 6.07% respectively). Allocate resources to strategic campaigns or special offers that resonate well on these days.
    * Analyze the types of content and messaging that performed well on high CTR days. Adapt our content strategy to align with user expectations and preferences on these days to maximize engagement.
    * Allocate a higher proportion of our advertising budget to days with historically high CTRs. This ensures maximum visibility and potential return on investment during peak engagement periods.
    * Consider lighter promotional activities or adjust campaign intensity on days with lower CTRs. This approach helps in maintaining visibility while focusing resources on more effective days.
    * Improve user experience and engagement tactics across all days. Implement personalized marketing strategies and user-centric campaigns that resonate with our audience's preferences and behaviors.

4) Based on the segmentation of our CTR data by weekdays and weekends, here are some actionable insights:
    * Maximize weekend campaigns by allocate resources and prioritize major campaigns, product launches, or promotional activities during weekends. Leverage the higher engagement levels to maximize visibility and impact.
    * Tailor content to align with weekend browsing habits and leisure time activities of our target audience. Highlight promotions and offers that are likely to resonate during weekends.
    * Introduce exclusive weekend offers or promotions to capitalize on higher user engagement during these periods.
    * Develop content that resonates with weekend browsing behaviors. Consider leisurely topics or content that aligns with weekend activities and interests of our target audience.
    * Schedule email sends, social media posts, and ad placements to peak times during weekends to maximize visibility and engagement. Use analytics to determine optimal timing for different demographics.
    * Develop weekday-specific content strategies that emphasize productivity, work-related themes, or solutions-oriented messaging and tailor our messaging to align with the mindset and needs of users during weekdays.
5) Here's how we can leverage the insights from our CTR forecast:
    * Plan and launch significant marketing campaigns during June and December. These months have historically shown high engagement, and our forecast supports this trend.
    * Consider running seasonal promotions, holiday sales, and exclusive offers to capitalize on the increased user activity.
    * Align our content calendar to include high-impact content, such as special announcements, product launches, and engaging multimedia content, during these high-engagement months.
    * Increase the frequency of content posting and advertising efforts during these periods to maximize visibility and engagement.
    * Use personalized marketing strategies to target users more effectively. Implement personalized email campaigns, recommendations, and offers based on user behavior and preferences.
    * Develop interactive content such as quizzes, polls, and user-generated content campaigns to increase engagement during the lower-performing months.

By effectively leveraging these insights, we can enhance our e-commerce business's overall performance, improve customer satisfaction, and drive sustained growth.
