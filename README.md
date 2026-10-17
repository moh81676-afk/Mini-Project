# Mini Project 3 – Global Country Comparison Dashboard (Power BI)

An interactive, 4-page Power BI report that compares **262 countries and territories** across economy, population, health, trade and development indicators.

## Dataset
`Country Data Comparison.csv` (semicolon-delimited, loaded with Power Query) – one row per country with 15 indicators:

| Group | Fields |
|---|---|
| Economy | GDP, GDP per Capita, GDP Growth, Inflation, Unemployment |
| Trade | Exports, Imports |
| Population & health | Population, Birth Rate, Death Rate, Infant Mortality, Life Expectancy |
| Other | Area, Internet Users |

## Data modelling
Calculated columns (DAX) that classify each country:
- **GDP Category** – Low (< $5B), Medium (< $50B), High
- **Population Category** – Small (< 1M), Medium (< 10M), Large
- **Development Level** – High (life expectancy ≥ 75 and GDP/capita ≥ $15K), Medium (≥ 65 and ≥ $3K), Low, or Unknown
- **Growth Indicator Category** – Negative, Low (< 3%), Moderate (< 6%), High
- Sort-order columns so categories display in a logical order

Around **46 DAX measures**, organised in measure tables, including:
- Totals and averages (GDP, population, exports/imports, life expectancy, inflation…)
- `Trade Balance`, `Internet Penetration %`, `GDP Share %`
- `GDP Rank` and `Population Rank` (RANKX)
- Dynamic "Top country" labels (TOPN + CONCATENATEX)
- Comparison against the global **median** (e.g. `Life Expectancy vs Median` shows ▲ / ▼ gaps)

## Report pages
1. **Executive Overview** – KPI cards (countries, population, GDP, GDP growth, life expectancy, inflation), map, GDP ranking bar chart with GDP share, donut by development level, and distribution of countries by GDP and growth category.
2. **Country Comparison** – scatter plot (GDP per capita vs. infant mortality, bubble size = GDP), a country table, and bar charts for GDP growth, infant mortality and exports vs. imports.
3. **Country Details** – single-country profile: KPI cards, a life-expectancy gauge vs. the global median, trade (exports / imports / balance) and demographics (birth rate, death rate, infant mortality).
4. **Insights** – top country for GDP, growth, life expectancy and infant mortality, plus a matrix of development level × growth category.

All pages share slicers (development level, GDP, population and growth category, country) and navigation buttons.

## Key figures
- 262 countries/territories; combined GDP ≈ **$55.6 trillion**
- Largest economies: United States ($11.8T), China ($7.3T), Japan ($3.7T), India ($3.3T), Germany ($2.4T)
- Development levels: 51 High · 86 Medium · 125 Low
- Highest life expectancy: Andorra (83.5 years) · Highest infant mortality: Angola (191 per 1,000)
- GDP per capita is moderately correlated with life expectancy (r ≈ 0.52)

## Known limitation
Missing values in the source CSV are stored as `0` (e.g. 38 rows have life expectancy = 0, 33 have GDP = 0). They are currently included in the averages and in the development classification, which pulls averages down (the average life expectancy shows ≈ 58 years). Planned improvement: convert zeros to blanks in Power Query so the existing "Unknown" categories and `ISBLANK` checks work as intended.

## Tools
Power BI Desktop · Power Query · DAX · Data modelling · Data visualization

## How to open
Download `Mini-Project_3.pbix` and open it with [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free).

## Author
**Mohamed Ali** – Junior Data Analyst
[LinkedIn](https://linkedin.com/in/mohamedali-zaho) 
