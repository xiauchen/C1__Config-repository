```yaml
#tomcat servelt1
server:
  tomcat:
    max-threads: 128
    min-spare-threads: 64
#spring-boot-undertow servelt2
  undertow:
    io-threads: 2
    worker-threads: 16
    buffer-seze: 8
    buffers-per-region: 10
    direct-buffers: 512
```
```yaml
spring:
  application:
    name: hello-service
  cloud:
    loadbalancer:
      retry:
        enabled: true
	cofig:
	  server:
	    git:
		  uri: http://git.xxxx.net/didispace/
		  username: qingxiao4@gmail.com
		  password: a9761008
		  uri: file://${user.home}/config-repo
		  search-paths: {application}
		  basedir:
		  repos:
		    dev:
			  pattern: dev/*
			  uri: file://home/git/config-repo
			test: http://git.xxx.xxx/test/config-repo
			prod:
			  pattern: prod/pp*,online/oo*
			  uri: http://git.xxx,xxx/prod/config-repo
		svn:
		  uri: svn://localhost:443/xxx/cofig-repo
		  username: qingxiao4@gmail.com
		  password: a9761008
		  basedir:
		health:
		  repositories:
		    check:
			  name: check-repo
			  label: master
			  profile: default
		overrides:
		  name: moon
		  from: shanghai
  datasource:
    username: moon
	password: {cipher}dba6505baa81d7808799d4429de499bf4c2053c05f029e7cfbf143695f5b
feign:
  compression:
    request:
	  enabled: true
	  mime-types: text/xml,application/xml,application/json
	  min-request-size: 2048
	response:
	  enabled: true
encrypy:
  key: fifispaces
  key-store:
    alias: config-server
	password: 111111
    secret: 222222
	location: config-server
```
```yaml
#自定參數
book.name=SpeingCloudInAction
#@Value("${book.name}")
#random
blog.value=${random.value}
blog.number=${random.int}
blog.bignumber=${random.long}
blog.test1=${random.int(10)}
blog.test2=${random.int(10,20)}
```
```bash
java -jar xxx.jar --spring.profiles.active=test
java -jar xxx.jar --spring.profiles.active=prod
```
```yaml
#actuator
/autoconfig
/beans
/configprops
/env
/mappings
/info
/metrics
/health
/dump
/trace
/shutdown
/refresh
```
```
@RestController
public class ConsumerController {
	@Autowired
	RestTemplate restTemplate;
	
	@RequestMapping(value = "/ribbon-comsumer",method = RequestMethod.GET)
	public String helloConsumer(){
		return restTemplate.getForEntity("http://hello-service/hello",String.class).getBody();
	}
}
```
```yaml
#zuul filter
ServletDetectionFilter ^-3
Servlet30WrapperFilter ^-2
FormBodyWrapperFilter ^-1
DebugFilter ^1
PreDecorationFilter ^5
#zuul route
RibbonRoutingFilter ^10
SimpleHostRoutingFilter ^100
SendForwardFilter ^500
#zuul post
SendErrorFilter ^0
SendResponseFilter ^1000
```
```
#config
/{application}/{profile}[/{label}]
/{application}-{profile}.yml
/{label}/{application}-{profile}
/{application}-{profile}.properties
/{label}/{application}-{profile}.properties
```