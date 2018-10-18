---
description: src/components/Home/Home.jsx
---

# Home.jsx

Home.jsx is the root of all logic for the application above the boilerplate layer. It manages the React state of the application, and propagates the state and actions for the state down to its lower components through props.  
At the time being, it is passed through props \(the classical way\) vs using React's Context API because the nesting structure of the application is shallow and when I attempted to use the Context API in this situation, it added lots of unnecessary complexity.

There are several important steps within the lifecycle of this component:

## componentDidMount\(\)

When the Home component is going to be mounted to the virtual DOM, the map must be prepared. This event happens after the Google Maps JavaScript API is loaded in the `<head>` of public/index.html, so a variable called `map` is attached to the `window` object by calling the `google.maps.Map()` constructor. In this constructor the `mapStyles` defined in `constants.js` is applied, which removes the many unnecessary map labels of local Points of Interest \(POIs\). 

The map is also set to the geographic extent defined by the `campusBounds` object in `constants.js`, which has coverage of both upper and lower campus.

Next, the Firebase API begins to be used, by attaching an event listener to the `shuttles` reference on the database, listening for both the `child_changed` and `value` events. At a high level, this should mean that the event listener is fired every time a shuttle node in the database is updated, either because it has updated its position, or the timestamp on the node is older than the timeout, so it has been reaped by BloomBus-Server. When the listener is called, the `shuttle` reference is iterated over \(each child represents a loop\) and the value is passed to `handleNewValue()`.

Next, the database reference is set to the `stations` ref, and the `.once()` method is called on this reference since we are only interested in constructing the state and map markers for these shuttles at the start of the application. They do not need to be continuously updated.

## componentDidUpdate\(\)

Whenever the state of Home is updated, if there is a currently selected map marker, then the map will be locked to be centered upon that marker.

## onStationSelect\(\), onShuttleSelect\(\)

These methods are action handlers that are passed as props to the StationsDrawer and ShuttlesDrawer components, respectively.

## handleNewValue\(\)

`handleNewValue()` is called any time a shuttle node in Firebase has been updated. The shuttle node has a key corresponding to the loop the shuttle is a child of, and this is used to reference the `shuttleMarkers` object to see if the shuttle already has a constructed map marker.

{% hint style="danger" %}
**Note:** This does not necessarily mean the map marker is **visible** if it already exists. Map markers for shuttle nodes with a stale timestamp are set to be invisible.
{% endhint %}

The shuttle node data that has been passed to `handleNewValue()` is set as the value of the corresponding loop key in `this.state.shuttleMarkers`, so that a rerender of the map's markers will be triggered and its new position will be shown, or the marker will be removed from the map.

