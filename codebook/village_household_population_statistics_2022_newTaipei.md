# Codebook: Village Household and Population Statistics (2022, New Taipei)

## Dataset Information
- **Path**: `data/raw/村(里)界(TWD97經緯度)1141031/village_household_population_statistics_2022_newTaipei.csv`
- **Source**: [政府資料開放平臺 - 村里戶數及人口數統計表](https://data.gov.tw/dataset/14299) — filtered from the full 2022 release to New Taipei City only
- **Statistical Year**: 2022 (民國111年)
- **Geographic Coverage**: New Taipei City villages (里) only; 1,032 records (1 header + 1,032 data rows)
- **Encoding**: UTF-8 (set locale or `fileEncoding`/`locale(encoding="UTF-8")` when reading)
- **Headers**: Column names translated to English; values remain in Chinese for region/village names.
- **Filter Applied**: `區域別` contains "新北市"

## Variables

| Column (CSV header) | Origianl Chinese header | Type | Description |
|---------------------|-----------|------|-------------|
| Statistical Year | 統計年 | Integer | Year in ROC calendar (111 = 2022 CE) |
| Region Code | 區域別代碼 | String | Unique village identifier; aligns with `VILLCODE` in the NLSC village boundary shapefile |
| Region Name | 區域別 | String | Full admin name (City/County + District + Village) |
| Village Name | 村里名稱 | String | Village name (里/村) |
| Ordinary Households | 共同生活戶_戶數 | Integer | Number of ordinary (family) households |
| Institutional Households | 共同事業戶_戶數 | Integer | Number of institutional households |
| Single-person Households | 單獨生活戶_戶數 | Integer | Number of single-person households |
| Ordinary Households - Male | 共同生活戶_男 | Integer | Male population in ordinary households |
| Institutional Households - Male | 共同事業戶_男 | Integer | Male population in institutional households |
| Single-person Households - Male | 單獨生活戶_男 | Integer | Male population in single-person households |
| Ordinary Households - Female | 共同生活戶_女 | Integer | Female population in ordinary households |
| Institutional Households - Female | 共同事業戶_女 | Integer | Female population in institutional households |
| Single-person Households - Female | 單獨生活戶_女 | Integer | Female population in single-person households |

## Derived Fields (common)
- `total_population = 共同生活戶_男 + 共同事業戶_男 + 單獨生活戶_男 + 共同生活戶_女 + 共同事業戶_女 + 單獨生活戶_女`
- `total_households = 共同生活戶_戶數 + 共同事業戶_戶數 + 單獨生活戶_戶數`
- Optional gender counts: `total_male`, `total_female`
- Gender ratio: `total_male / total_female`

## Household Type Definitions
- **共同生活戶 (Ordinary Households)**: Family/related members living together (nuclear, extended, multi-generational).
- **共同事業戶 (Institutional Households)**: Group living for specific purposes (dormitories, barracks, worker housing, religious institutions, care facilities).
- **單獨生活戶 (Single-person Households)**: One-person households.

## Usage Notes
- Subset of the national dataset: rows where `區域別` includes `新北市`; `區域別代碼` starts with `65` for New Taipei.
- Join to spatial data: use `區域別代碼` ↔ `VILLCODE` from `VILLAGE_NLSC_11401031.shp` (filter the shapefile to New Taipei when mapping).
- Missing values are represented as 0.
- When plotting skewed distributions, consider `sqrt` or `log10` scales.

## Last Updated
- Generated: 2025-12-10
