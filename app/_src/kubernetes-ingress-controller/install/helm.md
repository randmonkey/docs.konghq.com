---
title: Install Kong Ingress Controller with Helm
type: how-to
purpose: |
  Using Helm to install KIC
---

{{ site.kic_product_name }} is installed using the [kong/ingress](https://github.com/Kong/charts/tree/main/charts/ingress) Helm chart.

The `kong/ingress` chart is a wrapper around `kong/kong` that manages separate {{ site.kic_product_name }} and {{ site.base_gateway }} deployments automatically.

You can use any of the [configuration options](https://github.com/Kong/charts/blob/main/charts/kong/README.md#configuration) available in the `kong/kong` chart when using the `kong/ingress` chart.

*  To configure the {{ site.kic_product_name }} deployment, place the keys from `kong/kong` under a `controller` key in the `values.yaml` file.

```yaml
controller:
  ingressController:
    image:
      repository: kong/kubernetes-ingress-controller
      tag: "{{ site.data.kong_latest_KIC.version }}"
```


*  To configure the {{ site.base_gateway }} deployment, place the keys from `kong/kong` under a `gateway` key in the `values.yaml` file.

```yaml
gateway:
  env:
    router_flavor: expressions
```

## Installation

{% include /md/kic/prerequisites.md release=page.release disable_accordian=true enable_oss=true %}
