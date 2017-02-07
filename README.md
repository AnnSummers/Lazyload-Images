# Lazyload-Images
Responsive Image Lazyloader

## How does it work?

Lazyload runs through the following workflow:

1. lookup **placeholder elements**
2. replace **placeholders** with transparent images
3. update `src` attribute for each image and assign the best quality/size ratio URL

Finally, it will lazy load images to speed up page load time even further.

## Using

```html
<div style="width: 240px">
    <div class="delayed-image-load" data-src="http://placehold.it/{width}" data-alt="alternative text"></div>
</div>

<script>
    new Imager({ availableWidths: [200, 260, 320, 600] });
</script>
```

This will result in the following HTML output:

```html
<div style="width: 240px">
    <img src="http://placehold.it/260" data-src="http://placehold.it/{width}" alt="alternative text" class="image-replace">
</div>

<script>
    new Imager({ availableWidths: [200, 260, 320, 600] });
</script>
```

`260` has been elected as the best available width (as it is the closest upper size relative to `240` pixels).

### Passing a collection of elements

You might want to pass a NodeList or an array of **placeholder elements** as the first argument rather than a class selector.

```html
<div style="width: 240px">
    <div class="delayed-image-load" data-src="http://placehold.it/{width}" data-alt="alternative text"></div>
</div>

<script>
    var placeholderElems = document.querySelectorAll('.delayed-image-load');
    var imgrPlaceholder = new Imager(placeholderElems, {
        availableWidths: [200, 260, 320, 600]
    });
</script>
```

This will result in the following HTML output:

```html
<div style="width: 240px">
    <img src="http://placehold.it/260" data-src="http://placehold.it/{width}" alt="alternative text" class="image-replace">
</div>
```

# Credit
Much of this work is based on [BBC News Imager](https://github.com/BBC-News/Imager.js)
