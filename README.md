# darkCSS4slack
CSS For Dark Theme on Slack 4.x

7-Zip must have libraries to support asar archives

`C:\Users\<USER_NAME>\AppData\Local\slack\app-4.0.0\resources`

1) Extract `ssb-interop.bundle.js`

2) add this at bottom of file:

```
// First make sure the wrapper app is loaded
document.addEventListener('DOMContentLoaded', function() {
  // Fetch our CSS in parallel ahead of time
  const cssPath = 'https://raw.githubusercontent.com/caiceA/slack-raw/master/slack-4';
  let cssPromise = fetch(cssPath).then((response) => response.text());

  // Insert a style tag into the wrapper view
  cssPromise.then((css) => {
    let s = document.createElement('style');
    s.type = 'text/css';
    s.innerHTML = css;
    document.head.appendChild(s);
  });
});
```

3) Open `app.asar` with 7-Zip. Remove `dist/ssb-interop.bundle.js`. Replaced with edited one.

4.) Restart Slack
