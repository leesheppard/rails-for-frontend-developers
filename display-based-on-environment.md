---
description: Rails.env.production? or Rails.env.development? or Rails.env.test?
---

# Display based on Environment

See [docs](http://apidock.com/rails/Rails/env/class) for further information.

```text
<% if Rails.env.development? %>
  <p>Dev Mode</p>
<% else %>
  <p>Production or test mode</p>
<% end %>
```

