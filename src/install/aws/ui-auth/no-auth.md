# 🌐 Public access (no authentication)
----

Long hair, don't care? Just want to test us out without auth on your Console? **NO PROBLEM!**

During setup you have the option to opt-out of the default [Cognito-based auth solution](./cognito.md) by setting your flag to `COGNITO=false` in the `aws.env` file. This will prevent any auth-related resources from being installed in your infrastructure in the future.

```bash
# An opt-in/out feature that enables auth on the Console UI app.
# Default should be true if you're unsure if you want this, please change to false.
# If you select false, ignore fields MDAI_UI_HOSTNAME and MDAI_UI_USER_POOL_DOMAIN
COGNITO=true

# Amazon Resource Name (ARN) of the certificate to be used for the Console endpoint (e.g., eu-west-2.yourdomain.dev)
MDAI_UI_HOSTNAME=

# The domain name to tie your auth to, e.g., 'example.com' would use 'example' here (e.g., yourdomain)
MDAI_UI_USER_POOL_DOMAIN=
```

## Some bad news...

Currently, we don't have steps to retroactively apply cognito if you change your mind, but with your feedback to [support@mydecisive.ai](mailto:support@mydecisive.ai) or by opening an [issue](https://github.com/DecisiveAI/mdai-inkops/issues/new), we'll prioritize these post-install flows for you!

----
<span class="left"><a href="../validate.md">⏪ Back to: Validate Installation</a></span>
<span class="right"><a href="../lifecycle/overview.md">Next Step: Lifecycle Overview ⏩</a></span>