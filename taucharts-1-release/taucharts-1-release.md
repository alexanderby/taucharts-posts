# Taucharts One

Can you remind a **charting library** with **simple API**, **fresh looking** and **highly performant**? I can remind one, the **Taucharts One**. The latest stable **release 1.2.2** can be dowloaded via [npm](https://www.npmjs.com/package/taucharts).

Let's see what this new release comes with.

## Bar as span (Timeline) plugin

**Timeline** chart is suitable for visualizing teams **progress**.

![Timeline chart](taucharts-v1_timeline.png)

```javascript
const chart = new tauCharts.Chart({
    type: 'horizontal-bar',
    x: 'end',
    y: ['country', 'team'],
    color: 'team',
    label: 'team',
    plugins: [
        Taucharts.api.plugins.get('bar-as-span')({
            x0: 'start',
            collapse: true
        })
    ]),
    data: [
        {start: '2015-02-29', end: '2015-03-09', team: 'Real', country: 'Spain'},
        ...
    ]
});
```

## Crosshair plugin

It is now possible to **highlight** element values **on axes**.

![Crosshair plugin](taucharts-v1_crosshair.png)

```javascript
const chart = new tauCharts.Chart({
    ...
    plugins: [
        Taucharts.api.plugins.get('crosshair')()
    ])
});
```

## Legend plugin improvements

You can now **focus on a single element** or **toggle multiple elements** by clicking a color icon. Size and color gradient legents are now aligned horizontally to reduce consumed space. Highlighted elements will float over others.

![Crosshair plugin](taucharts-v1_legend.gif)

## Tooltip plugin improvements

Highlighting of elements on chart has never been so **fast** and simple. It is also possible to highlight points that overlap each other. After element **click** additional **buttons** will appear on tooltip.

![Crosshair plugin](taucharts-v1_tooltip.gif)

## Sparkline mode

When chart size is **too small** or ticks density is too large, it's better to hide chart axes and grid.

![Sparkline mode](taucharts-v1_sparkline.png)

```javascript
const chart = new tauCharts.Chart({
    ...
    settings: {
        // Axes are hidden when chart content
        // size is lower than these values
        minChartWidth: 300,
        minChartHeight: 200,
        minFacetWidth: 150,
        minFacetHeight: 100,
    }
});
```

## Line with size improvements

Line with **size** preserve it's width between points and now looks more consistent.

![Line with size](taucharts-v1_line-size.png)

```javascript
tauCharts.api.tickFormat.add('bugs-format', (x) => `${x} bugs`);
const chart = new tauCharts.Chart({
    type: 'line',
    x: 'Date',
    y: 'Effort',
    size: 'Bugs Count',     // Setup line size
    label: 'Bugs Count',
    color: 'Team',
    guide: {
        interpolate: 'smooth-keep-extremum',
        showGridLines: 'y',
        label: {
            tickFormat: 'bugs-format'
        }
    },
    plugins: [
        tauCharts.api.plugins.get('legend')(),
        tauCharts.api.plugins.get('quick-filter')(),
        tauCharts.api.plugins.get('tooltip')()
    ],
    settings: {
        utcTime: true
    },
    data: [
        {
            'Date': new Date('2015-07-01T00:00:00.000Z'),
            'Effort': 20,
            'Bugs Count': 4,
            'Team': 'Alaska'
        },
        ...
    ]
});
```

## Non-blocking rendering

Drawing of **Big Data** can be slow. To **prevent browser freeze**, several chart settings were introduced.

```javascript
settings: {
    asyncRendering: false,
    renderingTimeout: 10000,
    syncRenderingInterval: 50,
    handleRenderingErrors: true
}
```

Setting `asyncRendering: true` will make a chart **render asynchronously** by small synchronous chunks, making a browser **more responsive** to user interactions. Read more about asynchronous rendering [here](https://github.com/TargetProcess/taucharts-docs/blob/master/advanced/performance.md).

## TypeScript type definition

Taucharts NPM package comes with d.ts **type definitions** and this enables **code completion** in TypeScript or JavaScript files (if IDE supports this feature) without any additional setup.

![Taucharts code completion](taucharts-v1_code-completion.png)

## Underscore dependency removal

Thanks **[Juanjo Diaz](https://github.com/juanjoDiaz)** for **replacing Underscore** with modern native JavaScript features.

## And even more

There were innumerous count of **improvements** and bug fixes. You can see the whole list [here](https://github.com/TargetProcess/tauCharts/releases/tag/1.0.0). Some notable changes are:
- UTC time scale, periods and formats (`settings.utcTime: true|false`).
- Show line and area points (`guide.showAnchors: 'always'|'hover'|'never'`).
- Smooth line and area interpolation, that doesn't exceed data points (`guide.interpolate: 'smooth-keep-extremum'|'smooth'|'linear'|'step'|'step-before'|'step-after'`).
- Lowercase package name for CommonJS and AMD (`require('taucharts')`).

## Taucharts 2

**Taucharts v2** is about to be released, uses D3 v4 modules and brings **new features and improvements**.

![Diff Tooltip plugin](taucharts-v2_diff-tooltip.png)

