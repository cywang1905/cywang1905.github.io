---
layout: post
title: "First Post"
categories: Test Description
---

需求：

- 静态配置依赖的服务允许通配

  - 不允许短配，必须5级域名

  - 通配

- 通过selector来选择服务

- 以上需要和动态依赖进行聚合，注意去重、性能

```yaml
apiVersion: microservice.slime.io/v1alpha1
kind: ServiceFence
metadata:
  name: productpage
  namespace: default
spec:
  enable: true
status:
  domains:
    details.default.svc.cluster.local:
      hosts:
      - details.default.svc.cluster.local
    reviews.default.svc.cluster.local:
      hosts:
      - reviews.default.svc.cluster.local
  metricStatus:
    '{destination_service="details.default.svc.cluster.local"}': "9"
    '{destination_service="reviews.default.svc.cluster.local"}': "24"
  visitor:
    default/ratings: true
```
