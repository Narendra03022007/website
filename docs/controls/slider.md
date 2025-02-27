---
title: Slider
sidebar_label: Slider
slug: slider
---

A slider provides a visual indication of adjustable content, as well as the current setting in the total range of content.

Use a slider when you want people to set defined values (such as volume or brightness), or when people would benefit from instant feedback on the effect of setting changes.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Examples

[Live example](https://flet-controls-gallery.fly.dev/input/slider)

### Basic sliders

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page):
    page.add(
        ft.Text("Default slider:"),
        ft.Slider(),
        ft.Text("Default disabled slider:"),
        ft.Slider(disabled=True))

ft.app(target=main)
```
  </TabItem>
</Tabs>

### Sliders with values

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page):
    page.add(
        ft.Text("Slider with value:"),
        ft.Slider(value=0.3),
        ft.Text("Slider with a custom range and label:"),
        ft.Slider(min=0, max=100, divisions=10, label="{value}%"))

ft.app(target=main)
```
  </TabItem>
</Tabs>

<img src="/img/docs/controls/slider/slider-with-custom-content.gif" className="screenshot-30"/>

### Slider with `on_change` event

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet as ft

def main(page):

    def slider_changed(e):
        t.value = f"Slider changed to {e.control.value}"
        page.update()

    t = ft.Text()
    page.add(
        ft.Text("Slider with 'on_change' event:"),
        ft.Slider(min=0, max=100, divisions=10, label="{value}%", on_change=slider_changed), t)

ft.app(target=main)
```
  </TabItem>
</Tabs>

<img src="/img/docs/controls/slider/slider-with-change-event.gif" className="screenshot-30"/>

## Properties

### `active_color`

The [color](/docs/guides/python/colors) to use for the portion of the slider track that is active.

The "active" side of the slider is the side between the thumb and the minimum value.

### `adaptive`

If the value is `True`, an adaptive Slider is created based on whether the target platform is iOS or macOS.

On iOS and macOS, a [`CupertinoSlider`](/docs/controls/cupertinoslider), which has matching functionality and presentation as `Slider`, and are the graphics expected on iOS. On other platforms, this creates a Material Slider.

The default value is `False`.

### `autofocus`

True if the control will be selected as the initial focus. If there is more than one control on a page with autofocus set, then the first one added to the page will get focus.

### `divisions`

The number of discrete divisions.

Typically used with `label` to show the current discrete value.

If not set, the slider is continuous.

### `inactive_color`

The [color](/docs/guides/python/colors) for the inactive portion of the slider track.

The "inactive" side of the slider is the side between the thumb and the maximum value.

### `label`

Format with `{value}`.

A label to show above the slider when the slider is active. The value of `label` may contain `{value}` which will be replaced with a current slider value.

It is used to display the value of a discrete slider, and it is displayed as part of the value indicator shape.

If not set, then the value indicator will not be displayed.

### `max`

The maximum value the user can select.

Defaults to `1.0`. Must be greater than or equal to `min`.

If the `max` is equal to the `min`, then the slider is disabled.

### `min`

The minimum value the user can select.

Defaults to `0.0`. Must be less than or equal to `max`.

If the `max` is equal to the `min`, then the slider is disabled.

### `round`

The number of decimals displayed on the `label` containing `value`. The default is 0 (displays value rounded to the nearest integer).

### `thumb_color`

The [color](/docs/guides/python/colors) of the thumb.

### `value`

The currently selected value for this slider.

The slider's thumb is drawn at a position that corresponds to this value.

## Events

### `on_blur`

Fires when the control has lost focus.

### `on_change`

Fires when the state of the Slider is changed.

### `on_change_end`

Fires when the user is done selecting a new value for the slider.

### `on_change_start`

Fires when the user starts selecting a new value for the slider.

### `on_focus`

Fires when the control has received focus.