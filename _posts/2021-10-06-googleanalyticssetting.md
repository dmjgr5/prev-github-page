---
layout: post
title: Jekyll 기반 Github Page 의 Google Analytics 환경 설정하기
category: 05_Cloud
tag: [GoogleAnalytics]
---


![example](/assets/images/ga1.jpg)

> Jekyll 기반으로 된 Github page 를 구글 어날리틱스에서 조회할 수 있게 세팅하는 방법을 정리하고자 합니다.


----

설정은 간단하며 아래와 같이 각 파일에 세팅함으로서 실시간으로 접속자의 현황을 파악할 수 있습니다.
 
----

#### `_config.yml`


![example](/assets/images/ga2.jpg)

위의 측정ID를 참조하여 tracking_id 값에 넣어 세팅한다.

```

google_analytics:
  tracking_id: '측정ID'

```



#### `google_analytics.html` in `_includes` folder

```text

<script async src="https://www.googletagmanager.com/gtag/js?id={{ site.google_analytic.tracking_id }}"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', '{{ site.google_analytics.tracking_id }}');
</script>

```



#### `head.html` in `_includes` folder

```text

  {% if site.google_analytics != null %} 
  {% include google_analytics.html %}
  {% endif %}

```
 
---

### Google Analytics

- 아래와 같이 사용자 수 및 위치 등의 각종 현황을 확인할 수 있다.
 
![example](/assets/images/ga3.jpg)

![example](/assets/images/ga4.jpg)