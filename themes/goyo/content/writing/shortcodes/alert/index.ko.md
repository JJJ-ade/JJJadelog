+++
title = "Alert Box"
weight = 1
+++

다양한 유형의 알림 메시지를 표시하여 중요한 정보, 상태, 경고 등을 효과적으로 전달합니다.

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

## 스타일

`style` 파라미터를 사용하여 알림 스타일을 지정할 수 있습니다. 사용 가능한 스타일:
- `soft` (기본값)
- `outline`
- `dash`

### Soft (기본값)

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