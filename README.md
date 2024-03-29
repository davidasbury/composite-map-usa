# Composite USA Map Viewer

This is a configurable app that can show various views of the United States within the same frame. Each map uses the Albers equal-area projection and all views (except Alaska) are dynamically rendered at the same scale. The rendered scale is set on page load by the viewport size. This allows for better thematic mapping as areas across the country can be more accurately compared.

While the app is responsive and the maps will render on any screen or iframe, the layouts have been optimized for an aspect ratio of 1.777 (16/9)

[Click for a sample](https://davidasbury.github.io/composite-map-usa/)

[![Screenshot 2022-12-23 at 3 13 13 PM](https://user-images.githubusercontent.com/6776067/209412615-8b239746-39de-4005-ae72-ad5dbd943c91.png)](https://davidasbury.github.io/composite-map-usa/)

This app is a modification of the Composite Views sample on the ArcGIS Developer site: [ArcGIS Maps SDK for JavaScript
Sample Code | Composite Views](https://developers.arcgis.com/javascript/latest/sample-code/views-composite-views/)

## Configure URL parameters

The base url uses a feature service that can be swapped out with a url parameter. Other parameters can be used to change the overview map and show/hide individual inset maps.

### To change the data being displayed on the map:

``<base URL>?featurelayer=<feature layer ID>`` 

where ``<feature layer ID>`` is an item ID for any feature service. You can use ArcGIS Server (non-hosted) feature services, but they must be registered with an ArcGIS Enterprise or ArcGIS Online portal in order to have an item ID. 

Example: [https://davidasbury.github.io/composite-map-usa?featurelayer=c93f8a9f2a614ff8a31db732636eff9b](https://davidasbury.github.io/composite-map-usa?featurelayer=c93f8a9f2a614ff8a31db732636eff9b)

The map can use **any** feature service and will dynamically reproject the data within each view.

### To change the overview map:

``<base URL>?featurelayer=<feature layer ID>&overview=<webmap ID>``

where ``<webmap ID>`` is any ArcGIS Online webmap in WGS84 or Web Mercator projection. This is a requirement of the [3D SceneViewer](https://developers.arcgis.com/javascript/latest/api-reference/esri-views-SceneView.html#spatialReference).

Example using the Oceans Basemap: [https://davidasbury.github.io/composite-map-usa?featurelayer=c93f8a9f2a614ff8a31db732636eff9b&overview=67ab7f7c535c4687b6518e6d2343e8a2](https://davidasbury.github.io/composite-map-usa?featurelayer=c93f8a9f2a614ff8a31db732636eff9b&overview=67ab7f7c535c4687b6518e6d2343e8a2)

### To change which inset maps are shown

By default all inset maps are shown. If your feature service does not include data for some of the areas, you can show only those insets that contain data.

``<base URL>?views=<views>``

where ``<views>`` is a comma separated list of the [ISO 3166 alpha-2 code](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) for each area of interest. Entries are not case-sensitive. Include any of the following entries to customize your view. For example:


``AK`` = Alaska

``HI`` = Hawaii

``PR`` = Puerto Rico

``VI`` = US Virgin Islands

``GU`` = Guam

``AS`` = American Samoa

``MP`` = Commonwealth of the Northern Mariana Islands

``UM`` = United States Minor Outlying Islands

``globe`` = Overview map

``None`` = Continental US only


Due to layout constraints, some views are paired together. For example, if you'd like to see Puerto Rico, you will also see the US Virgin Islands. The same is true for Guam/Northern Marianas. Alaska and Hawaii can also not be displayed individually and the Alaska/Hawaii insets will always be shown when choosing either American Samoa or Guam/Northern Marianas.

[Example showing zip codes and AK/VI views](https://davidasbury.github.io/composite-map-usa/?featurelayer=c93f8a9f2a614ff8a31db732636eff9b&overview=67ab7f7c535c4687b6518e6d2343e8a2&views=ak,vi)

[![Screenshot 2022-12-23 at 3 06 56 PM](https://user-images.githubusercontent.com/6776067/209412387-bf696eba-ac44-4a62-a4c1-ec41b75ff4d8.png)](https://davidasbury.github.io/composite-map-usa/?featurelayer=c93f8a9f2a614ff8a31db732636eff9b&overview=67ab7f7c535c4687b6518e6d2343e8a2&views=ak,vi)


## Secondary layout

Use ``index2.html`` to see a second layout that shows Alaska and Hawaii (including the Northwestern Hawaiian Islands) at true scale. 

[Example showing Alaska at true scale](https://davidasbury.github.io/composite-map-usa/index2.html?featurelayer=c93f8a9f2a614ff8a31db732636eff9b&views=ak,hi,pr)

[![Screenshot 2022-12-23 at 3 11 11 PM](https://user-images.githubusercontent.com/6776067/209412636-049e2b05-6c73-4118-8192-0d47b94bb032.png)](https://davidasbury.github.io/composite-map-usa/index2.html?featurelayer=c93f8a9f2a614ff8a31db732636eff9b&views=ak,hi,pr)

