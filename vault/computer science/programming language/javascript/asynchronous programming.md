>[mdn web docs: asynchronous javascript](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Async_JS)
---

javascript implements [[asynchronous]] programming with:
1. callbacks
2. promises

> callback should be avoided because it creates the **pyramid of doom**

# callbacks

a callback is a function that:
- expects a function as parameter (**callback function**)
- execute a long task in a different thread
- calls the callback function when appropriate

```javascript
function do(callback){
	// do something
	callback();
}
```

## pyramid of doom

```javascript
function doStep1(init, callback) {
  const result = init + 1;
  callback(result);
}

function doStep2(init, callback) {
  const result = init + 2;
  callback(result);
}

function doStep3(init, callback) {
  const result = init + 3;
  callback(result);
}

function doOperation() {
  doStep1(0, (result1) => {
    doStep2(result1, (result2) => {
      doStep3(result2, (result3) => {
        console.log(`result: ${result3}`);
      });
    });
  });
}

doOperation();
```
# promises
