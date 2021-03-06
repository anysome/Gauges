# Gauges
Gauges gives you a nice looking circular progress view.

![](https://github.com/ilyapuchka/Gauges/blob/master/example.png)

### Usage

You can customize almost every visual aspect of the view using `Gauge` struct .

```swift
struct Gauge {
    enum Color {
        case gradient([(color: UIColor, location: CGFloat)])
        case solid(UIColor)
    }

    enum Direction {
        case clockwise
        case counterClockwise
    }

    var value: Float
    var color: Color
    var radius: CGFloat
    var lineWidth: CGFloat
    var backgroundColor: Color
    var direction: Direction
    var startAngle: CGFloat

}

gaugeView.gauges = [
    Gauge(value: 0, color: .gradient([(.yellow, 0), (.orange, 1)]), radius: 60, lineWidth: 15),
    Gauge(value: 0, color: .gradient([(.cyan, 0), (.green, 1)]), radius: 90, lineWidth: 15),
    Gauge(value: 0, color: .gradient([(.blue, 0), (.magenta, 1)]), radius: 120, lineWidth: 15)
]
```

Additionally you can customize shadows with `Shadow` struct:

```swift
struct Shadow {
    enum Color {
        case colors([UIColor])
        case blur
    }

    var color: Color
    var offset: CGSize
    var opacity: CGFloat
    var radius: CGFloat
}

gaugeView.shadow = Shadow(color: .blur)
```

You can access and change values of each gauge individually:

```swift
gaugeView.gauges[0].value = 0.5
```

### Limitations

`UIVisualEffectView` was used for gradient shadow, which comes with some limitations:

  - everything that you put behind `GagueView` will be blurred, to avoid that set it an opaque background color
  - you can not change shadow radius after it was set for the first time when you use `.blur` shadow color
  - you may notice some color artifacts on the edges of `GaugeView` even if you use solid background color
  
  ### Used by
  
  [Aconta: income and expenses](https://itunes.apple.com/us/app/aconta-income-and-expenses/id1301129130?ls=1&mt=8)
