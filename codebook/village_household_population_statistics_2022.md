# Codebook: Village Household and Population Statistics (2022)

## Dataset Information
- **Path**: `data/raw/村(里)界(TWD97經緯度)1141031/village_household_population_statistics_2022.csv`
- **Source**: [政府資料開放平臺 - 村里戶數及人口數統計表](https://data.gov.tw/dataset/14299)
- **Statistical Year**: 2022 (民國111年)
- **Geographic Coverage**: All villages (村/里) in Taiwan, including offshore islands
- **Encoding**: UTF-8 (set locale or `fileEncoding`/`locale(encoding="UTF-8")` when reading)

## Variables

| 原始欄位名 | English | Type | Description |
|-----------|---------|------|-------------|
| 統計年 | Statistical Year | Integer | Year in ROC calendar (111 = 2022 CE) |
| 區域別代碼 | Region Code | String | Unique village identifier; aligns with `VILLCODE` in the NLSC village boundary shapefile |
| 區域別 | Region Name | String | Full admin name (City/County + District + Village) |
| 村里名稱 | Village Name | String | Village name (里/村) |
| 共同生活戶_戶數 | Ordinary Households | Integer | Number of ordinary (family) households |
| 共同事業戶_戶數 | Institutional Households | Integer | Number of institutional households |
| 單獨生活戶_戶數 | Single-person Households | Integer | Number of single-person households |
| 共同生活戶_男 | Ordinary Households - Male | Integer | Male population in ordinary households |
| 共同事業戶_男 | Institutional Households - Male | Integer | Male population in institutional households |
| 單獨生活戶_男 | Single-person Households - Male | Integer | Male population in single-person households |
| 共同生活戶_女 | Ordinary Households - Female | Integer | Female population in ordinary households |
| 共同事業戶_女 | Institutional Households - Female | Integer | Female population in institutional households |
| 單獨生活戶_女 | Single-person Households - Female | Integer | Female population in single-person households |

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
- Missing values are represented as 0.
- Join to spatial data: use `區域別代碼` ↔ `VILLCODE` from `VILLAGE_NLSC_11401031.shp`.
- When plotting skewed distributions, consider `sqrt` or `log10` scales.

## Last Updated
- Generated: 2025-12-03
