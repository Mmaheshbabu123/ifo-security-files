# Clickjacking Protection

This guide explains how to handle clickjacking issues using JavaScript to check if the current window is in an iframe and ensure it is loaded from the correct domain.
#FullCode
```javascript
  const getHostname = (url_link) => {
      try{
        let url = url_link.location.href;
      const matches = url.match(/^https?\:\/\/([^\/?#]+)(?:[\/?#]|$)/i);
  // extract hostname (will be null if no match is found)
  return matches && matches[1];
}catch(e){
  return 'localFile';
}
      // use URL constructor and return hostname

    }

    let top_url = getHostname(window.top);
    let self_url = getHostname(window.self);

    var turl = (window.location != window.parent.location) ? document.referrer : document.location.href;

    if(window.top != window.self){
      console.log('not matched');
    }
    var parent = $(window.frameElement).parent();

    if(top_url != null && top_url !== self_url){
return (
<div className = "unauthorisedAccess">
<h1>ACCESS DENIED</h1>
<hr></hr>
<h3>You are not authorised to access this url within the iframe</h3>
</div>
);
}
```
#Break down full code
## Steps

1. **Check if URL is included in the login URL:**

```javascript
const url_included = url.includes(window.loginurl);
```
2. Function to extract hostname from a URL:
```javascript
const getHostname = (url_link) => {
  try {
    let url = url_link.location.href;
    const matches = url.match(/^https?\:\/\/([^\/?#]+)(?:[\/?#]|$)/i);
    // extract hostname (will be null if no match is found)
    return matches && matches[1];
  } catch(e) {
    return 'localFile';
  }
  // use URL constructor and return hostname
}
```
3.Get hostname of the top window and self window:
```javascript
let top_url = getHostname(window.top);
let self_url = getHostname(window.self);
```
4.Check if the window is in an iframe and log a message if not matched:

```javascript
if(window.top != window.self){
  console.log('not matched');
}
```
5.Get the parent element of the iframe:
```javascript
var parent = $(window.frameElement).parent();
```
6.Check if the top window's URL is different from the self window's URL and show an access denied message if not authorized:

```javascript
if(top_url != null && top_url !== self_url){
  return (
    <div className="unauthorisedAccess">
      <h1>ACCESS DENIED</h1>
      <hr></hr>
      <h3>You are not authorised to access this URL within the iframe</h3>
    </div>
  );
}
```
Summary

This code helps in protecting against clickjacking by ensuring that the current window is not loaded within an unauthorized iframe. If the top window's URL is different from the self window's URL, it displays an "ACCESS DENIED" message.

You can copy this content and paste it into your README.md file. If you need assistance with committing this file to your repository or any further modifications, please let me know!

