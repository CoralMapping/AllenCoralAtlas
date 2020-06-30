## Allen Coral Atlas data standards ##
TODO: workshop what this standard document should actually be for
    - Will it be for both internal and external?
    - Should we separate into two standards docs? i.e. one for internal with data I/O and ingestion standards, and another for extneral use ofr users with download specs

### Visual image products: ###
- Planet Dove multitemporal mosaics
    - Date range typically []
    - Aquisition within low tide window
    - Proprietory mosaicing algorithm, including normalisation + cloud masking + ...
- Acquisition within global reef mask [reef mask repo link]

### Bathymetry products: ###
- Three satellite sensor sources:
    - Planet Dove (aquisition within low tide window)
    - Sentinel-2 (filtered for cloud free scenes)
    - Landsat 8 (filtered for cloud free scenes)
- Methods:
    - Consistent method across sensors, sensu Li et al. 2019 [paper link]
    - Specific links to processing code repos:
        - [Dove link]
        - [Landsat/S2 link]?
    - Mapping approach uses a composite depth that combines products to form a seamless mosaic. Current protocol is to preference Senintel-2 -> Landsat 8 -> Dove
        - [Composite repo link]
- Data values:
    - Depth estimates in centimeters
    - No data flags:
        - Negative retreival `[-1]`
        - Land `[-2]`
        - Very bright pixels (clouds, breaking waves) `[-3]`

### Wave products: ###
- Fetch based/closure depth model using composite bathymetry layer
- Based on Harris et al. XXXX [paper link]

### Mapping products: ###
- Geomorphic and benthic zones
    - Scientific paper on zonations [Kennedy et al. 2020]
    - Class numbers [class number repo link]
- Methods:
    - Consistent across globe, sensu Lyons et al. 2020 [paper link]
    - Specific links to processing code repos:
        - [gee-mapping-source]
#### proposed & for review ####
- Bands in export stack (pre-Atlas ingestion):
    `0:` composite depth [centimeters]
    `1:` reef/no reef [binary]
    `2:` geomorphic [classification]
    `3:` benthic [classification]
    `4:` confidence [relative percentage - see below]
- No data flags (in geo/benthic bands):
    - Imagery available, but water depth or quality prevented classifiction `[0]`
    - Imagery available, but area manually masked out (no reef present, turbidity, inland water, river mouths) `[-1]`
    - Missing image or depth data `[-2]`
- Confidence layer, combines:
    - random forest classification probability
    - scaled by reference sample expert confidence
    - intersected with image QAQC data (aretfects etc.)

### Monitoring products: ###
- TODO

### Download file specifications: ###
- TODO

