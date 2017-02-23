# jquery.modal
Simple, yet complex jQuery modal with used to extend and create advanced modal dialogs.


## Example

Will replace all `<a href="/fallback-no-js" data-modal="true" data-href="/modal/url">link</a>` with a modal.

```js
$p.modal.init();

$(document).on('click', 'a[data-modal="true"]', function(e) {
    e.preventDefault();

    // Cancel existing ajax-requests
    var xhr = $p.modal.getRequest();;
    if(xhr && xhr.readyState != 4){
        xhr.abort();
    }
    
    var url = $(this).data('href');
    var width = $(this).data('width');
    var height = $(this).data('height');

    if(url == null) {
        throw "Missing required data-parameter (href).";
    }

    $p.modal.setTitle('My title').setUrl(url).show();
});
```

## Callbacks

You can change callbacks easily by using the `$p.modal.bind()` function.

**Availible events:**

- **show:** triggers when `$p.modal.show` is triggered
- **load:** triggers when content is loading (return string to overwrite content-load).
- **closing:** triggers when modal is closing
- **closed:** triggers when modal is closed
- **center:** triggers when modal is being centered

**Example:**
```js
$p.modal.bind('load', function(modal, event) {
    
   return 'My custom modal content';
   
});
```
