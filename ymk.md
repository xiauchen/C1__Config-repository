```yaml
#tomcat
server:
  tomcat:
    max-threads: 128
    min-spare-threads: 64
#spring-boot-undertow
  undertow:
    io-threads: 2
    worker-threads: 16
    buffer-seze: 8
    buffers-per-region: 10
    direct-buffers: 512
```
```yaml
#zuul
zuul:
  host:
    socket-timeout-millis: 100
    connect-timeout-millis: 100
    max-total-connections: 200
    max-per-route-connections: 20
  semphore:
    max-semaphores: 128
  eureka:
    [serviceId]:
      semaphore:
        max-semaphores: 128
  routes:
    customers: /customers/**
    [serviceId]
      path:
      serviceId:
      strip-prefix:
      url:
      sensitive-headers:
      ignored-headers:
  prefix:
  strip-prefix:

```
```yaml
#ribbon
ribbon:
  eager-load:
    enabled: true
  max-auto-retries: 1
  max-auto-retries-next-server: 1
  ok-to-retry-on-all-operations: true
  server-list-refresh-interval: 2000
  connect-timeout: 3000
  read-timeout: 3000
  max-total-http-connections:
  max-connections-per-host:
```
```yaml
hystrix:
  command:
    [CommandKey]:
      execution:
        isolation:
          thread:
            timeout-in-milliseconds: 1000
          semaphore:
            max-concurrent-requests: 100
          timeout:
            enabled: true
          thread:
            interrupt-on-timeout: true
            interrupt-on-cancel: false
          strategy: THREAD
      fallback:
        isolation:
          semaphore:
            max-concurrent-requests: 10
        enabled: true
```
```yaml
spring:
  cloud:
    loadbalancer:
      retry:
        enabled: true
```
