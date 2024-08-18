# Alpine Js lesson

This repo contain notes from my first meet with alpine js.

You can follow this README to learn alpine like me

## Setup server

Start server

```bash
python -m http.server 8000
```

With `index.html` like this

```html
<script src="//unpkg.com/alpinejs" defer></script>

<div x-data="{ open: false }">
  <button @click="open = true">Expand</button>

  <span x-show="open"> Content... </span>
</div>
```

To hide content during loading you can add `style="display: none"` to content tag

## Webstorm support

For webstorm you can use plugin:

https://plugins.jetbrains.com/plugin/15251-alpine-js-support

## How to get rid style="display: none"

My first though to remove flickering was overriding style, but there is better way. Add style

```css
[x-cloak] {
  display: none;
}
```

Docs: https://alpinejs.dev/

### x-cloak

> Hide a block of HTML until after Alpine is finished initializing its contents

## x-on:click === @click

There is `@` that is shortcut form `x-on:`.

You can add also modifiers to listeners like this

```javascript
@keydown.window="if ($event.key === 'Escape') { open = false }"
```

## x-init

On mounted we using x-init, for example we can initialize x-data by fetch

```javascript
x-data="{ dogFact: '', id: '' }"
x-init="fetch('https://dogapi.dog/api/v2/facts')
    .then(response => response.json())
    .then(
        data => {
            dogFact = data.data[0].attributes.body
            id = data.data[0].id
        }
)"
```

and use these data binding them to title and content of another tag

```javascript
x-bind:title="id ? `Fact ID: ${id}` : ''"
x-text="dogFact"
```

## x-data as wrapper

Standalone

```html
<pre x-text="'ok'"></pre>
```

added in any place will not work, but if you wrap it by x-data

```html
<div x-data>
  <pre x-text="'ok'"></pre>
</div>
```

it will.

If you are using x-show it is recommended to add x-transition to make it smooth.

There as `x-text` and `x-html` that pasting content to elements.

15 Attributes:
x-data
x-bind
x-on
x-text
x-html
x-model
x-show
x-transition
x-for
x-if
x-init
x-effect
x-ref
x-cloak
x-ignore
6 Properties:
$store
$el
$dispatch
$watch
$refs
$nextTick
2 Methods:
Alpine.data
Alpine.store
