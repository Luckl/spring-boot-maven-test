# spring-boot-maven-test
To demonstrate issue with spring-boot-maven-plugin build-image goal.

When running a mvn install, you will see that it runs the maven lifecycle until the install phase. 
Then the following log line appears:
```
[INFO] >>> spring-boot-maven-plugin:2.3.0.RELEASE:build-image (build-image) > package @ spring-boot-maven-test >>>
```

After which maven will restart the lifecycle it seems.

Most default maven goals can handle this, as you can see with for instance surefire which prints the following:
```
[INFO] Skipping execution of surefire because it has already been run for this configuration
```

But if jacoco is setup to run in the report phase, it will run twice and in our case will also add the integration test coverage into the coverage report. (not yet part of the example)
