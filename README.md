Talkie Leaflet/Mapbox example
===========

A simple Leaflet example using Talkie, an open source library by http://kiln.it. Full Talkie library and documentation here: http://kiln.it/talkie/

To see our example live, visit http://nicholasgunner.com/talkie-leaflet

## Usage

Include Leaflet. For this example, we'll use mapbox.js which includes Leaflet:

	<script src='mapbox-dist/mapbox.js'></script>
	<link href='mapbox-dist/mapbox.css' rel='stylesheet' />

Include the Talkie library:

	<link rel="stylesheet" type="text/css" href="http://kiln.it/talkie/ui/1.0/talkie.css">
	<script src="http://kiln.it/talkie-1.3.min.js"></script>

Include talkie-leaflet:

	<script src="talkie-leaflet.js"></script>
	
Add audio player to the body of your page:

    <div id="controls"></div>
    <audio id="soundtrack" controls="controls">
      <source src="your-audio.ogg" type="audio/ogg">
      <source src="your-audio.mp3" type="audio/mpeg">
    </audio>

Initialize Leaflet, hook up talkie-leaflet, build the timeline, and include optional functionality:

    <script>
      /* Initialise Leaflet */
      var map = L.mapbox.map("map", "examples.map-i86nkdio")
        .setView([42.44, -79.33], 9);

      /* Hook up the Talkie integration to our map */
      var tl = TalkieLeaflet(map);

      /* Talkie timeline config */
      var timeline = Talkie.timeline("#soundtrack", {
        "00:18": tl.setView([40.7298, -74.0027], 13), // New York city
        "00:22": tl.setView([42.8963, -78.8822], 12), // Buffalo
        "00:26": tl.setView([-41.112, -188.767], 6),  // New Zealand
        "00:29": tl.setView([42.8963, -78.8822], 12), // Buffalo
        "00:32": tl.setView([42.44, -79.33], 17)      // Fredonia
      });

      // Tell TalkieLeaflet that we want to revert user changes to the map view
      //
      // If we don’t call this, then the scripted setViews will still work but
      // user changes will not pause the timeline or be reverted.
       tl.undoViewChanges(timeline);
    </script>

## Now go tell amazing stories on maps!

Here's an amazing example usage!! - http://www.theguardian.com/world/ng-interactive/2014/aviation-100-years

Music credit: "Sidewalk Chalk" by Broke For Free (http://brokeforfree.com/)
