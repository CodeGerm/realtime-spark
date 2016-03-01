# realtime-spark
Set of infrastructure Docker images and Docker compose to create a realtime spark system

The project inscludes following docker containers:

1. hadoop-docker : a docker container with hadoop/yarn cluster with spark assembly preinstalled.

2. spark-jobserver-docker :  a docker container with spark jobserver which is pointing to the yarn cluster container mentioned above.

# How to run the realtime-spark

Git pull this project.

Run docker compose. It will automatically build the docker images and run docker containers. 
```
docker-compose up -d
```
Test the spark job server ui using a browser @ http://docker host:18090 and also test the yarn @ http://docker host:8088

Run your first spark job, assuming you have built spark example word count jar file.

Create new application and upload jar
```
curl --data-binary @job-server-tests/target/scala-2.10/job-server-tests_2.10-0.6.2-SNAPSHOT.jar docker_host:18090/jars/test
```
Run test application 

```
propmpt$curl -d "input.string = a b c a b see" 'docker_host:18090/jobs?appName=test&classPath=spark.jobserver.WordCountExample'

{
  "status": "STARTED",
  "result": {
    "jobId": "43f0e14a-96fd-48bf-8d66-f121dcc2c6da",
    "context": "b83a8688-spark.jobserver.WordCountExample"
  }
}
```

Get test results

```
prompt$curl docker_host:18090/jobs/43f0e14a-96fd-48bf-8d66-f121dcc2c6da

{
  "duration": "3.526 secs",
  "classPath": "spark.jobserver.WordCountExample",
  "startTime": "2016-02-27T10:34:57.387Z",
  "context": "b83a8688-spark.jobserver.WordCountExample",
  "result": {
    "b": 2,
    "a": 2,
    "see": 1,
    "c": 1
  },
  "status": "FINISHED",
  "jobId": "43f0e14a-96fd-48bf-8d66-f121dcc2c6da"
}
```


