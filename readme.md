# The Controller Object


## Description

The `Controller` object is a single object that has named properties, some of which are functions.

The value of the `[[Prototype]]` internal property of the `Controller` object is the standard built-in `Object` prototype object (ES 15.2.4). The value of the `[[Class]]` internal property of the `Controller` object is "*Controller*".

The `Controller` object does not have a `[[Construct]]` internal property; it is not possible to use the `Controller` object as a constructor with the new operator.

The `Controller` object does not have a `[[Call]]` internal property; it is not possible to invoke the `Controller` object as a function.


## Value Properties of the Controller Object


 - ...


## Function Properties of the Controller Object

 - `getDevices()` Returns a `DeviceList` of active devices


```
interface Controller : Device {

	DeviceList getDevices();



	Event createEvent(DOMString eventInterfaceName);

};


```

Note:

"DeviceList" does not exist, but represents a hypothetical collection interface for a hypothetical "Device" interface:

```
interface DeviceList {

	getter Device? item(unsigned long index);

	readonly attribute unsigned long length;

	// ...
};

interface Device : EventTarget {

	readonly attribute unsigned long id;


	// Returns an object descriptor that represents the current state
	DOMStringMap queryState()



	// ...
};

```



```javascript

// Usage. Includes array methods from ES.next

var devices = Controller.getDevices();

devices == null; // true, as no "deviceconnect" event has fired on the window

// ...

// "deviceconnect" would fire as a result of either connecting the device or when the first "interact" event occurs

window.addEventListener( "deviceconnect", setupControllers, false );


function setupControllers() {

	var devices = Controller.getDevices();

	// devices == null; // false, the "deviceconnect" event has fired on the window


	// event listening...
	Array.from( devices ).forEach(function( device ) {

		device.addEventListener("interact", function( event ) {

			console.log( event, device.getState() );

		}, false );

	});

	// animation frame state query...
	function queryState() {

		requestAnimationFrame( queryState );

		var state = devices.item( 0 ).getState();

		doSomethingWithControllerState( state );

	}

	queryState();

}


```




# DOM Events

## Current

#### Events

 - **buttondown** (`MozJoyButtonDown`)
 - **buttonup** (`MozJoyButtonUp`)
 - **axismove** (`MozJoyAxisMove`)


## Propose

Implement new `UIEvent` interface: `DeviceEvent`

The DOM `DeviceEvent` represents events that occur as a result of the user interacting with a device (in this case, not a keyboard and not a mouse).

The event object of a `DeviceEvent` should provide a value property named `state` who's value is an object descriptor representing the complete state of the device.

The event object of a `DeviceEvent` should provide a value property named `type` who's value is a string that describes the event that occurred as result of of the user interacting with the device.

The event object of a `DeviceEvent` should provide a value property named `type` who's value is a string that describes the event that occurred as result of of the user interacting with the device.


#### Events

Device

 - **interact** Dispatched whenever the user interacts with the device
 - **connect**
 - **disconnect**

Window

 - **deviceconnect** Dispatched whenever a device is connected, or as first "interact" event



