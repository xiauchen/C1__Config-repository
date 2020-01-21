```yaml
eureka:
  instance:
    instanceId=${spring.application.name}:${random.int}
    hostname: localhost
	lease-renewal-interval-in-seconds: 30
	lease-expiration-duration-in-seconds: 90
	metadataMap:
	  zone:shanghai
	prefer-ip-address: false
    non-secure-port: 80
    secure-port: 443
	non-secure-port-enabled: true
	secure-port-enabled: true
	appname: unknown
  client:
    enabled: true
	registry-fetch-interval-seconds: 30
	instance-info-replication-interval-seconds: 30
	initial-instance-info-replication-interval-seconds: 40
	eureka-service-url-poll-interval-seconds: 300
	eureka-server-read-timeout-seconds: 8
	eureka-server-total-connections: 200
	eureka-server-total-connections-per-host: 50
	eureka-connection-idle-timeout-seconds: 30
	heartbeat-executor-thread-pool-size: 2
	heartbeat-executor-exponential-back-off-bound: 10
	use-dns-for-fetching-service-urls: false
    register-with-eureka: false
	fetch-registry: false
	prefer-same-zone-eureka: true
	filter-only-up-instances: true
	serviceUrl:
	  defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
```