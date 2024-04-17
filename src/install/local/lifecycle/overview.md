# MDAI Engine Life Cycle Management

## Overview

MDAI Engine lifecycle management involves post-creation operations to control the behavior and state of the components of each engine or the engine as a whole.

The common use cases for lifecycle management are highlighted below...
1. [Disable Engine Ingress](./disable.md) - Disable ingress to validate that data flow has stopped.
2. [Enable Engine Ingress](./enable.md) - Enable ingress to validate that data flow has been re-instantiated.
3. [Uninstall Engine](./destroy.md) - Destroy all artifacts associated with the MDAI Engine.


## 🚨 Important considerations for Life Cycle Management 🚨

* Ensure that you have the necessary permissions and access rights to perform these operations.
* Always review and test configurations before applying changes to avoid unintended consequences.
* Use caution when destroying a cluster, as it will permanently delete all associated resources.

----
<span class="left"><a href="/install/local/validate.md">⏪ Back to: Validate</a></span>
<span class="right"><a href="./disable-engine.md">Next Step: Disable the Engine ⏩</a></span>
