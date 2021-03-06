# Packaging

Initial ideas for packaging study and trial data.  See [datapackages](http://data.okfn.org/doc/data-package) for more details on this style of packaging and manifest spec.


## Studies

Sample file layout for storing XROMM **study** data and associated metadata:

    /project/rossc/lab/experiments/
      monkey-feeding/
        README.md
        study.json              # contains study metadata
        models/
        trials/
          <trial_id_a>/
            trial.json          # contains metadata for each file
            <file_1>
            <file_2>
            <file_3>
          <trial_id_b>/
            trial.json          # contains metadata for each file
            <file_1>
            <file_2>
            <file_3>
            
      lizard-locomotion/
        README.md
        study.json
        models/
        trials/
      alligator-coracoid/         # example used below
        README.md
        study.json                # see below
        models/
          all-markers.zip
          coracoid.zip
        trials/
          markerless.zip
          single-marker.zip
          double-marker.zip
          all-markers.zip


#### `study.json`

Here's an example `study.json` file for the [`alligator-coracoid`](http://xmaportal.org/sandbox/larequest.php?request=explorePublicStudy&StudyID=6&instit=SANDBOX1) example study.  Note that many of the resources associated with a study might also be [datapackages](http://data.okfn.org/doc/data-package) with their own `package.json` containing metadata for the file(s) comprising that resource.

```json
{
  "name": "alligator-coracoid",
  "title": "Alligator Coracoid Example Data",
  "description": "Data for markerless XROMM short-course tutorial",
  "keywords": [
    "coracoid",
    "markerless",
    "example"
  ],
  "version": "1.0",
  "license": "PDDL-1.0",
  "investigators": "Brainerd, Beth",
  "study_leader": "Camp, Ariel",
  "last_updated": "2007-10-31",
  "resources": [
    {
      "file": "trials/markerless.zip",
      "name": "Markerless Trial",
      "format": "trialpackage",
      "mediatype": "application/zip",
      "description": "isolated coracoid bone with no markers"
    },
    {
      "file": "trials/single-marker.zip",
      "name": "Single Marker Trial",
      "format": "trialpackage",
      "mediatype": "application/zip",
      "description": "isolated coracoid bone with marker 1"
    },
    {
      "file": "trials/double-marker.zip",
      "name": "Double Marker Trial",
      "format": "trialpackage",
      "mediatype": "application/zip",
      "description": "isolated coracoid bone with markers 1 and 4"
    },
    {
      "file": "trials/all-markers.zip",
      "name": "All Markers Trial",
      "format": "trialpackage",
      "mediatype": "application/zip",
      "description": "isolated coracoid bone with all 4 markers"
    },
    {
      "file": "trials/calibration.zip",
      "name": "Calibration",
      "format": "trialpackage",
      "mediatype": "application/zip",
      "description": "calibration data for these trials"
    },
    {
      "file": "models/coracoid.zip",
      "name": "Coracoid Bone Model",
      "format": "datapackage",
      "mediatype": "application/zip",
      "description": "Polygonal mesh models of coracoid bone"
    },
    {
      "file": "models/all-markers.zip",
      "name": "4 Marker Model",
      "format": "datapackage",
      "mediatype": "application/zip",
      "description": "Polygonal mesh models of all 4 markers"
    }
  ]
}
```


## Tools and Examples

* [datapackage-json](https://github.com/maxogden/datapackage-json) - module to manage a `package.json` for [tabular data packages](http://dataprotocols.org/tabular-data-package/)

* [dpm](https://github.com/okfn/dpm) - library and command line manager for
  [data packages](http://dataprotocols.org/data-packages/)

* [Data Packager](http://ckan.org/2014/06/09/the-open-knowledge-data-packager/) - The CKAN folks developed [a web app](http://datapackager.okfn.org/) for quickly creating and publishing [data packages](https://github.com/datasets).  This is just a nice example of a clean front-end for uploading data files as a package with associated metadata.

* [Example upload script](https://github.com/ckan/example-add-dataset) -
  Example script that uses the CKAN API to create a dataset and upload some
  files to it.
