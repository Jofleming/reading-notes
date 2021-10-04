# 201 Reading 13 Local Storage

Data is stored in key/value pairs locally within the web client browser. This is similar to cookies but it is not transmitted to the remote web server.

Function to test for local storage:
```
function supports_html5_storage() {
  try {
    return 'localStorage' in window && window['localStorage'] !== null;
  } catch (e) {
    return false;
  }
}
```

the named key mentioned above is a string. The data can be any type supported by JS, but is stored as a string.
```
localStorage.setItem("key", value);

localStorage.getItem("key");
```
You use the set item to store something. You call it with the key. YOu can also overwrite data with the same key by just using the set command again with the same key.


[Back](README.md)