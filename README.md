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
 
    <span x-show="open">
        Content...
    </span>
</div>
```

To hide content during loading you can add `style="display: none"` to content tag
