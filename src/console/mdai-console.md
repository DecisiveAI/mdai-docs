# The MyDecisive Engine Console

<!-- toc -->

## Introduction

The console is a web application that lives within your MDAI Engine that gives you an at-a-glance display of all of the telemetry data that has flowed through your MDAI Engine for the last hour.

## Data flow overview

<div style="text-align: center">
<img src="../media/console-data-flow.png" alt="The MDAI Engine Console showing data flows" style="width: 600px" />
</div>

The data flow overview provides a glanceable display of relative volumes of data flowing from receivers to exporters, divided by data type. Data flows are displayed in terms of counts of each data type (e.g., log messages) as reported by the OpenTelemetry collectors inside your engine.

In this view, the widest lines indicate greater data flow relative to narrower lines representing less. Striped lines indicate data flow errors, such as messages refused by the collector due to capacity constraints or messages dropped due to issues with a connected systems.

### Filters

<div style="text-align: center">
<img src="../media/console-filters.png" alt="The MDAI Engine Console with filter controls highlighted" style="width: 600px" />
</div>

The filters located in the top-right of the console view allow you to constrain the data flow and pipelines view to specific components or data types. These filters can be combined to reduce your view to specific components you wish to see.

#### Top Talkers and Top Listeners

The Top Talkers filter will show only the top three receivers by data volume, and the Top Listeners filter will show only the top three receivers by data volume.

#### More filters

The More Filters menu will allow you to filter your view by receiver, processor, data type or exporter.

## Pipelines overview

<div style="text-align: center">
<img src="../media/console-pipelines.png" alt="The MDAI Engine Console showing pipeline configuration" style="width: 600px" />
</div>

The pipelines view offers a graphical and textual view of the pipeline configurations running on your engine's collectors. Clicking on any component of this view will filter the view to components and data types that interact with that component, and will highlight that component's configuration in the textual configuration view

<div style="text-align: center">
<img src="../media/console-viz-mode.png" alt="The MDAI Engine Console with pipelines mode switch highlighted" style="width: 600px" />
</div>

The pipelines overview mode can be toggled via the highlighted control above, or by clicking any of the data types in the data flow view.

### Configuration view

This panel displays the yaml pipeline configuration running on your engine's collectors.

## Data reduction and total data flow summary sidebar

The console sidebar displays a count of receivers, pipelines and exporters running on your collectors, and the total volume of data flowing through them for the last hour.

> Note: Traffic flowing to `debug` exporters are not counted in data flow totals
