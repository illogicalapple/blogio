css vh bugs
they don't work well
illogicalapple
---
You've probably used the "vh" css unit before. Guess what? It's buggy.
When you're using it on Chrome on a mobile device, it gets covered by the navigation bar.
Oh no.
You don't want this to happen.
If you make a `<div>` with `100vh` for whatever reason, it will force the body to scroll.
You probably don't want that.
Here's how to fix it!
```javascript
function onResize() {
	document.body.style.setProperty("--height", window.innerHeight); // doesn't support IE, Baidu Mini, or QQ Browser
	// OR:
	document.querySelectorAll(".full-height").forEach(element => element.style.height = window.innerHeight); // should support all browsers
}
window.addEventListener("resize", onResize);
window.addEventListener("load", onResize);
```
```css
body {
	--height: 100vh; /* fallback */
}
.full-height {
	height: /* 100vh */ var(--height);
}
```
Wow! You have fixed it! Congratulations!
