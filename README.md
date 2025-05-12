# Maven 4 SNAPSHOT breaks extra-enforcer-rules requirePropertyDiverges

## Maven 3.9.9

```
❯ mvn -q wrapper:wrapper -Dmaven=3.9.9 && ./mvnw -v && mvn -e -q validate
Apache Maven 3.9.9 (8e8579a9e76f7d015ee5ec7bfcdc97d260186937)
Maven home: /Users/mifr/.m2/wrapper/dists/apache-maven-3.9.9/3477a4f1
Java version: 21.0.7, vendor: Eclipse Adoptium, runtime: /Library/Java/JavaVirtualMachines/temurin-21.jdk/Contents/Home
Default locale: de_DE, platform encoding: UTF-8
OS name: "mac os x", version: "15.4.1", arch: "aarch64", family: "mac"
```

## Maven 4.0.0-rc-3

```
❯ mvn -q wrapper:wrapper -Dmaven=4.0.0-rc-3 && ./mvnw -v && mvn -e -q validate  
Apache Maven 4.0.0-rc-3 (3952d00ce65df6753b63a51e86b1f626c55a8df2)
Maven home: /Users/mifr/.m2/wrapper/dists/apache-maven-4.0.0-rc-3/f94e8f8d
Java version: 21.0.7, vendor: Eclipse Adoptium, runtime: /Library/Java/JavaVirtualMachines/temurin-21.jdk/Contents/Home
Default locale: de_DE, platform encoding: UTF-8
OS name: "mac os x", version: "15.4.1", arch: "aarch64", family: "mac"
```

## Maven 4.0.0-rc4-SNAPSHOT

