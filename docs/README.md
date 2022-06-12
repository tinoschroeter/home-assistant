# home-assistant

## proxy configuration

```yaml
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 10.42.2.160
    - 10.0.1.100
    - 127.0.0.1
    - ::1
```
