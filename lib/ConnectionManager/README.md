Plug.UPnP_ConnectionManager
============================

A Plug.UPnP Abstraction API for communicating specifically with a UPnP device obtained via the [W3C Network Service Discovery draft specification (4th October 2012 version)](http://www.w3.org/TR/2012/WD-discovery-api-20121004/).

__A general description of the Plug.Play library is available in the main [README](https://github.com/richtr/plug.play.js/blob/master/README.md) file available in the root of this repository.__

### Example Usage

The following example shows how to obtain and use a Plug.UPnP_ConnectionManager object. For [Step 1](https://github.com/richtr/plug.play.js/blob/master/README.md#step-1-obtaining-networkservice-objects) and [Step 2](https://github.com/richtr/plug.play.js/blob/master/README.md#step-2-creating-a-new-plug.upnp-object) please consult the main [README](https://github.com/richtr/plug.play.js/blob/master/README.md) file.

    var mediaConnection = new Plug.UPnP_ConnectionManager( service, { debug: false } );
    
    mediaConnection.getProtocolInfo().then(function(response) {
        
      if( response && response.data ) {
        debugLog( "Service[" + service._index + "] is reporting SOURCE=[" + response.data.Source + "]" );
        debugLog( "Service[" + service._index + "] is reporting SINK=[" + response.data.Sink + "]" );
      } else {
        debugLog( "Service[" + service._index + "] is reporting no response" );
      }

    }).then( null, function( error ) { // Handle any errors

      debugLog( "An error occurred with service[" + service._index + "]: " + error.description );

    });

You can see this code in action in [demo.html](https://github.com/richtr/plug.play.js/tree/master/lib/ConnectionManager/demo.html).

