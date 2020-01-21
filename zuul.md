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
      path: /api-a-url/**
      serviceId: feign-comsumer
      strip-prefix:
      url: http://localhost:8080
      sensitive-headers:
      ignored-headers:
	  custom-sensitive-headers: true
	  sensitive-headers:
      retryable: false	  
  add-host-header: true
  prefix:
  strip-prefix:
  retryable: false
```
```yaml
#ribbon
[CommandKey]:
  ribbon:
ribbon:
  connect-timeout: 250
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
            max-concurrent-requests: 10
          timeout:
            enabled: true
          thread:
            interrupt-on-timeout: true
            interrupt-on-cancel: false
          strategy: THREAD/SEMAPHORE
      fallback:
        isolation:
          semaphore:
            max-concurrent-requests: 10
        enabled: true
	  circuit-breaker:
	    enabled: true
		sleep-window-in-milliseconds: 5000
		error-threshold-percentage: 50
		force-open: false
		force-closed: false
	  metrics:
	    rolling-stats:
		  time-in-milliseconds: 1000
		  num-buckets: 10
		rolling-percentile:
		  enabled: true
		  time-in-milliseconds: 60000
		  num-buckets: 6
		  bucket-size: 100
		health-snapshot:
		  interval-in-milliseconds: 500
	  request-cache:
	    enabled: true
	  request-log:
	    enabled: true
  collapser:
    [CommandKey]:
	  max-requests-in-batch: Integer.MAX_VALUE
	  timer-delay-in-milliseconds: 10
	  request-cache:
	    enabled: true
  threadpool:
    [CommandKey]:
	  core-size: 10
	  max-queue-size: -1
	  queue-size-rejection-threshold: 5
	  metrics:
	    rolling-stats:
		  time-in-milliseconds: 10000
		  num-buckets: 10
```