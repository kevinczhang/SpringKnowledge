---
description: >-
  Spring Data makes it easier to create Spring driven applications that use new
  ways to access data, such as non-relational databases, map-reduction
  frameworks, cloud services, as well as well-advanced
---

# Spring Data JPA

## Core concepts:

1. Entity class
2. Hibernate entity manager
3. Data source
4. Transaction manager

`spring-data-jpa`, `hibernate-entitymanager`: for Spring Data JPA and [Hibernate](https://www.journaldev.com/3793/hibernate-tutorial) support.

```java
@Configuration
@EnableTransactionManagement
@EnableJpaRepositories("com.journaldev.spring.repository")
@PropertySource("classpath:database.properties")
public class DataConfig {

	private final String PROPERTY_DRIVER = "driver";
	private final String PROPERTY_URL = "url";
	private final String PROPERTY_USERNAME = "user";
	private final String PROPERTY_PASSWORD = "password";
	private final String PROPERTY_SHOW_SQL = "hibernate.show_sql";
	private final String PROPERTY_DIALECT = "hibernate.dialect";

	@Autowired
	Environment environment;

	@Bean
	LocalContainerEntityManagerFactoryBean entityManagerFactory() {
		LocalContainerEntityManagerFactoryBean lfb = new LocalContainerEntityManagerFactoryBean();
		lfb.setDataSource(dataSource());
		lfb.setPersistenceProviderClass(HibernatePersistence.class);
		lfb.setPackagesToScan("com.journaldev.spring.model");
		lfb.setJpaProperties(hibernateProps());
		return lfb;
	}

	@Bean
	DataSource dataSource() {
		DriverManagerDataSource ds = new DriverManagerDataSource();
		ds.setUrl(environment.getProperty(PROPERTY_URL));
		ds.setUsername(environment.getProperty(PROPERTY_USERNAME));
		ds.setPassword(environment.getProperty(PROPERTY_PASSWORD));
		ds.setDriverClassName(environment.getProperty(PROPERTY_DRIVER));
		return ds;
	}

	Properties hibernateProps() {
		Properties properties = new Properties();
		properties.setProperty(PROPERTY_DIALECT, environment.getProperty(PROPERTY_DIALECT));
		properties.setProperty(PROPERTY_SHOW_SQL, environment.getProperty(PROPERTY_SHOW_SQL));
		return properties;
	}

	@Bean
	JpaTransactionManager transactionManager() {
		JpaTransactionManager transactionManager = new JpaTransactionManager();
		transactionManager.setEntityManagerFactory(entityManagerFactory().getObject());
		return transactionManager;
	}
}
```

* `@Configuration`: this [spring annotation](https://www.journaldev.com/16966/spring-annotations) says that it is configuration class.
* `@EnableTransactionManagement`: this annotation allows users to use transaction management in application.
* `@EnableJpaRepositories("com.journaldev.spring.repository")`: indicates where the repositories classes are present.
* `@PropertySource("classpath:database.properties")`: says that we have property file in our classpath. The values from this file will be injected into environment variable. The contents of the database.properties file are shown below.

```yaml
driver=org.postgresql.Driver
url=jdbc:postgresql://127.0.0.1:5432/postgres
user=postgres
password=postgres

hibernate.dialect=org.hibernate.dialect.PostgreSQL82Dialect
hibernate.show_sql=true
```

## Annotations for Entity class

* @Entity: This annotation allows entity manager to use this class and puts it in context.
* @Table\(name = “people”\): associates a class with a table in the database.
* `@Id`: says that this field is the primary key.
* `@GeneratedValue(strategy = GenerationType.IDENTITY)`: Defines the strategy for generating the primary key.
* `@Column(name = "age")`: denotes a column in the database with which this field will be associated.

## JPA Repository

```java
public interface PersonRepository<P> extends CrudRepository<Person, Long> {
    List<Person> findByFirstName(String firstName);
}
```

By inheriting from `CrudRepository`, we can call many methods without the need to implement them ourself. Some of these methods are:

* save
* findOne
* exists
* findAll
* count
* delete
* deleteAll

## Service class

```java
@Service
public class PersonService {

	@Autowired
	PersonRepository<Person> personRepository;

	@Transactional
	public List<Person> getAllPersons() {
		return (List<Person>) personRepository.findAll();
	}

	@Transactional
	public List<Person> findByName(String name) {
		return personRepository.findByFirstName(name);
	}

	@Transactional
	public Person getById(Long id) {
		return personRepository.findOne(id);
	}

	@Transactional
	public void deletePerson(Long personId) {
		personRepository.delete(personId);
	}

	@Transactional
	public boolean addPerson(Person person) {
		return personRepository.save(person) != null;
	}

	@Transactional
	public boolean updatePerson(Person person) {
		return personRepository.save(person) != null;
	}
}
```

 `@Transactional` annotation indicates that the method will be executed in the transaction. Spring will take care of transaction management.

