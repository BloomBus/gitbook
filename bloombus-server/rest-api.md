# REST API

{% api-method method="get" host="https://bloombus.bloomu.edu" path="/api/download/stops/geojson" %}
{% api-method-summary %}
Download Stops GeoJSON
{% endapi-method-summary %}

{% api-method-description %}
Retrieves the current state of the GeoJSON representing the geometry of shuttle stops from the Firebase Realtime Database. Since it is not stored in Firebase as proper GeoJSON \(features residing within a FeatureCollection\) the data is massaged within this service before it is sent to the client.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Stops GeoJSON successfully retrieved.
{% endapi-method-response-example-description %}

{% code title="stops-2019-05-26.geojson" %}
```javascript
{
  "type": "FeatureCollection",
  "features": [
    {
      "geometry": {
        "coordinates": [
          -76.449313,
          41.00196
        ],
        "type": "Point"
      },
      "properties": {
        "name": "Corner East/5th",
        "stopKey": "cornerEast5th"
      },
      "type": "Feature"
    },
    ...
  ]
}
```
{% endcode %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "message": "Error retrieving stops GeoJSON."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://bloombus.bloomu.edu" path="/api/download/loops/geojson" %}
{% api-method-summary %}
Download Loops GeoJSON
{% endapi-method-summary %}

{% api-method-description %}
Retrieves the current state of the GeoJSON representing the geometry of shuttle loops from the Firebase Realtime Database.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Loops GeoJSON successfully retrieved.
{% endapi-method-response-example-description %}

{% code title="loops-2019-05-26.geojson" %}
```
{
  "crs": {
    "properties": {
      "name": "EPSG:4326"
    },
    "type": "name"
  },
  "features": [
    {
      "geometry": {
        "coordinates": [
          [
            -76.44382211899995,
            41.01081362700006
          ],
          [
            -76.44447165999998,
            41.01080468400005
          ],
          [
            -76.44444118899997,
            41.00983172800005
          ],
          ...
        ],
        "type": "LineString"
      },
      "id": 1,
      "properties": {
        "color": "#33A3F4",
        "key": "campus",
        "name": "Campus Loop",
        "objectID": 1,
        "shapeLength": 0.03144377168231157,
        "stops": [
          "library",
          "nelsonFieldHouse",
          "jka",
          "orangeLot",
          "moa",
          "mpa"
        ]
      },
      "type": "Feature"
    },
    ...
  ],
  "type": "FeatureCollection"
}

```
{% endcode %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://bloombus.bloomu.edu" path="/api/upload/stops/geojson" %}
{% api-method-summary %}
Upload Stops GeoJSON
{% endapi-method-summary %}

{% api-method-description %}
Parses GeoJSON representing the geometry of shuttle stops and updates the `/stops` reference in the Firebase Realtime Database with this GeoJSON. Since the GeoJSON is meant to be stored in the Firebase Realtime Database under the `/stops` reference as key-value pairs of each stop's key string to a GeoJSON Feature object, the previously valid GeoJSON provided in the uploaded file will be massaged into this format.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
multipart/form-data
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="stops-geojson" type="object" required=true %}
The File object provided by an HTML `<input type="file/>`.
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successfully updated stops GeoJSON.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://bloombus.bloomu.edu" path="/api/upload/loops/geojson" %}
{% api-method-summary %}
Upload Loops GeoJSON
{% endapi-method-summary %}

{% api-method-description %}
Parses GeoJSON representing the geometry of shuttle loops and updates the `/loops` reference in the Firebase Realtime Database with this GeoJSON.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Content-Type" type="string" required=false %}
multipart/form-data
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="loops-geojson" type="object" required=false %}
The File object provided by an HTML `<input type="file/>`.
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successfully updated loops GeoJSON.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

