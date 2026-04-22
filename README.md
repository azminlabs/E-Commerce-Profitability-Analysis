# 📦 E-Commerce Profitability Analysis

> **Data Analyst Portfolio — Muh. Azmin**  
> `Advanced Excel` · `Power Query` · `Solver Optimization` · `Pivot Table`  
> *April 2026*

---

## 📋 Table of Contents

1. [Project Overview](#-project-overview)
2. [Data Preparation](#-data-preparation)
3. [Data Insights](#-data-insights)
4. [Summary](#-summary)

---

## 🔍 Project Overview

### Business Problem
The company generated **$1M+ in Gross Revenue** over the last two years, yet profit margins have been **consistently shrinking**.

### Goals
- Identify product categories that **drive** and **drag** profitability
- Determine the most **efficient sales channel**
- Understand the impact of **product returns** on revenue
- Identify marketing platforms with the best **Return on Ad Spend (ROAS)**
- Build a marketing budget reduction recommendation to **minimize revenue impact**

### Dataset

| File | Description |
|------|-------------|
| `orders.csv` | Transaction-level order data |
| `products.csv` | Product details including cost and category |
| `marketing_spend.csv` | Monthly spend per marketing platform |

---

## 🛠️ Data Preparation

### Excel Tools Used

| Category | Tools |
|----------|-------|
| Data Pipeline | Power Query |
| Visualization | Pivot Table & Pivot Chart |
| Optimization | Solver |
| Formatting | Conditional Formatting |
| Calculation | Formula & Functions |
| Statistics | Data Analysis Toolpak (Histogram) |
| Transformation | Calculated Columns, Data Aggregation/Groupby |

### ETL Process

**Extract** — Loaded all raw datasets into Power Query

**Transform** — Applied data cleaning, formatting, merging, and aggregation

**Load** — Loaded a total of **15 queries** for downstream analysis

| Query Group | Queries |
|-------------|---------|
| Raw Data | `orders`, `products`, `marketing_spend` |
| Category Analysis | `total_revenue`, `total_costs`, `total_profit`, `profit_margin`, `products_analysis` |
| Channel Analysis | `aov`, `average_profit`, `return_rate` |
| Platform Analysis | `average_roas`, `average_cpa`, `average_cpc`, `marketing_analysis` |

---

## 📊 Data Insights

### 1. Electronics Leads Profitability, While Books Is Dragged Down by Shipping Cost

The company's average profit margin is **22%**. **Electronics (31%)** is the top performer, while **Books (12%)** falls far below the company standard.

![Profit Margin by Category](/image/profit_margin_by_category.jpg)
*Profit margin per product category — Books (12%) is the most critical point*

![Correlation Heatmap](/image/correlation_heatmap.jpg)
*Correlation heatmap — shipping cost has a near-perfect negative correlation with margin (−0.98)* |

| Variable | Correlation with Margin |
|----------|:-----------------------:|
| Shipping Cost | **−0.98** 🚨 |
| Product Cost | −0.59 |
| Discount | +0.19 |
| Returns | −0.07 |

> **Executive Insight:** 3 out of 8 categories (Books, Beauty, and Clothing) are below the company average. **Books (12%)** is identified as the most critical point — a deeper analysis of shipping cost is needed to bring profitability back to the average level.

---

### 2. Shipping Cost Policy Adjustment to Protect Margin

The shipping-to-selling-price ratio for Books reaches **0.58** — nearly **60% of a book's price** is consumed by logistics. With **55% of transactions below $60**, the free shipping policy is burning profit on the majority of Books orders.


![Shipping Cost Ratio](/image/shipping_cost_ratio.jpg)
*Shipping cost-to-price ratio per category — Books (0.58) is far above all others*

---
![Transaction Distribution Histogram](/image/transaction_histogram.jpg) 
*Transaction value distribution — 55% of total transactions fall below $60*

> **Executive Insight:** Implement a **Tiered Shipping Policy** — Free Shipping for orders > $60, 50% subsidy for $30–$60, and full cost for < $30. This protects margin while also encouraging customers to spend more (upselling).

---

### 3. Mobile App Efficiency Far Outperforms Marketplace Burdened by Platform Fees

**Mobile App** records the highest profit per order **(\$36.32)**, while **Marketplace** is the weakest channel **($15.40)** due to a $7,950 platform fee burden.

![Channel Profit Scatter](/image/channel_profit_scatter.jpg)
*Average profit vs. average order value per sales channel*

---
![Platform Fee Comparison](/image/platform_fee_comparison.jpg)
*Total platform fee per channel — Marketplace bears the highest cost at $7,950*


| Channel | Avg. Profit/Order | Platform Fee |
|---------|:-----------------:|:------------:|
| **Mobile App** | **$36.32** | $0 |
| Website | ~$32 | $0 |
| Social Commerce | ~$19 | $1,945 |
| **Marketplace** | **$15.40** | **$7,950** |

> **Executive Insight:** Encouraging customer migration to **Mobile App** is a strategic move to increase profitability without raising product prices.

---

### 4. High Return Rate Causes $20.6K in Lost Revenue

Return rates vary significantly across channels, with the critical point at **Social Commerce — Books category (18.30%)** and the best efficiency at **Sports category (0.40%)**.

![Return Rate Heatmap](/image/return_rate_heatmap.jpg)
*Return rate heatmap by category and channel — red cells indicate critical points*

---
![Return Revenue Waterfall](/image/return_revenue_waterfall.jpg) 

*Revenue impact of returns: $20.6K lost revenue → $13.6K net loss* |

> **Executive Insight:** Focusing on **Quality Control** and customer expectation alignment in the **Books** category will protect the company's potential profit next year.

---

### 5. Separating Profitable Platforms from Money-Burning Ones

**TikTok Ads (avg. 24.4x)** and **Influencer (23.4x)** consistently lead in ROAS. Monthly analysis reveals **budget wastage on Email Marketing**, especially in **June, October through December**.

![ROAS by Platform](/image/roas_by_platform.jpg)

*Average ROAS per marketing platform — TikTok Ads leads at 24.4x*

---
![ROAS Monthly Heatmap](/image/roas_monthly_heatmap.jpg) 
*Monthly ROAS heatmap — red cells (< 4.5x) indicate Loss Zone months* |

| Platform | Avg. ROAS | Zone |
|----------|:---------:|:----:|
| **TikTok Ads** | **24.4x** | ⭐ Star Zone |
| **Influencer** | **23.4x** | ⭐ Star Zone |
| Instagram Ads | 17.0x | ✅ Safe Zone |
| Google Ads | 13.7x | ✅ Safe Zone |
| Facebook Ads | 11.3x | ✅ Safe Zone |
| **Email Marketing** | **5.4x** | ⚠️ Borderline |

> ROAS threshold: **4.5x** — below this = Loss Zone

> **Executive Insight:** Platforms with ROAS below 4.5 must be cut and reallocated to higher-ROAS platforms to maximize profit.

---

### 6. Protect & Trim Strategy to Achieve 20% Marketing Budget Efficiency

**'Protect & Trim'** — maintain full budget on profitable platforms and cut underperforming ones.

![Protect & Trim Table](/image/protect_trim_table.jpg)
*Optimized budget allocation per platform per month — 20% cut achieved*

---
> **Methodology:** Excel Solver | **Objective:** Maximize Revenue | **Constraint:** Total Budget ≤ 80% | **Algorithm:** GRG Nonlinear
![Solver Parameters](/image/solver_parameters.png)
*Excel Solver configuration: Maximize Revenue, Budget ≤ 80%, GRG Nonlinear*

> **Executive Insight:** This allocation strategy guarantees **20% cost efficiency** by focusing full budget on **TikTok Ads & Influencer** (ROAS > 4.5) and aggressively cutting **Email Marketing** down to 20% in low-ROAS months.

---

## ✅ Summary

| # | Finding | Recommendation |
|---|---------|----------------|
| 1 | **Electronics** is the top profit driver; **Books** is dragged down by inefficient logistics (shipping ratio: 0.58) | Tiered Shipping Policy for Books |
| 2 | **Mobile App** is the most efficient channel vs. **Marketplace** burdened by $7,950 platform fees | Drive customer migration to Mobile App |
| 3 | Revenue leakage of **$20.6K** due to high return rate — critical at Social Commerce Books (18.30%) | Quality Control & customer expectation alignment |
| 4 | **TikTok Ads & Influencer** deliver the best ROAS; **Email Marketing** is unproductive in 4 months | Cut Email Marketing budget in Loss Zone months |
| 5 | **20% marketing cost efficiency** is achievable using the Protect & Trim strategy | Implement Solver-optimized budget allocation |


---

## 👤 Contact

**Muh. Azmin**

[![Email](https://img.shields.io/badge/Email-azminmuh%40gmail.com-blue?style=flat&logo=gmail)](mailto:azminmuh@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-muh--azmin-blue?style=flat&logo=linkedin)](https://linkedin.com/in/muh-azmin-1b348a219)
