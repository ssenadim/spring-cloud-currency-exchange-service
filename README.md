# spring-cloud-currency-exchange-service

---
# Readme Note 1
Test URL        : http://localhost:8000/currency-exchange/from/USD/to/TRY

PROBLEM > ERROR 10068 --- [  restartedMain] o.s.boot.SpringApplication               : Application run failed
SOLVE   > spring.jpa.defer-datasource-initialization=true
---