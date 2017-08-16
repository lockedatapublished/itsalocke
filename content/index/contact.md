+++
#disable = true
weight = 90
title = "Contact us"
subtitle  = "Kick off a conversation about how we can help you."
lastmod = "2016-11-22"
date = "2016-11-22"
# The contact form uses www.formspree.io as default email proxy.
# Visitors can send up to a 1000 emails each month for free.
#
# What you need to do for the setup?
#
# - set your email address under 'email' below
# - upload the generated site to your server
# - send a dummy email yourself to confirm your account
# - click the confirm link in the email from www.formspree.io
# - you're done. Happy mailing!

# It is possible to substitute formspring with other providers.
# Example: Mailout plugin from caddy.
# Provide a URL to post to and add necessary custom javascript.
#postURL = "https://example.com/mailout/"

# Email can be set here or within config.toml.
# The email setting from config.toml takes precedent.
email = "consultancy@itsalocke.com"

button = "Send message"

[menu.main]
  name = "Contact"
  weight = 90
  url = "#contact"

# Fields and messages are only defined within this file.

# Overall success or error messages
[message]
  success = "Message sent. Someone will follow up in the next day or two."
  error = "Message could not be sent. Please contact us at info@itsalocke.com instead."

# Fields not defined are removed from the contact form.
[fields.name]
  text = "Your Name *"
  warning = "Please enter your name."

[fields.email]
  text = "Your Email *"
  warning = "Please enter your email address."

[fields.message]
  text = "Your Message *"
  warning = "Please enter a message."

# Add optional form fields to identify contact forms.
#[[fields.hidden]]
#  name = "someID"
#  value = "example.com"
#
#[[fields.hidden]]
# Special values for name such as "page" and "site" will be autofilled
#  name = "page"
+++
<!-- Calendly inline widget begin -->
<div class="calendly-inline-widget" data-url="https://calendly.com/lockedata" style="min-width:320px;height:580px;"></div>
<script type="text/javascript" src="https://calendly.com/assets/external/widget.js"></script>
<!-- Calendly inline widget end -->