# Map

## What are SM Maps
A map is a simple SVG file. This means that you can easily modify it to match
the real building structure or the room layout.

The only requirements is that each computer is a `rect` with the following
properties are set:

- `class`: `computer`
- `id`: the hostname of the computer. Dots must be replace with underscores.
  (e.g. `r01p01_demo_sm_cri_epita_net`)

## Create or edit a map
Although not required, `inkscape` is recommended to design a map.

A simple `demo.svg` map is provided. It is recommended to edit it rather than
creating a map from scratch.

### Add a computer
Copying an existing computer with `inkscape` will provide every properties
required except `id`.

You may resize it if required.

### Resize and export
If your map renders properly only on `inkscape`, the `viewBox` might be invalid.

`inkscape` provides a way to export your work so that it fills the whole space
available. To do so, you have to export it using `Save As` > `Optimized SVG` and
check `Enable viewboxing`.
This will automatically resize the viewbox and provide a much more readable
(and shorted) output.

While this is great for production, the contributed maps MUST be on a format
easily editable. It does not matter if the `viewBox` is wrong as it will be
exported later for production.

## Links
Every maps (including `demo.svg` and `demo_optimized.svg`) are available on the
CRI's github: [here](https://github.com/epita/sm-maps-svg).
