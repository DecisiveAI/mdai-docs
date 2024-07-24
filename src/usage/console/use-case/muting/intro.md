# Telemetry Pipeline Manual Muting

*⚠️ This page assumes that you've already done the [installation process](../../../../install/installation.md) either locally or cloud-based. ⚠️*

## **TL;DR** 

**Tell me what I'm getting with Manual Mute**

<p>
  An MDAI Cluster provides the ability to mute by Metrics, Logs, and/or Trace data within OpenTelemetry telemetry pipelines. You can do this with our <a href="../../../../install/local/cli-install.md" target="_blank">CLI</a>, or from your MDAI Cluster's Console.
</p> 

----
<div class="right">
  ⏩ Skip ahead: <br /><br />
  <span><a href="./manual-cli.md">Mute with CLI</a></span><br />
  <span><a href="./manual-console.md">Mute with Console</a></span>
</div>


<br /><br />


## Telemetry Muting

One of our primary goals is to give back full-control of telemetry pipelines. Moving and storing data is expensive.. it doesn't have to be. Imagine a world where you only send data to observability vendors when you need to, i.e., coming up on an event (incident, spike in activity, etc). 

***📣 Introducing Manual Muting! 📣***

### What is Telemetry Muting? 

*Simple! Telemetry muting is the act of stopping data flow through a telemetry pipeline, period.*

Through our muting capability, you can create rules in your data pipelines that will help you stop/start data flow. These rules can be enabled or disabled on-demand, however, manually. We plan to continue building out this capability, so stay tuned for more updates.

### Why use Telemetry Muting?

**Cost Savings & Telemetry Control**

As we mentioned, it's very expensive to send data into and out of your technology envelope. Not only is it expensive, but not all data is high-priority data.

Manual muting affords you the ability to start and stop data flow and saving money by only sending the highest priority data per your definition. This can be achieved by: 

1. A [CLI command](https://github.com/DecisiveAI/mdai-cli/blob/main/docs/md/mdai_mute.md) to apply mute rules to your OTel pipelines 
2. Using the MDAI Console's [streamlined rule builder wizard](./manual-console.md) to apply mute rules to your OTel pipelines

*Note: Both of these options will work together, so you can choose what works best for you after experimenting.*

### ❗️Limited support❗️

Our first iteration of muting only allows you to mute by one or all of Metrics, Logs, and Trace based pipeline definitions. Don't worry, we're hard at work to expand the Telemetry Muting capability.


### Future Enhancements

Based on usage and adoption of this feature, we plan to expand the ability to have telemetry and cost controls.

If you have feedback or suggestions about the future of automute. 

* Email us at <a href="mailto:support@mydecisive.ai" target="_blank">support@mydecisive.ai</a>
* File an issue under the <a href="https://github.com/DecisiveAI/mdai-cli/issues/new" target="_blank">MDAI InkOps Project</a>

<br /><br />

----
<div class="left"><a href="../installation.md">⏪ Back to Installation</a></div>
<div class="right">
  Choose your adventure: <br /><br />
  <span><a href="./manual-cli.md">Mute with CLI</a></span><br />
  <span><a href="./manual-console.md">Mute with Console</a></span>
</div>