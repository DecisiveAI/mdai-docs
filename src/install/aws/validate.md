## Validate data flow

1. From the last step in [Verify](./verify.md), you should've found your Console UI Load Balance link. Please visit that URL to view your pipeline configuration and dataflow.
2. As telemetry flows through the engine, you will see counts increase in the console, color-coded by telemetry type. 🐙🎉

![The MDAI Engine Console showing pipeline composition and data flow](../../media/console-data-flow.png)

> Note: Data flowing to `debug` exporters are not counted towards data flow totals in the right sidebar


----
<span class="left"><a href="./verify.md">⏪ Back to: Verify</a></span>
<span class="right"><a href="./ui-auth.md">Next Step: UI Auth (Cognito) ⏩</a></span>


{{#include ./footer.md}}