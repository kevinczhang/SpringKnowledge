---
description: 一个Batch(批处理)过程由一个Job(作业)组成。这个实体封装了整个批处理过程。
---

# Spring Batch

一个Job\(作业\)可以由一个或多个Step\(步骤\)组成。在大多数情况下，一个步骤将读取数据\(通过ItemReader\)，处理数据\(使用ItemProcessor\)，然后写入数据\(通过ItemWriter\)。

JobLauncher处理启动一个Job\(作业\)。

最后，JobRepository存储关于配置和执行的Job\(作业\)的元数据。

Spring Batch provides a physical implementation of the layers, components, and technical services commonly found in the robust, maintainable systems that are used to address the creation of simple to complex batch applications, with the infrastructure and extensions to address very complex processing needs.

![Batch Stereotypes](../../.gitbook/assets/image%20%2829%29.png)

## Job

 A `Job` is an entity that encapsulates an entire batch process. `Job` is just the top of an overall hierarchy, as shown in the following diagram:  


![Job Hierarchy](../../.gitbook/assets/image%20%2827%29.png)

 In Spring Batch, a `Job` is simply a container for `Step` instances. It combines multiple steps that belong logically together in a flow and allows for configuration of properties global to all steps, such as restartability. 

### **JobInstance**

 A `JobInstance` refers to the concept of a logical job run. **** Each `JobInstance` can have multiple executions \(JobExecution\).  The definition of a `JobInstance` has absolutely no bearing on the data to be loaded. It is entirely up to the `ItemReader` implementation to determine how data is loaded. 

### **JobParameters**

 A `JobParameters` object holds a set of parameters used to start a batch job. They can be used for identification or even as reference data during the run, as shown in the following image:

![Job Parameters](../../.gitbook/assets/image%20%2828%29.png)

 `JobInstance` = `Job` + identifying `JobParameters`

### **JobExecution**

 A `JobExecution` refers to the technical concept of a single attempt to run a Job. An execution may end in failure or success, but the `JobInstance` corresponding to a given execution is not considered to be complete unless the execution completes successfully. 

## Step

 A `Step` is a domain object that encapsulates an independent, sequential phase of a batch job. Therefore, every Job is composed entirely of one or more steps.  A `Step` contains all of the information necessary to define and control the actual batch processing. 

![Job Hierarchy With Steps](../../.gitbook/assets/image%20%2826%29.png)

### **StepExecution**

 A `StepExecution` represents a single attempt to execute a `Step`. **** A new `StepExecution` is created each time a `Step` is run, similar to `JobExecution`.  Each execution contains a reference to its corresponding step and `JobExecution` and transaction related data, such as commit and rollback counts and start and end times.

### ExecutionContext

 An `ExecutionContext` represents a collection of key/value pairs that are persisted and controlled by the framework in order to allow developers a place to store persistent state that is scoped to a `StepExecution` object or a `JobExecution` object. The best usage example is to facilitate restart.

### Item Reader

`ItemReader` is an abstraction that represents the retrieval of input for a `Step`, one item at a time. When the `ItemReader` has exhausted the items it can provide, it indicates this by returning `null`. More details about the `ItemReader` interface and its various implementations can be found in [Readers And Writers](https://docs.spring.io/spring-batch/docs/4.2.x/reference/html/readersAndWriters.html#readersAndWriters).

### Item Writer

`ItemWriter` is an abstraction that represents the output of a `Step`, one batch or chunk of items at a time. Generally, an `ItemWriter` has no knowledge of the input it should receive next and knows only the item that was passed in its current invocation. More details about the `ItemWriter` interface and its various implementations can be found in [Readers And Writers](https://docs.spring.io/spring-batch/docs/4.2.x/reference/html/readersAndWriters.html#readersAndWriters).

### Item Processor

`ItemProcessor` is an abstraction that represents the business processing of an item. While the `ItemReader` reads one item, and the `ItemWriter` writes them, the `ItemProcessor` provides an access point to transform or apply other business processing. If, while processing the item, it is determined that the item is not valid, returning `null` indicates that the item should not be written out. More details about the `ItemProcessor` interface can be found in [Readers And Writers](https://docs.spring.io/spring-batch/docs/4.2.x/reference/html/readersAndWriters.html#readersAndWriters).

## JobRepository

`JobRepository` is the persistence mechanism for all of the Stereotypes mentioned above. It provides CRUD operations for `JobLauncher`, `Job`, and `Step` implementations. When a `Job` is first launched, a `JobExecution` is obtained from the repository, and, during the course of execution, `StepExecution` and `JobExecution` implementations are persisted by passing them to the repository.

When using java configuration, `@EnableBatchProcessing` annotation provides a `JobRepository` as one of the components automatically configured out of the box.

## JobLauncher

 `JobLauncher` represents a simple interface for launching a `Job` with a given set of `JobParameters`

```java
public interface JobLauncher {

public JobExecution run(Job job, JobParameters jobParameters)
            throws JobExecutionAlreadyRunningException, JobRestartException,
                   JobInstanceAlreadyCompleteException, JobParametersInvalidException;
}
```

## @EnableBatchProcessing

通过添加这个注解会需要很多操作。下面是@EnableBatchProcessing创建的概述:

* JobRepository \(bean名称 "jobRepository"\)
* JobLauncher \(bean名称 "jobLauncher"\)
* JobRegistry \(bean名称 "jobRegistry"\)
* JobExplorer \(bean名称 "jobExplorer"\)
* PlatformTransactionManager \(bean名称 "transactionManager"\)
* JobBuilderFactory \(bean名称"jobBuilders"\)，它可以方便地防止您必须将作业存储库注入到每个Job\(作业\)中
* StepBuilderFactory \(bean名称 "stepBuilders"\)，以方便您避免将作业存储库和事务管理器注入到每个Step\(步骤\)中

