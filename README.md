# JLB (JavaScript Loader and Blocker)

Intends to replace the use of the ugly, non-performant &lt;script> tag with a flexible and performance-optimized alternative API.

For instance, the following "&lt;script> tag soup":

```html
<script src="http://remote.tld/jquery.js"></script>
<script src="local/plugin1.jquery.js"></script>
<script src="local/plugin2.jquery.js"></script>
<script src="local/init.js"></script>
<script>
  initMyPage();
</script>
```

With JLB it becomes:

```html
<script src="JLB.js"></script>
<script>
  $JLB
    .script("http://remote.tld/jquery.js")
    .wait()
    .script("/local/plugin1.jquery.js")
    .script("/local/plugin2.jquery.js")
    .wait()
    .script("/local/init.js")
    .wait(function () {
      initMyPage();
    });
</script>
```
