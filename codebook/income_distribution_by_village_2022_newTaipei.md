# Codebook: Income Distribution by Village (Tax Year 2022, New Taipei City)

## Dataset Information
- **Path**: `data/income_distribution_by_village_2022_newTaipei.csv`
- **Source**: [政府資料開放平臺 - dataset 17975](https://data.gov.tw/dataset/17975) (exported CSV)
- **Tax Year**: 2022 (ROC 111)
- **Geographic Coverage**: All villages/里 across Taiwan (and outlying islands)
- **Rows**: 1,093 (1 header + 1,092 data rows)
- **Encoding**: UTF-8 with BOM (keep `encoding="UTF-8"` or `utf-8-sig`)
- **Headers**: Translated to English (values remain in Chinese for region/village names)

## Variables

| Column (CSV header) | Original | Type | Description |
|---------------------|----------|------|-------------|
| Region Name | 縣市別 | String | County/City + District combined (e.g., 新北市新莊區) |
| Village Name | 村里 | String | Village/里 name |
| Tax Units (Households) | 納稅單位(戶) | Integer | Number of filing units (households) in the village |
| Total Comprehensive Income | 綜合所得總額 | Numeric | Aggregate comprehensive income across tax units (likely thousand NTD; confirm with source metadata) |
| Mean Income | 平均數 | Numeric | Mean comprehensive income per tax unit |
| Median Income | 中位數 | Numeric | Median comprehensive income per tax unit |
| 1st Quartile Income | 第一分位數 | Numeric | 25th percentile of comprehensive income per tax unit |
| 3rd Quartile Income | 第三分位數 | Numeric | 75th percentile of comprehensive income per tax unit |
| Standard Deviation | 標準差 | Numeric | Std. dev. of comprehensive income per tax unit |
| Coefficient of Variation | 變異係數 | Numeric | `標準差 / 平均數` |

### Derived in analysis
- `mean_income_calc`: `Total Comprehensive Income / Tax Units (Households)`; used to confirm the reported mean.

## Usage Notes
- Monetary unit in the source is not stated in the CSV; it is commonly thousand NTD in MOF tax tables—confirm with the dataset page.
- Values for county/district/village are in Chinese; join to spatial boundaries using consistent naming or codes if available elsewhere.
- CSV includes a UTF-8 BOM; some parsers may need `encoding=\"utf-8-sig\"`.

## Last Updated
- Updated: 2024-12-10
