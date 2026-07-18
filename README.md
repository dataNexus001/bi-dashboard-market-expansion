# Business Intelligence Dashboard — Airport Passenger Traffic Analysis

An interactive Power BI dashboard built for a simulated business intelligence consultancy scenario, identifying the best airport locations for a luxury retail client's international expansion based on year-on-year passenger traffic data.

## Scenario

QDS Data Services (a fictional BI consultancy) was approached by a luxury fashion retailer looking to open its first airport boutique. As the analyst on the project, the brief was to determine:

1. Which **UK airport** is the strongest candidate for the client's first store, based on international/domestic passenger volumes.
2. Which **other international airport or country** represents the next-best expansion opportunity.

The analysis needed to account for both **year-on-year trends** and **within-year passenger volumes**, since raw trend direction alone can be misleading if overall traveller numbers shift.

## Tools & Technologies

- **Power BI Desktop** — dashboard build and visualisation
- **Power Query (M)** — data cleaning, transformation, and shaping (all performed inside Power BI before loading)
- **DAX** — calculated columns and measures for KPIs and trend comparisons
- **Data Modelling** — relationships across multiple passenger traffic tables
- **KPI Cards & Slicers** — interactive filtering by airport, country, and year

## Datasets

All data is UK/US government open data, supplied as part of the assignment brief:

| Dataset | Source | License |
|---|---|---|
| AVI0105 — International passenger movements at UK airports by country (2011–2021) | [gov.uk / DfT — TSGB02](https://www.gov.uk/government/statistical-data-sets/tsgb02) | Open Government Licence v3.0 |
| AVI0301 — Top 25 airports globally by international passengers (2019–2020) | [gov.uk / DfT — TSGB02](https://www.gov.uk/government/statistical-data-sets/tsgb02) | Open Government Licence v3.0 |
| San Francisco Air Traffic Passenger Statistics (2005–2022) | [data.sfgov.org](https://data.sfgov.org/Transportation/Air-Traffic-Passenger-Statistics/rkru-6vcg/data) | Open Data (SF Open Data Portal) |
| International Air Passenger Traffic Route Analysis, UK airports (May 2022) | [CAA UK Airport Data](https://www.caa.co.uk/data-and-analysis/uk-aviation-market/airports/uk-airportdata/uk-airport-data-2022/may-2022/) | Open Government Licence v3.0 |

No separate raw or cleaned data files are included in this repo — all cleaning and transformation was performed inside Power BI's Power Query editor and is embedded in the `.pbix` file itself. The `.pbix` can be opened in Power BI Desktop to inspect the full query steps.

## Process

1. **Data Import & Cleaning** — loaded all four datasets into Power Query; handled inconsistent date formats, removed irrelevant columns, standardised country/airport naming, and merged tables where needed.
2. **Data Modelling** — built relationships between the UK airport tables, the SF dataset, and the route analysis table to allow cross-filtering.
3. **DAX Measures** — created year-on-year % change measures, passenger volume KPIs, and ranking logic to compare airports/countries on a like-for-like basis.
4. **Dashboard Design** — built 4 report pages with KPI cards and slicers so a non-technical stakeholder (the client) could explore the data interactively.

## Dashboard Pages

**Screenshots:**

![Page 1 - UK Airport Overview](screenshots/Page%201%20(UK%20Airport%20Overview).png)
*Page 1 — UK Airport Overview: passenger trend line 2014–2024, Year/Region slicers, COVID Recovery Rate and Total PAX KPI cards.*

![Page 2 - UK Airport Comparison](screenshots/Page%202%20(UK%20Airport%20Comparison).png)
*Page 2 — UK Airport Comparison: bar chart of UK airports by international PAX (Heathrow predominant), Top Routes by Country, and Traffic Distribution by Region pie chart.*

![Page 3 - Global Airport Rankings](screenshots/Page%203%20(Global%20Airport%20Rankings).png)
*Page 3 — Global Airport Rankings: full Top 25 airports table (2022 vs 2023 PAX), Global Airport Growth chart comparing Dubai and Heathrow.*

![Page 4 - SFO Analysis](screenshots/Page%204%20(SFO%20Analysis).png)
*Page 4 — SFO Analysis: San Francisco international passenger trend 1999–2025, 2024 PAX by region donut chart, 2019 vs 2024 KPI cards.*

## Key Insights

- **Heathrow (LHR) is the clear recommendation for the client's first UK store.** It handled 4.99M international passengers in May 2022 — 76.5% more than second-place Gatwick (2.83M) — and has held volume leadership across the 2014–2024 AVI0105 trend data. Its route mix is also the most relevant commercially: the top individual country routes are the USA, UAE, and Germany, which are high luxury-spending source markets, and Western Europe accounts for 62.58% of all UK international traffic through Heathrow.

- **Dubai International (DXB) is the recommended next international expansion target.** It's the highest-volume international airport in the world (87.0M passengers in 2023, up +31.7% from 66.1M in 2022), already exceeding its pre-pandemic peak. Its passenger profile aligns with luxury retail spending — Dubai Duty Free alone generates over $2 billion annually — making it a stronger long-term case than a single-year snapshot would suggest.

- **A clear COVID-19 dip and recovery pattern is visible across all three datasets.** UK international passengers fell from 258.3M (2019) to just 50.6M (2021) before fully recovering to 258.5M by 2024. San Francisco's international traffic followed the same shape (15M → ~3M in 2020 → a new record of 16M in 2024). Some spikes, like Incheon's +212.9% "growth," reflect recovery from near-zero COVID closures rather than organic demand — a distinction the dashboard's conditional formatting was designed to make clear rather than mislead.

## Limitations

- **No luxury-spend data.** Passenger *volume* isn't the same as luxury-spending potential — a fully comprehensive analysis would weight airports by the share of passengers from high luxury-spending nationalities (USA, China, UAE, Saudi Arabia) and average duty-free spend, but this data isn't publicly available and would require direct airport operator or retail analytics partnerships.
- **No terminal-level granularity.** Knowing Heathrow is the right airport isn't enough — the client would also need to know the best terminal (e.g. Terminal 3's OneWorld/US-Middle East traffic vs Terminal 5's British Airways dwell time), which the CAA route dataset doesn't break down.
- **CAA route data is from May 2022** and is now dated relative to more recent route changes; a production analysis would refresh this with the latest CAA release.

## How to Run

1. Clone this repo.
2. Open `QDS_YSL_Airport_Analysis.pbix` in Power BI Desktop (free from Microsoft).
3. Use the slicers on each page to filter by airport, country, or year.
4. To inspect the cleaning steps, open the Power Query Editor (Home → Transform Data).

## Repo Structure

```
├── QDS_YSL_Airport_Analysis.pbix
├── screenshots/
│   ├── page1.png
│   ├── page2.png
│   ├── page3.png
│   └── page4.png
└── README.md
```

## Skills Demonstrated

Data modelling, DAX (calculated measures, YoY comparisons), Power Query ETL, multi-source data integration, KPI/dashboard design, stakeholder-focused data storytelling.
