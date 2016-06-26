[![Build Status](https://travis-ci.org/bootique/bootique-jooq.svg)](https://travis-ci.org/bootique/bootique-jooq)

# bootique-jooq

Integration of Jooq SQL builder with Bootique.

## Usage

Include ```bootique-jooq```:
```xml
<dependency>
	<groupId>io.bootique.jooq</groupId>
	<artifactId>bootique-jooq</artifactId>
</dependency>
```

Do whatever Jooq class generation is required (for now outside of bootique-jooq scope).

Create configuration with DB connection information and optional Jooq settings:
```yaml
jdbc:
  default:
      url: "jdbc:postgresql://192.168.99.100:5432/scheduling"
      initialSize: 1
      username: postgres
      password: postgres

jooq:
  dialect: POSTGRES
  executeLogging: true
```
Inject ```JooqFactory``` and start using Jooq:
```java
@Inject
private JooqFactory jooqFactory;

public void doSomething() {
	try (DSLContext c = jooqFactory.newContext()) {
	    Record r = c.select().from(Tables.MY_TABLE).fetchOne();
	}
}
```




