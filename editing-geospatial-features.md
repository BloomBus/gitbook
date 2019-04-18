# Editing Geospatial Features

The spatial data for the BloomBus project \(the collections of points, lines and polygons that represent shuttle loops, shuttle stops, etc\) are stored in Firebase as GeoJSON. The shuttle loops are kept as a GeoJSON FeatureCollection at the `/shuttles` ref, and under the `/stops` ref there is a collection of keys that correspond to a shuttle stop with it's value being a GeoJSON Feature.

When this spatial needs to be edited, there are 2 options:  
If the edit is to be made on a point feature \(e.g. the shuttle stops\), the easiest method is probably to find the new Lat/Lng pair by using Google Maps/Google Earth \(both use the WGS84 coordinate system\), then log onto the Firebase Console, find the GeoJSON of the point and manually edit it's `geometry.coordinates` array, and any corresponding edits that need to be made to the `properties` object.

For the line features, there is less of a direct and easy way to edit these. Originally the features were imported into Firebase by exporting them as GeoJSON from ArcGIS Pro \(can be used in the GIS lab in Hartline B14\) but there is an extension for QGIS in the works that will pull the feature GeoJSON from Firebase, add the layers in QGIS \(free alternative to ArcGIS\), and then reupload the GeoJSON after edits have been made.