```
❯ curl -s https://repository.apache.org/content/repositories/snapshots/org/apache/maven/apache-maven/4.0.0-rc-4-SNAPSHOT/apache-maven-4.0.0-rc-4-20250512.103009-96-bin.tar.gz | tar xz && ./apache-maven-4.0.0-rc-4-SNAPSHOT/bin/mvn -v && ./apache-maven-4.0.0-rc-4-SNAPSHOT/bin/mvn -e validate  
Apache Maven 4.0.0-rc-4-SNAPSHOT (ec56597f9ba8a8d68491bbee989756d3dcdd41d9)
Maven home: /Users/mifr/ghq/github.com/mfriedenhagen/maven4-extra-enforcer/apache-maven-4.0.0-rc-4-SNAPSHOT
Java version: 21.0.7, vendor: Eclipse Adoptium, runtime: /Library/Java/JavaVirtualMachines/temurin-21.jdk/Contents/Home
Default locale: de_DE, platform encoding: UTF-8
OS name: "mac os x", version: "15.4.1", arch: "aarch64", family: "mac"
[INFO] Error stacktraces are turned on.
[INFO] Scanning for projects...
[INFO] 
[INFO] --------------------------------< com.github.mfriedenhagen:maven4-extra-enforcer-parent >---------------------------------
[INFO] Building maven4-extra-enforcer-parent 9999
[INFO]   from pom.xml
[INFO] ---------------------------------------------------------[ pom ]----------------------------------------------------------
[INFO] 
[INFO] --- enforcer:3.5.0:enforce (default-enforce) @ maven4-extra-enforcer-parent ---
[INFO] Always pass!
[INFO] Rule 0: org.apache.maven.enforcer.rules.AlwaysPass passed
[INFO] Rule 1: org.apache.maven.enforcer.rules.property.RequireProperty passed
[INFO] --------------------------------------------------------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] --------------------------------------------------------------------------------------------------------------------------
[INFO] Total time:  0.272 s
[INFO] Finished at: 2025-05-12T18:05:42+02:00
[INFO] --------------------------------------------------------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-enforcer-plugin:3.5.0:enforce (default-enforce) on project maven4-extra-enforcer-parent: Execution default-enforce of goal org.apache.maven.plugins:maven-enforcer-plugin:3.5.0:enforce failed: Failed to find reference POM which defines the current value -> [Help 1]
org.apache.maven.lifecycle.LifecycleExecutionException: Failed to execute goal org.apache.maven.plugins:maven-enforcer-plugin:3.5.0:enforce (default-enforce) on project maven4-extra-enforcer-parent: Execution default-enforce of goal org.apache.maven.plugins:maven-enforcer-plugin:3.5.0:enforce failed: Failed to find reference POM which defines the current value
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute2(MojoExecutor.java:346)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute(MojoExecutor.java:310)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:214)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:179)
    at org.apache.maven.lifecycle.internal.MojoExecutor$1.run(MojoExecutor.java:168)
    at org.apache.maven.plugin.DefaultMojosExecutionStrategy.execute(DefaultMojosExecutionStrategy.java:39)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:165)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:110)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:76)
    at org.apache.maven.lifecycle.internal.builder.singlethreaded.SingleThreadedBuilder.build(SingleThreadedBuilder.java:60)
    at org.apache.maven.lifecycle.internal.DefaultLifecycleStarter.execute(DefaultLifecycleStarter.java:123)
    at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:310)
    at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:225)
    at org.apache.maven.DefaultMaven.execute(DefaultMaven.java:149)
    at org.apache.maven.cling.invoker.mvn.MavenInvoker.doExecute(MavenInvoker.java:461)
    at org.apache.maven.cling.invoker.mvn.MavenInvoker.execute(MavenInvoker.java:100)
    at org.apache.maven.cling.invoker.mvn.MavenInvoker.execute(MavenInvoker.java:81)
    at org.apache.maven.cling.invoker.LookupInvoker.doInvoke(LookupInvoker.java:166)
    at org.apache.maven.cling.invoker.LookupInvoker.invoke(LookupInvoker.java:136)
    at org.apache.maven.cling.ClingSupport.run(ClingSupport.java:76)
    at org.apache.maven.cling.MavenCling.main(MavenCling.java:51)
    at jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
    at java.lang.reflect.Method.invoke(Method.java:580)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launchEnhanced(Launcher.java:255)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launch(Launcher.java:201)
    at org.codehaus.plexus.classworlds.launcher.Launcher.mainWithExitCode(Launcher.java:361)
    at org.codehaus.plexus.classworlds.launcher.Launcher.main(Launcher.java:314)
Caused by: org.apache.maven.plugin.PluginExecutionException: Execution default-enforce of goal org.apache.maven.plugins:maven-enforcer-plugin:3.5.0:enforce failed: Failed to find reference POM which defines the current value
    at org.apache.maven.plugin.DefaultBuildPluginManager.executeMojo(DefaultBuildPluginManager.java:152)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute2(MojoExecutor.java:339)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute(MojoExecutor.java:310)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:214)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:179)
    at org.apache.maven.lifecycle.internal.MojoExecutor$1.run(MojoExecutor.java:168)
    at org.apache.maven.plugin.DefaultMojosExecutionStrategy.execute(DefaultMojosExecutionStrategy.java:39)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:165)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:110)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:76)
    at org.apache.maven.lifecycle.internal.builder.singlethreaded.SingleThreadedBuilder.build(SingleThreadedBuilder.java:60)
    at org.apache.maven.lifecycle.internal.DefaultLifecycleStarter.execute(DefaultLifecycleStarter.java:123)
    at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:310)
    at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:225)
    at org.apache.maven.DefaultMaven.execute(DefaultMaven.java:149)
    at org.apache.maven.cling.invoker.mvn.MavenInvoker.doExecute(MavenInvoker.java:461)
    at org.apache.maven.cling.invoker.mvn.MavenInvoker.execute(MavenInvoker.java:100)
    at org.apache.maven.cling.invoker.mvn.MavenInvoker.execute(MavenInvoker.java:81)
    at org.apache.maven.cling.invoker.LookupInvoker.doInvoke(LookupInvoker.java:166)
    at org.apache.maven.cling.invoker.LookupInvoker.invoke(LookupInvoker.java:136)
    at org.apache.maven.cling.ClingSupport.run(ClingSupport.java:76)
    at org.apache.maven.cling.MavenCling.main(MavenCling.java:51)
    at jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
    at java.lang.reflect.Method.invoke(Method.java:580)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launchEnhanced(Launcher.java:255)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launch(Launcher.java:201)
    at org.codehaus.plexus.classworlds.launcher.Launcher.mainWithExitCode(Launcher.java:361)
    at org.codehaus.plexus.classworlds.launcher.Launcher.main(Launcher.java:314)
Caused by: java.lang.IllegalStateException: Failed to find reference POM which defines the current value
    at org.codehaus.mojo.extraenforcer.model.RequirePropertyDiverges.execute(RequirePropertyDiverges.java:102)
    at org.apache.maven.plugins.enforcer.EnforceMojo.executeRuleNew(EnforceMojo.java:351)
    at org.apache.maven.plugins.enforcer.EnforceMojo.executeRule(EnforceMojo.java:325)
    at org.apache.maven.plugins.enforcer.EnforceMojo.execute(EnforceMojo.java:248)
    at org.apache.maven.plugin.DefaultBuildPluginManager.executeMojo(DefaultBuildPluginManager.java:146)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute2(MojoExecutor.java:339)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute(MojoExecutor.java:310)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:214)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:179)
    at org.apache.maven.lifecycle.internal.MojoExecutor$1.run(MojoExecutor.java:168)
    at org.apache.maven.plugin.DefaultMojosExecutionStrategy.execute(DefaultMojosExecutionStrategy.java:39)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:165)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:110)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:76)
    at org.apache.maven.lifecycle.internal.builder.singlethreaded.SingleThreadedBuilder.build(SingleThreadedBuilder.java:60)
    at org.apache.maven.lifecycle.internal.DefaultLifecycleStarter.execute(DefaultLifecycleStarter.java:123)
    at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:310)
    at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:225)
    at org.apache.maven.DefaultMaven.execute(DefaultMaven.java:149)
    at org.apache.maven.cling.invoker.mvn.MavenInvoker.doExecute(MavenInvoker.java:461)
    at org.apache.maven.cling.invoker.mvn.MavenInvoker.execute(MavenInvoker.java:100)
    at org.apache.maven.cling.invoker.mvn.MavenInvoker.execute(MavenInvoker.java:81)
    at org.apache.maven.cling.invoker.LookupInvoker.doInvoke(LookupInvoker.java:166)
    at org.apache.maven.cling.invoker.LookupInvoker.invoke(LookupInvoker.java:136)
    at org.apache.maven.cling.ClingSupport.run(ClingSupport.java:76)
    at org.apache.maven.cling.MavenCling.main(MavenCling.java:51)
    at jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
    at java.lang.reflect.Method.invoke(Method.java:580)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launchEnhanced(Launcher.java:255)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launch(Launcher.java:201)
    at org.codehaus.plexus.classworlds.launcher.Launcher.mainWithExitCode(Launcher.java:361)
    at org.codehaus.plexus.classworlds.launcher.Launcher.main(Launcher.java:314)
[ERROR] 
[ERROR] Re-run Maven using the '-X' switch to enable verbose output
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/PluginExecutionException
```
