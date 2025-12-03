# Codebook: Village Household and Population Statistics

## Dataset Information

**Source**: [政府資料開放平臺 - 村里戶數及人口數統計表](https://data.gov.tw/dataset/14299)

**Original Filename**: `6926e8fd62668ca8b1d3056aae8ed8d0_export.csv`

**New Filename**: `village_household_population_statistics_2022.csv`

**Description**: This dataset contains household and population statistics for villages (村/里) across Taiwan, broken down by household type and gender.

**Statistical Year**: 2022 (民國111年)

**Geographic Coverage**: All villages in Taiwan (including main island and offshore islands)

## Variable Definitions

| Variable Name | English Translation | Data Type | Description |
|--------------|-------------------|-----------|-------------|
| 統計年 | Statistical Year | Integer | Year of statistics (ROC calendar, 111 = 2022 CE) |
| 區域別代碼 | Region Code | String | Unique identifier code for the village |
| 區域別 | Region Name | String | Full administrative name (City/County + District + Village) |
| 村里名稱 | Village Name | String | Name of the village (里) |
| 共同生活戶_戶數 | Ordinary Households | Integer | Number of ordinary (family) households |
| 共同事業戶_戶數 | Institutional Households | Integer | Number of institutional households (e.g., dormitories, military barracks) |
| 單獨生活戶_戶數 | Single-person Households | Integer | Number of single-person households |
| 共同生活戶_男 | Ordinary Households - Male | Integer | Male population in ordinary households |
| 共同事業戶_男 | Institutional Households - Male | Integer | Male population in institutional households |
| 單獨生活戶_男 | Single-person Households - Male | Integer | Male population in single-person households |
| 共同生活戶_女 | Ordinary Households - Female | Integer | Female population in ordinary households |
| 共同事業戶_女 | Institutional Households - Female | Integer | Female population in institutional households |
| 單獨生活戶_女 | Single-person Households - Female | Integer | Female population in single-person households |

## Household Type Definitions

### 共同生活戶 (Ordinary Households)
Households where family members live together, including:
- Nuclear families
- Extended families
- Multi-generational households

### 共同事業戶 (Institutional Households)
Group living arrangements for specific purposes, including:
- Student dormitories
- Military barracks
- Worker dormitories
- Religious institutions
- Care facilities

### 單獨生活戶 (Single-person Households)
Households with only one person living alone

## Data Notes

1. **Total Population Calculation**: Sum of all male and female populations across all household types
2. **Total Households**: Sum of all three household types
3. **Missing Values**: Represented as 0 in the dataset
4. **Administrative Levels**: Data follows Taiwan's administrative hierarchy:
   - 縣/市 (County/City)
   - 區 (District)
   - 里/村 (Village)

## Usage Examples

### Calculate Total Population by Village
```r
village_data %>%
  mutate(total_population = 
    共同生活戶_男 + 共同事業戶_男 + 單獨生活戶_男 +
    共同生活戶_女 + 共同事業戶_女 + 單獨生活戶_女)
```

### Calculate Gender Ratio
```r
village_data %>%
  mutate(
    total_male = 共同生活戶_男 + 共同事業戶_男 + 單獨生活戶_男,
    total_female = 共同生活戶_女 + 共同事業戶_女 + 單獨生活戶_女,
    gender_ratio = total_male / total_female
  )
```

## Related Files

- Shapefile: `VILLAGE_NLSC_11401031.shp` (村里界 TWD97經緯度)
- Can be joined using village names or region codes

## Last Updated

2025-12-03
