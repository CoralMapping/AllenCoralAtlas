## Allen Coral Atlas data standards ##
`TODO: workshop what this standard document should actually be for`

### file naming, bands and no-data values: ###

- surface reflectance products: 
    - always *.tif 
    `todo:  determine if it should be something else, e.g.: *_sr.tif`
    - RGBN bands, no alpha band
    - no data value = 0 
    `todo: 0's are real though i think - no data is undefined in .tif attributes - is that desired?`
    - high/low/any tide, determined by: *_high*...

- rb quads: 
    - *_rb.tif
    - RGB bands
    - no data value = 0 
    `todo: currently no data value is set to -9999 (as per depth), but 0 would be better to have unsigned integers`
    - high/low/any tide, determined by: *_high*...

- depth quads: 
    - *_depth.tif 
    - no data values
      - -1 = negative reterivals (*probably* very shallow)
      - -2 = land/exposed
      - -3 = very bright (*usually* cloud and breaking wvaes)
    - high/low/any tide, determined by: *_high*...