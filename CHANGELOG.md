# Changelog

## [Unreleased]

### Added

* exposed a parameter in `reverseGeocode` requests to fetch intersections.

### Fixed

* appropriate l18n input parameter is now passed in `reverseGeocode` requests

## [2.0.1]

### Fixed

* ensured that options from Geosearch constructor are mixed in correctly.

## [2.0.0]

### Added

* implemented a new 'countries' parameter for the `arcgisOnlineProvider` based on new capabilities of the [World Geocoding Service](https://developers.arcgis.com/rest/geocode/api-reference/overview-world-geocoding-service.htm) #38
* implemented a new 'categories' parameter for the `arcgisOnlineProvider` based on new capabilities of the [World Geocoding Service](https://developers.arcgis.com/rest/geocode/api-reference/overview-world-geocoding-service.htm)
* added the ability to include 'categories' in requests using `L.esri.Geocoding.suggest`
* updated result objects across providers to include the actual GeoJSON of candidates #81

### Fixed

* included additional logic to ensure that queries are case insensitive #83 (thanks @rntdrts)
* refactored the calculation of result bounds calculation to avoid uncaught exceptions and usage of `new` #84

## [2.0.0-beta.3]

### Fixed

* Missing files in NPM release.

## [2.0.0-beta.2]

### Fixed

* Missing sourcemap in build.

## [2.0.0-beta.1]

### Breaking

* Requires the 2.0.0-beta.4 release of Esri Leaflet.
* Require the 1.0.0-beta.1 release of Leaflet.
* Namespaces have changed all exports now sit directly under the `L.esri.Geocoding` namespace. This mean that things like `L.esri.Geocoding.Controls.Geosearch.Providers.FeatureLayer` can now be accessed like `L.esri.Geocoding.FeatureLayerProvider`.
* `useArcgisWorldGeocoder` has been removed. Now you must pass `L.esri.Geocoding.arcGisOnlineProvider()` in the `providers` array. This will facilitate easily passing options to the ArcGIS Online geocoder.

### Added

* Better build/test/release automation.
* Support for JSPM in package.json. Now you can `import geocode from 'esri-leaflet-geocoder/src/Tasks/Geocoder';` for more compact builds but, be aware of [caveats](http://blog.izs.me/post/44149270867/why-no-directories-lib-in-node-the-less-snarky)
* Support for browserify in the package.json. Now you can `var geocode = require('esri-leaflet-geocoder/src/Tasks/Geocoder');` for more compact builds, but be aware of [caveats](http://blog.izs.me/post/44149270867/why-no-directories-lib-in-node-the-less-snarky)

## [1.0.2]

* Fix bug in Suggest logic affecting older versions of ArcGIS Server (#77)

## [1.0.1]

* Fix incorrect version number in built files.

## [1.0.0]

This represents the stable release of Esri Leaflet Geocoder compatible with Leaflet 0.7.3. All future 1.0.X releases will be compatible with Leaflet 0.7.3 and contain only bug fixes. New features will only be added in Esri Leaflet Geocoder 2.0.0 which will require Leaflet 1.0.0.

### Changes

* Introduced support for dynamic suggestions from custom geocoding services. #65
* Refactored code to account for changes introduced in Esri Leaflet `1.0.0`. #75
* Fixed problem in `initialize` #63 (thanks @timwis!)
* Plugin now dynamically sets a hard search extent when `useMapBounds` is set to true. #58

## Release Candidate 3

### Breaking Changes

* Providers should now supply their `url` with the `url` key inside of `options` as opposed to a separate parameter.
* Namespace has been reorganized. everything now sits under `L.esri.Geocoding`. So `L.esri.Tasks.Geocode` is now `L.esri.Geocoding.Tasks.Geocode`.

### Changes

* `MapService` provider now supports being passed an array of layers to search. https://github.com/Esri/esri-leaflet-geocoder/issues/48
* `title` option will now set the title on the input to `'Location Search'` by default. https://github.com/Esri/esri-leaflet-geocoder/pull/51
* When using many providers or when a provider returns lots of results with a high limit, the suggestions div will now scroll. https://github.com/Esri/esri-leaflet-geocoder/issues/55
* `within()` and `nearby()` now return the task and can be changed. https://github.com/Esri/esri-leaflet-geocoder/pull/49
* Bugfix for `MapService` provider https://github.com/Esri/esri-leaflet-geocoder/issues/46

## Release Candidate 2

### Changes

* Bower support `bower install esri-leaflet-geocoder`
* Update Esri Leaflet dependency to RC 3

## Release Candidate 1

Please read through the docs and changes list carefully. There has been a major refactoring.

** Breaking Changes **

* Namespacing has changed. All methods and classes are now under `L.esri.Geocoding`. `L.esri.Geocoding` organizes everything into `Controls`, `Services`, and `Tasks`.
* `GeocodeService` has been rewritten from scratch to mirror the Esri Leaflet service style that returns tasks.
* `GeocodeService.suggest`, `GeocodeService.geocode` and `GeocodeService.reverse` all return their respective tasks.

** Changes **

* New tasks for `Suggest`, `Geocode` and `ReverseGeocode` that mirror the Esri Leaflet task structure.
* `L.esri.Geocoding.Controls.Geosearch` can now search multiple providers.
* Available on NPM and Bower
* Wrapped as a CommonJS module
* Wrapped as an AMD module
* Basic unit tests
* TravisCI support
* Source maps for compressed builds

## Beta 5

**Changes**
* Improve experience for users when they hit enter with no suggestion selected. The current test in the input will be geocoded and the map centered on the extent of all results. This behavior can be disabled by setting `allowMultipleResults` to `false`.
* Fix behavior of `useMapBounds` which was incorrect.
* Don't pass `bbox` with suggest. The suggest API doesn't use it.
* Increase `useMapBounds` default to `12`.

## Beta 4

**Breaking Changes**
* Esri Leaflet Geocoder now relies on the Esri Leaflet Core build, find out more on the [Esri Leaflet downloads page](http://esri.github.com/esri-leaflet/downloads).
* The callback signatures on `L.esri.Services.Geocoding`. The raw response is now the 3rd parameter and the second parameter is now a processed array of [Geocode Results](https://github.com/Esri/esri-leaflet-geocoder#geocode-results) or a[Reverse Geocode Results](https://github.com/Esri/esri-leaflet-geocoder#reverse-geocode-result) depending on the call.
* `L.esri.Services.Geocoding` no longer accepts the `outFields` parameter.

**Changes**
* Fix a display issues where the form would close but would not expand again. https://github.com/Esri/esri-leaflet-geocoder/issues/33
* Now that `L.esri.Services.Geocoder` extends on `L.esri.Services.Service` you can pass the `forStorage` flag with any call and authenticate. Listen for the `authenticationrequired` event and provide a token or pass a `token` option.

## Beta 3

* Fix style to accommodate `topright` position
* Fix some leaflet-touch style issues

## Beta 2

* Fix bug in IE 10 and 11 on Windows 8 touch devices

## Beta 1

This is now ready for beta! This release helps finalize the API and includes lots of cross browser support.

## Alpha 2

**Breaking Changes**
* `result` and `results` events have been refactored into a single `results` event with and array of results.

**Changes**
* When the user hits enter without a suggestion selected their current text is geocoded within the current map bounds.
* Esri attribution added
* `error` event added

## Alpha 1

* Add the `allowMultipleResults` option. https://github.com/Esri/esri-leaflet-geocoder/issues/6

# Alpha

* Initial alpha release

[Unreleased]: https://github.com/Esri/esri-leaflet-geocoder/compare/v2.0.1...HEAD
[2.0.1]: https://github.com/Esri/esri-leaflet-geocoder/compare/v2.0.0...v2.0.1
[2.0.0]: https://github.com/Esri/esri-leaflet-geocoder/compare/v2.0.0-beta.3...v2.0.0
[2.0.0-beta.3]: https://github.com/Esri/esri-leaflet-geocoder/compare/v2.0.0-beta.2...v2.0.0-beta.3
[2.0.0-beta.2]: https://github.com/Esri/esri-leaflet-geocoder/compare/v2.0.0-beta.2...v2.0.0-beta.3
[2.0.0-beta.1]: https://github.com/Esri/esri-leaflet-geocoder/compare/v2.0.0-beta.2...v2.0.0-beta.3
[1.0.2]: https://github.com/Esri/esri-leaflet-geocoder/compare/v1.0.1...v1.0.2
[1.0.1]: https://github.com/Esri/esri-leaflet-geocoder/compare/v1.0.1...v1.0.2
[1.0.0]: https://github.com/Esri/esri-leaflet-geocoder/compare/v1.0.0...v1.0.2
