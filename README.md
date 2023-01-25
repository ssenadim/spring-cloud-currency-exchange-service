# spring-cloud-currency-exchange-service

---
# Readme Note 1
Test URL        : http://localhost:8000/currency-exchange/from/USD/to/TRY

PROBLEM > ERROR 10068 --- [  restartedMain] o.s.boot.SpringApplication               : Application run failed
SOLVE   > spring.jpa.defer-datasource-initialization=true
---

# Readme Note 2
Connecting currency conversion exchange microservice to eureka

        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
        </dependency>
        
        @EnableDiscoveryClient
        eureka.client.service-url.default-zone=http://localhost:8761/eureka
        Open http://localhost:8761/ and see this message
        CURRENCY-EXCHANGE-SERVICE 	n/a (1) 	(1) 	UP (1) - host.docker.internal:currency-exchange-service:8000
---

# Readme Note 3
OPEN BUG with spring-cloud-starter-netflix-eureka-client

It uses jackson-dataformat-xml.

Hence, you would see XML responses instead of JSON responses in the browser.

If you want to see JSON responses, you can add an exclusion for jackson-dataformat-xml dependency.

You need to make this change in 2 POM.XML files - Currency Exchange and Currency Conversion

    <dependency>
    	<groupId>org.springframework.cloud</groupId>
    	<artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
    	<exclusions>
    		<exclusion>
    			<groupId>com.fasterxml.jackson.dataformat</groupId>
    			<artifactId>jackson-dataformat-xml</artifactId>
    		</exclusion>
    	</exclusions>
    </dependency>
