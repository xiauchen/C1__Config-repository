```yaml
spring:
  rabbitmq:
    addresses: 127.0.0.1:5762
	cache:
	  channel:
	    checkout-timeout: 30000
		size: 500
	  connection:
	    mode: CHANNEL
		size: 20
	connection-timeout: 0
	dynamic: true
	host: localhost
	listener:
	  acknowledge-mode: 
	  auto-startup: true
	  concurrency: 1
	  default-requeue-rejected: true
	  max-concurrency:8
	  prefetch: 50
	  retry:
	    enabled: false
	    initial-interval: 1000
		max-attempts: 3
		max-interval: 10000
		multiplier: 1.0
		stateless: true
	  transaction-size: <spring.rabbitmq.listener.prefetch
    password:
	port: 5672
	publisher-confirms: false
	publisher-returns: false
	requeue-heartbeat: 10
	ssl:
	  enabled: false
	  key-store: file/addresses
	  key-store-password: {file/address}
	  trust-store:
	  trust-store-password:
	  algorithm:
	template:
	  mandatory: false
	  receive-timeout: 0
	  reply-timeout: 5000
	  retry:
	    enabled: false
		initial-interval: 1000
		max-attempts: 3
		max-interval: 10000
		multiplier: 1.0
	username:
	virtual-host:
```