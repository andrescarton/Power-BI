<h1 align="center">Sellers' Performance Dashboard</h1>

<p align="center">
  A Power BI dashboard that lets a sales manager see, in one screen, how every sales rep is doing.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Power_BI-F2C811?style=flat-square&logo=powerbi&logoColor=black" alt="Power BI">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white" alt="pandas">
  <img src="https://img.shields.io/badge/CatBoost-FFCC00?style=flat-square" alt="CatBoost">
</p>

<p align="center">
  <a href="Sellers'%20Performance/dashboard_walkthrough.mp4"><b>▶ Watch the walkthrough (1:26)</b></a> ·
  <a href="Sellers'%20Performance/Dashboard.pbix"><b>⬇ Download the .pbix</b></a> ·
  <a href="Sellers'%20Performance/sales_analysis.ipynb"><b>📓 Open the notebook</b></a>
</p>

![Sellers' Performance dashboard](Sellers'%20Performance/images/dashboard.png)

## The problem

The brief: a company selling lab products wanted its key sales metrics in one place. Sales were spread across many reps, product groups and customers, and a manager should be able to answer *who is selling the most, of what, and who is close to their target* from a single screen.

## What it answers

| Question | Where to look |
|---|---|
| How many products has each rep sold, by product group? | **Quantidade de Produtos** donut + rep cards on the left |
| How much money did that bring in? | **Valor Total** donut |
| How did that change month by month? | The two **Histórico** line charts |
| Is the rep on track for the target? | **Meta** gauge |
| Which customers buy the most? | **Quantidade de Produto por Empresa** treemap |
| Which products sell the most? | **Distribuição dos Produtos** bar chart |

Everything filters together: click a rep, or pick a year, month, product group or product at the top, and the whole page updates. Hovering over a customer shows a tooltip with a small map of where they are.

![Using the dashboard](Sellers'%20Performance/images/dashboard_demo.gif)

## How I built it

**1. Data preparation (Python).** The data came as two tables: 3,543 sales records with 29 columns, and a list of the reps. In the notebook I checked for missing values (seven columns were almost entirely empty, and only two records had gaps), looked for outliers with z-scores (55 records) and boxplots, and explored sales by group, rep and customer to decide what was worth putting on the dashboard.

| Products sold by group | Products sold by rep |
|---|---|
| ![](Sellers'%20Performance/images/products_by_group.png) | ![](Sellers'%20Performance/images/products_by_seller.png) |

**2. Dashboard (Power BI).** One page, built around the questions above: slicers at the top, a rep selector on the left, KPIs and trends in the middle, and the customer and product breakdowns at the bottom.

**3. Forecast (CatBoost).** As an extra, I trained a CatBoost regression to forecast future sales of each product per rep. The idea was to give the company a starting point for stock planning and for pushing the products with the highest ticket.

## Files

| File | What it is |
|---|---|
| [`Dashboard.pbix`](Sellers'%20Performance/Dashboard.pbix) | The Power BI report. Opens in the free [Power BI Desktop](https://www.microsoft.com/power-platform/products/power-bi/desktop) |
| [`dashboard_walkthrough.mp4`](Sellers'%20Performance/dashboard_walkthrough.mp4) | Screen recording of the dashboard in use |
| [`sales_analysis.ipynb`](Sellers'%20Performance/sales_analysis.ipynb) | Data cleaning, exploratory analysis and the CatBoost model |
| [`Project Performance.pptx`](Sellers'%20Performance/Project%20Performance.pptx) | The project presentation |

---

<sub>Course project. The data comes from the course material.</sub>
