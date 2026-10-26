# Code-and-dataset-from-Hima-project
There are all the data and codes used in the test for Hima region. 
1. Method describtion:
To establish comparable environmental background, a 1:1 Propensity Score Matching scheme (Duncanson et al., 2023) was performed between pixels inside and outside the Hima area. Topographic covariates—including elevation, slope, and aspect—along with strict land cover constraints (excluding urban areas, cropland, and water bodies) were incorporated as matching criteria. The Propensity Score Matching codes in R are in file PSM by Duncanson et al., 2023.
NPP was compared in 2024 and 2025, the comperation codes are in file NPP Varchart codes.
2. Data describtion (download codes in CASA-GEE codes):
Input Datasets Used: Landsat 8 and 9 Collection 2 Surface Reflectance provides 30m resolution optical bands to generate cloud-masked monthly composite NDVI images. ERA5-Land Monthly Aggregated Data supplies climate drivers including downward solar radiation, air temperature, actual evapotranspiration, and potential evapotranspiration. ESA WorldCover 10m provides land cover classification to dynamically define optimal temperatures and maximum light use efficiency for different biomes.
CASA Model Workflow (the model is pre-packaged with GEE): Landsat QA bands are used to remove clouds and bad pixels before deriving monthly median NDVI images. FPAR is computed by linearly scaling monthly NDVI between its dynamic 5th and 95th percentiles. PAR is calculated as a fixed fraction of downward solar radiation from ERA5-Land. Temperature stress is derived by comparing air temperature against biome-specific optimal temperatures, while water stress is estimated using the ratio of actual to potential evapotranspiration. Maximum light use efficiency values are assigned to pixels based on land cover types. Monthly NPP is calculated by multiplying PAR, FPAR, temperature stress, water stress, and maximum light use efficiency. Finally, monthly NPP values are aggregated into annual products for years with sufficient valid data and exported to NPP file.
3. Codes update
20261026-Update codes in audit loop of hima test.

Reference:
Duncanson, L., Liang, M., Leitold, V., Armston, J., Krishna Moorthy, S. M., Dubayah, R., Costedoat, S., Enquist, B. J., Fatoyinbo, L., Goetz, S. J., Gonzalez-Roglich, M., Merow, C., Roehrdanz, P. R., Tabor, K., & Zvoleff, A. (2023). The effectiveness of global protected areas for climate change mitigation. Nature Communications, 14(1), Article 1. https://doi.org/10.1038/s41467-023-38073-9
