# Charty Documentation

Charty is an open-source charting library built with Jetpack Compose. The library focuses on simplicity and customization while supporting Kotlin Multiplatform (KMP). This guide gives a high-level overview of the available components and how to start using them in your project.

## Installation

Charty is available from Maven Central. Add the dependency to your module's `build.gradle.kts`:

```kotlin
dependencies {
    implementation("com.himanshoe:charty:<version>")
}
```

If you use [Version Catalog](https://docs.gradle.org/current/userguide/platforms.html#sub:version-catalogs), declare it in your `libs.versions.toml` and depend on `libs.charty`.

For multiplatform projects include the library in the `commonMain` source set:

```kotlin
sourceSets {
    commonMain.dependencies {
        implementation(libs.charty)
    }
}
```

Find the latest release on the [GitHub releases page](https://github.com/hi-manshu/Charty/releases).

## Available Chart Components

Charty provides several composable functions for common chart types:

- **BarChart / HorizontalBarChart** – vertical or horizontal bar charts for simple comparisons.
- **StackedBarChart** – stacked bars to represent multiple values per category.
- **LineChart / MultiLineChart** – single or multiple line series with optional filled areas and interaction tooltips.
- **LineBarChart / LineStackedBarChart** – hybrid charts that combine line and bar representations.
- **ComparisonBarChart** – side‑by‑side bars for comparing related metrics.
- **SignalProgressBarChart** – progress style bars that can be animated.
- **StorageBar** – a progress bar style chart useful for storage breakdowns.
- **PieChart** – pie or donut style charts with slice selection callbacks.
- **PointChart** – charts that display individual points.
- **CircleChart / SpeedometerProgressBar** – circular representations for gauges or progress.

Each composable exposes configuration objects for colors, axis labels and additional behaviour so you can tailor the charts to your design.

## Customization

### Colors

Colors are supplied through the `ChartColor` type. Use `Color.asSolidChartColor()` for a single color or `Color.asGradientChartColor()` / `List<Color>.asGradientChartColor()` for gradients:

```kotlin
import com.himanshoe.charty.common.asSolidChartColor
import com.himanshoe.charty.common.asGradientChartColor

val axisColor = Color.Gray.asSolidChartColor()
val lineGradient = listOf(Color(0xFFCB356B), Color(0xFFBD3F32)).asGradientChartColor()
```

### Labels and Targets

`LabelConfig` lets you show axis labels and control their style. Many charts also support drawing a target line via `TargetConfig`:

```kotlin
val labelConfig = LabelConfig.default().copy(showXLabel = true, showYLabel = true)
val targetConfig = TargetConfig.default()
```

### Further Examples

The [docs/storage/StorageBar.md](storage/StorageBar.md) document shows an extended example of the `StorageBar` composable with usage code. The sample module inside this repository demonstrates the other charts in action.

## Contributing

Issues and pull requests are welcome! See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines on reporting problems, requesting features and submitting changes.

## License

Charty is distributed under the terms of the Apache 2.0 license. See [LICENSE.txt](../LICENSE.txt) for details.
