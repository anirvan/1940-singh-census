# The 1940 Singh Census

By 1940, there were over a thousand Sikh men, their spouses, and their children living in the United States, many of them mixed-race [Punjabi-Mexican](https://en.wikipedia.org/wiki/Punjabi_Mexican_Americans) families.

This dataset **lists all 962 people with the last name "Singh" in the 1940 U.S. Census**. It's made available by [Anirvan Chatterjee](http://www.chatterjee.net/) from the [Berkeley South Asian Radical History Walking Tour](http://www.berkeleysouthasian.org/).

## Datasets

There are two versions of this data, both encoded as standard JSON:

* `1940_singh_census_basic.json` is entirely in the public domain
* `1940_singh_census_with_geodata.json` contains all the domain data, plus some [geodata from OpenStreetMap, licensed under ODBl](https://www.openstreetmap.org/copyright)

## Example record

```json
{
   "age" : "19",
   "birthPlace" : "Oklahoma, United States",
   "birthPlaceNormalized" : "Oklahoma, United States",
   "birthYearApprox" : 1921,
   "censusLocation" : "Sup D 3, Maricopa County, Arizona, United States",
   "censusLocationNormalized" : "Maricopa County, Arizona, United States",
   "children" : [
      "Karlena",
      "Jerry"
   ],
   "gender" : "Female",
   "identifier" : "urn:uuid:5B2CC64F-0DE6-39F4-845A-3640B23D7BEA",
   "inferredGroups" : [
      "non-South Asian wife"
   ],
   "maritalStatus" : "Married",
   "name" : "Mildred Singh",
   "raceRecorded" : "White",
   "raceRecordedNormalized" : "White",
   "relationshipToHead" : "Wife",
   "spouse" : "Rala Singh"
},
```

## Data dictionary

### Main fields

These fields are in the public domain. All of them come straight out of the U.S. Census, except those specified where I did additional cleanup and tagging work.

* `name`: name
* `gender`: either "Male" or "Female"
* `maritalStatus`: either "Single", "Married", "Widowed", or "Divorced"
* `spouse`: name of spouse (in some cases, that spouse will also be in the dataset; look for a person with that name in the same censusLocation)
* `relationshipToHead`: relationship to the census head of household, e.g. "boarder," "son" (there are 44 different statuses!)
* `parents`: names of parents, father's name typically preceding mother's (in some cases, the parents will also be in the dataset; look for a person with that name in the same censusLocation)
* `siblings`: names of siblings
* `raceRecorded`: how the census taker recorded their race, often includes abbreviations, e.g. "White", "Black", "Hin", "H"
* `raceRecordedNormalized`: my normalized version of the race (e.g. I turn "H", "Hi", and "Hin" into ["Hindoo"](https://en.wikipedia.org/wiki/Racial_classification_of_Indian_Americans))
* `age`: age as of the date of the 1940 census, either an integer string like "21", or "<1" for children under 1 year of age
* `birthYearApprox`: approximate birth year (calculated as the age subtracted from 1940)
* `birthPlace`: the birthplace listed in the census, most often a country or US state, e.g. "India", "California, United States", "Sri Lanka", "Asia", "West Indian" (sic), "Inida" (sic)
* `birthPlaceNormalized`: my attempt at normalizing the birth place to a modern geocodable location
* `censusLocation`: the person's location as recorded in the census, often including a district name or number
* `censusLocationCleaned`: my attempt at normalizing the census location to a modern geocodable location
* `identifier`: a unique identifier for this record, expressed as a [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) [URN](https://en.wikipedia.org/wiki/Uniform_Resource_Name)
* `inferredGroups`: one or more of my potentially-incorrect attempts at categorizing people (some of the current groups are "Mexican wife", "married South Asian man", "married South Asian man with kids", and "US-born child")

### OpenStreetMap geographic data

The `1940_singh_census_with_geodata.json` file also contains extended geodata for the named locations, retrieved via [OpenStreetMap's Nominatim](https://nominatim.openstreetmap.org/). The contents of these fields are [© OpenStreetMap contributors](https://www.openstreetmap.org/copyright), and made available under the Open Database License.

* `birthPlaceGeocodedData`: OpenStreetMap data for `birthPlaceCleaned`
* `censusLocationGeocodedData`: OpenStreetMap data for `censusLocationCleaned`

Almost every location in the dataset contains this geocoded data, except for two cases where a person's birthplace is "[West Indies](https://en.wikipedia.org/wiki/West_Indies)," a location OpenStreetMap can't seem to resolve. (Maybe I should have resolved that to "Haiti" and just called it a day?)

# Citation

While the main dataset is in the public domain, you're encouraged to cite the source. For example:

> Chatterjee, Anirvan. (2017). _1940 Singh Census_. Retrieved from https://github.com/anirvan/1940-singh-census.

If you're using the OpenStreetMap geodata, they [ask for a credit](https://www.openstreetmap.org/copyright).
