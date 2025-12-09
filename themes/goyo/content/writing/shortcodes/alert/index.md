+++
title = "Alert"
weight = 1
+++

Display different types of alert messages to highlight important information, statuses, or warnings.

## Info

{% alert_info() %}
  Info alert
{% end %}

```jinja2
{%/* alert_info() */%}
  Info alert
{%/* end */%}
```

## Success

{% alert_success() %}
  Success alert
{% end %}

```jinja2
{%/* alert_success() */%}
  Success alert
{%/* end */%}
```

## Warning

{% alert_warning() %}
  Warning alert
{% end %}

```jinja2
{%/* alert_warning() */%}
  Warning alert
{%/* end */%}
```

## Error

{% alert_error() %}
  Error alert
{% end %}

```jinja2
{%/* alert_error() */%}
  Error alert
{%/* end */%}
```

## Styles

You can customize the alert style using the `style` parameter. Available styles are:
- `soft` (default)
- `outline`
- `dash`

### Soft (default)

{% alert_info(style="soft") %}
  Info alert with soft style
{% end %}

```jinja2
{%/* alert_info(style="soft") */%}
  Info alert with soft style
{%/* end */%}
```

### Outline

{% alert_info(style="outline") %}
  Info alert with outline style
{% end %}

{% alert_success(style="outline") %}
  Success alert with outline style
{% end %}

{% alert_warning(style="outline") %}
  Warning alert with outline style
{% end %}

{% alert_error(style="outline") %}
  Error alert with outline style
{% end %}

```jinja2
{%/* alert_info(style="outline") */%}
  Info alert with outline style
{%/* end */%}
```

### Dash

{% alert_info(style="dash") %}
  Info alert with dash style
{% end %}

{% alert_success(style="dash") %}
  Success alert with dash style
{% end %}

{% alert_warning(style="dash") %}
  Warning alert with dash style
{% end %}

{% alert_error(style="dash") %}
  Error alert with dash style
{% end %}

```jinja2
{%/* alert_info(style="dash") */%}
  Info alert with dash style
{%/* end */%}
```