# Geokodikas Exports [![CircleCI](https://circleci.com/gh/geokodikas/exports.svg?style=svg)](https://circleci.com/gh/geokodikas/exports)
Repo to manage exports for Geokodikas

## Procedure for generating new export

 1. clone this repo
 2. edit the `exports.yaml` file. Add the following template under a specific country:
 ```
    - completed: false
      download_date: COMPLETE_ME
      osm_pbf_file: COMPLETE_ME
      osm_pbf_md5sum:  COMPLETE_ME
      export_filename: ''
      export_download_url: ''
      export_md5sum: ''
 ```
 3. fill the fields which contain the `COMPLETE_ME` string
 4. commit and push to the repo
 5. CircleCI will automatically create a new export
 6. look at the [CircleCI Jobs](https://circleci.com/gh/geokodikas/exports/tree/master) and wait until it's finished
 7. update the `exports.yaml` file:
    - set `completed` to `true`
    - set `export_filename` and `export_md5sum` to the values reported at the `Run Exporeters` of the CircleCI run
    - set `export_download_url` to the url of the artifact created by CircleCI
 8. commit and push
 9. CircleCI won't create exports when the `completed` flag is set to `true`

## How does this work?

The configuration of CircleCI can be found [here](https://raw.githubusercontent.com/geokodikas/exports/master/.circleci/config.yml).
The real thing is done by the `ci-export-manager` Docker container.

