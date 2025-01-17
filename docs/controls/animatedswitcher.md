---
title: AnimatedSwitcher
sidebar_label: AnimatedSwitcher
slug: animatedswitcher
---

A control that by default does a cross-fade between a new control and the control previously set on the AnimatedSwitcher as a `content`.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Examples

### Animated switching between two containers with scale effect

<img src="/img/docs/controls/animated-switcher/animated-switcher.gif" className="screenshot-20" />

<Tabs groupId="language">
  <TabItem value="python" label="Python" default>

```python
import flet
from flet import (
    AnimatedSwitcher,
    Container,
    ElevatedButton,
    Page,
    Text,
    alignment,
    colors,
)

def main(page: Page):

    c1 = Container(
        Text("Hello!", style="headlineMedium"),
        alignment=alignment.center,
        width=200,
        height=200,
        bgcolor=colors.GREEN,
    )
    c2 = Container(
        Text("Bye!", size=50),
        alignment=alignment.center,
        width=200,
        height=200,
        bgcolor=colors.YELLOW,
    )
    c = AnimatedSwitcher(
        c1,
        transition="scale",
        duration=500,
        reverse_duration=100,
        switch_in_curve="bounceOut",
        switch_out_curve="bounceIn",
    )

    def animate(e):
        c.content = c2 if c.content == c1 else c1
        c.update()

    page.add(
        c,
        ElevatedButton("Animate!", on_click=animate),
    )

flet.app(target=main)
```
  </TabItem>
</Tabs>

## Properties

### `duration`

The duration, in milliseconds, of the transition from the old `content` value to the new one. Default is `1000` milliseconds.

### `reverse_duration`

The duration, in milliseconds, of the transition from the new `content` value to the old one. Default is `1000` milliseconds.

### `switch_in_curve`

The animation curve to use when transitioning in a new `content`. See [Curves](https://api.flutter.dev/flutter/animation/Curves-class.html) in Flutter docs for possible values. Default is `linear`.

### `switch_out_curve`

The animation curve to use when transitioning a previous `content` out. See [Curves](https://api.flutter.dev/flutter/animation/Curves-class.html) in Flutter docs for possible values. Default is `linear`.

### `transition`

An animation type to transition between new and old `content`: `fade` (default), `rotation`, `scale`.