# Dataset guide (English)

Both CSV files are shared by the French and English labs. Source values and column names are preserved so the exercises remain reproducible. `products.csv` already has English headers and product descriptions.

## Real-estate data: `selogerdata.csv`

| Original column | English reading |
| --- | --- |
| number | Source number |
| codeinsee | INSEE geographic code |
| codepostal, cp | Postal-code fields |
| etage | Floor |
| idagence | Agency ID |
| idannonce | Listing ID |
| idtiers | Third-party ID |
| idtypechauffage | Heating-type code |
| idtypecommerce | Commercial-property-type code |
| idtypecuisine | Kitchen type |
| idtypepublicationsourcecouplage | Publication-source code |
| naturebien | Property-nature code |
| nb_chambres | Number of bedrooms |
| nb_photos | Number of photos |
| nb_pieces | Number of rooms |
| position | Source position field |
| prix | Price |
| si_balcon | Balcony indicator |
| si_sdEau | Shower-room indicator |
| si_sdbain | Bathroom indicator |
| surface | Area |
| typedebien | Property type |
| ville | City |

Common values: `Appartement` means apartment; `Loft/Atelier/Surface` means loft/workshop/space; `aucune` means none; `séparée` means separate; `équipée` means fitted; `américaine` means open-plan; `coin cuisine` means kitchenette.

The source contains encoding artefacts, such as `s√©par√©e` for `séparée` and `Paris 16√®me` for Paris's 16th arrondissement. Inspect these as part of data cleaning. Numeric category codes and sentinel values such as `0` and `-1` have no supplied codebook: do not invent their meaning. Check missing values, duplicates, units and outliers before drawing conclusions.

## Product data: `products.csv`

The agent uses `title`, `description`, `category`, `sub_category` and `selling_price`. It assigns its own integer IDs after loading. Other source fields include brand, rating, discount, image URLs and product URLs. Prices retain their original string format and the dataset does not provide an explicit currency column.
