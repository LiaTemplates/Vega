<!--
author:   André Dietrich

email:    LiaScript@web.de

version:  0.0.1

language: en

narrator: US English Male

comment:  This is a template for integrating Vega visualizations into LiaScript
          courses. For more information on Vega, visit the project website:
          https://vega.github.io/vega-lite/examples

script:   https://cdn.jsdelivr.net/npm/vega@5.9.0
          https://cdn.jsdelivr.net/npm/vega-lite@4.0.2
          https://cdn.jsdelivr.net/npm/vega-embed@6.2.1

@Vega.exec: @Vega.exec_(@uid)

@Vega.exec_
<script>
  let vlSpec = @input
  vegaEmbed('#vis@0', vlSpec);
  "LIA: stop"
</script>

<div id="vis@0"></div>

@end

@Vega.run: @Vega.run_(@uid,```@0```)

@Vega.run_
<div id="vis@0"></div>

<script>
  setTimeout(function(e) {
    let vlSpec = @1
    vegaEmbed('#vis@0', vlSpec)
  }, 1000);
</script>

@end
-->

# Vega - Template

                         --{{0}}--
This is a template for integrating Vega visualizations into
[LiaScript](https://liascript.github.io) courses. See the following links for
further information and documentation:

                          {{0-1}}
* See the Vega docs [here...](https://vega.github.io/vega-lite/example)
* See the Github version of this document
  [here...](https://github.com/liaTemplates/vega)
* See the LiaScript version of this document
  [here...](https://liascript.github.io/course/?https://raw.githubusercontent.com/liaTemplates/vega/master/README.md)


                         --{{1}}--
There are three ways to use this template. The easiest way is to use the
`import` statement and the URL of the raw text-file of the master branch or any
other branch or version. But you can also copy the required functionality
directly into the header of your Markdown document, see therefor the
[last slide](#4). And of course, you could also clone this project and change
it, as you wish.

                           {{1}}
1. Load the macros via

   `import: https://raw.githubusercontent.com/liaTemplates/vega/master/README.md`

2. Copy the definitions into your Project

3. Clone this repository on GitHub


## `@Vega.exec`

                         --{{0}}--
Simply call the macro `@Vega.exec` below your JSON snippet to make the code
directly executable and editable:


```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
  "data": {"url": "https://vega.github.io/vega-lite/examples/data/seattle-weather.csv"},
  "mark": "tick",
  "encoding": {
    "x": {"field": "precipitation", "type": "quantitative"}
  }
}
```
@Vega.exec

---

```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
  "data": {
    "values": [
      {"a": "C", "b": 2},
      {"a": "C", "b": 7},
      {"a": "C", "b": 4},
      {"a": "D", "b": 1},
      {"a": "D", "b": 2},
      {"a": "D", "b": 6},
      {"a": "E", "b": 8},
      {"a": "E", "b": 4},
      {"a": "E", "b": 7}
    ]
  },
  "mark": "bar",
  "encoding": {
    "y": {"field": "a", "type": "nominal"},
    "x": {
      "aggregate": "average",
      "field": "b",
      "type": "quantitative",
      "axis": {
        "title": "Average of b"
      }
    }
  }
}
```
@Vega.exec


## `@Vega.run`

                         --{{0}}--
Use `@Vega.run` to immediately render your JSON snippet, without showing its
content to the user. Therefor, simply the macro to the head of your Markdown
snippet.


```json @Vega.run
{
  "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
  "data": {"url": "https://vega.github.io/vega-lite/examples/data/seattle-weather.csv"},
  "mark": "tick",
  "encoding": {
    "x": {"field": "precipitation", "type": "quantitative"}
  }
}
```

---

```json @Vega.run
{
  "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
  "data": {
    "values": [
      {"a": "C", "b": 2},
      {"a": "C", "b": 7},
      {"a": "C", "b": 4},
      {"a": "D", "b": 1},
      {"a": "D", "b": 2},
      {"a": "D", "b": 6},
      {"a": "E", "b": 8},
      {"a": "E", "b": 4},
      {"a": "E", "b": 7}
    ]
  },
  "mark": "bar",
  "encoding": {
    "y": {"field": "a", "type": "nominal"},
    "x": {
      "aggregate": "average",
      "field": "b",
      "type": "quantitative",
      "axis": {
        "title": "Average of b"
      }
    }
  }
}
```

## Implementation

                         --{{0}}--
The delay is currently required, to deal with the loading delay of the all
JavaScript files. This will be fixed in the next version of LiaScript.

````html
script:   https://cdn.jsdelivr.net/npm/vega@5.9.0
          https://cdn.jsdelivr.net/npm/vega-lite@4.0.2
          https://cdn.jsdelivr.net/npm/vega-embed@6.2.1

@Vega.exec: @Vega.exec_(@uid)

@Vega.exec_
<script>
  let vlSpec = @input
  vegaEmbed('#vis@0', vlSpec);
  "LIA: stop"
</script>

<div id="vis@0"></div>

@end

@Vega.run: @Vega.run_(@uid,```@0```)

@Vega.run_
<div id="vis@0"></div>

<script>
  setTimeout(function(e) {
    let vlSpec = @1
    vegaEmbed('#vis@0', vlSpec)
  }, 1000);
</script>

@end
````

                         --{{1}}--
If you want to minimize loading effort in your LiaScript project, you can also
copy this code and paste it into your main comment header, see the code in the
raw file of this document.

{{1}} https://raw.githubusercontent.com/liaTemplates/vega/master/README.md
