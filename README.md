#dundee.js

Mechanism to track changes on objects using timestamps, flattened object 
structure and safe navigation.

```
var obj = { 
	test: "foo"
	and: {
		isRecursive: true,
		handlesArrays: [
			"yes",
			"flawlessly"
		],
		especially: [{
			id: "e8bcc871-a071-462a-b314-9c1cfa097426",
			text: "when objects with ids are involved"
		}]
	}
};

var proxyObj = new Dundee(obj);

proxyObj.get("test");
// > "foo"

proxyObj.set("test", "bar");
// > "bar"

// push
proxyObj.set("handlesArrays[]", )
// 

proxyObj.isChanged("test", Date.now());

// returns all timestamps
var allTracking = proxyObj.getTracking();

// returns timestamps for specified paths
var myTracking = proxyObj.getTracking([
	"and.isRecursive",
	"and.handlesArrays[0]",
	"and.especially[e8bcc871-a071-462a-b314-9c1cfa097426]"
]);

// have any values been updated?
proxyObj.isChanged(myTracking);

// is any sub-object modifications have occured
proxyObj.isChanged("and", Date.now());
```