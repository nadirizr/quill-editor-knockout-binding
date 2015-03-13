# quill-editor-knockout-binding
A knockout binding for the Quill Editor (https://github.com/quilljs/quill)

This is a plugin that allows you to bind a Quill Editor element with a Knockout observable for both text and HTML.

## Installation
`bower install ko-quill`

## Usage
This plugin allows to use the binding 'quill' to do one of the following:
- Bind to a single observable for the HTML content:
```html
<div data-bind="quill: htmlObservable">
</div>

<script>
  var model = { htmlObservable: ko.observable("<strong>Quill!</strong>") };
  ko.applyBindings(model);
</script>
```
- Bind to an object with several observables and settings:
```html
<div id="toolbar">
  <button class="ql-bold">Bold</button>
  <button class="ql-italic">Italic</button>
</div>
<div data-bind="quill: { html: htmlObservable,
                         text: textObservable,
                         toolbar: '#toolbar',
                         enable: enableObservable }">
</div>

<script>
  var model = { htmlObservable: ko.observable("<strong>Quill!</strong>"),
                textObservable: ko.observable(),  // htmlObservable supercedes textObservable.
                enableObservable: ko.observable(true) };
  ko.applyBindings(model);
</script>
```

## Quill Editor Parameters
There are several configurable parameters and observables when using the 'quill' binding:
- html: Either a string or an observable that will update the Quill Editor using the <a href="http://quilljs.com/docs/api/#quillprototypesethtml">setHTML</a> method.
- text: Either a string or an observable that will update the Quill Editor using the <a href="http://quilljs.com/docs/api/#quillprototypesettext">setText</a> method.
- toolbar: A selector for the toolbar element to use when initializing as documented <a href="http://quilljs.com/docs/modules/toolbar/">here</a>.
- enable: A boolean or an observable that will control whether the Quill Editor is enabled.

## Notes
- If you use both 'html' and 'text' observables, both are updated when changes
  are made in the editor, but only 'html' data changes will be reflected in the
  editor.
- If you use only a 'text' observable, changes to it will of course be reflected
  as usual in the editor.
