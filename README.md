#kotlin-gradle-raspberry-bug

Reproducing a bug in gradle or kotlin on raspberry pi

## Instructions
Run with `./gradlew`  
It works fine on Linux on a 64bit Intel processor  
but fails with the following text on my Raspberry PI:

```
richo@docker[~/temp/kotlin-gradle-raspberry-bug]$ ./gradlew
:compileKotlin
Using kotlin incremental compilation
Could not perform incremental compilation with Kotlin compile daemon, non-incremental compilation in fallback mode will be performed
Could not connect to kotlin daemon. Using fallback strategy.
e: net.rubygrapefruit.platform.NativeIntegrationUnavailableException: Native integration ProcessLauncher is not supported for Linux arm.
	at net.rubygrapefruit.platform.internal.Platform.get(Platform.java:80)
	at net.rubygrapefruit.platform.Native.get(Native.java:85)
	at org.jetbrains.kotlin.compilerRunner.GradleCompilerRunner.compileOutOfProcess(GradleKotlinCompilerRunner.kt:237)
	at org.jetbrains.kotlin.compilerRunner.GradleCompilerRunner.compileWithDaemonOrFallback(GradleKotlinCompilerRunner.kt:128)
	at org.jetbrains.kotlin.compilerRunner.GradleCompilerRunner.compileWithDaemonOrFallback(GradleKotlinCompilerRunner.kt:43)
	at org.jetbrains.kotlin.compilerRunner.KotlinCompilerRunner.runCompiler(KotlinCompilerRunner.kt:115)
	at org.jetbrains.kotlin.compilerRunner.GradleCompilerRunner.runJvmCompiler(GradleKotlinCompilerRunner.kt:74)
	at org.jetbrains.kotlin.gradle.tasks.KotlinCompile.callCompiler$kotlin_gradle_plugin(Tasks.kt:254)
	at org.jetbrains.kotlin.gradle.tasks.KotlinCompile.callCompiler$kotlin_gradle_plugin(Tasks.kt:160)
	at org.jetbrains.kotlin.gradle.tasks.AbstractKotlinCompile.execute(Tasks.kt:141)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.gradle.internal.reflect.JavaMethod.invoke(JavaMethod.java:73)
	at org.gradle.api.internal.project.taskfactory.DefaultTaskClassInfoStore$IncrementalTaskAction.doExecute(DefaultTaskClassInfoStore.java:163)
	at org.gradle.api.internal.project.taskfactory.DefaultTaskClassInfoStore$StandardTaskAction.execute(DefaultTaskClassInfoStore.java:134)
	at org.gradle.api.internal.project.taskfactory.DefaultTaskClassInfoStore$StandardTaskAction.execute(DefaultTaskClassInfoStore.java:123)
	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeAction(ExecuteActionsTaskExecuter.java:95)
	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeActions(ExecuteActionsTaskExecuter.java:76)
	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.execute(ExecuteActionsTaskExecuter.java:55)
	at org.gradle.api.internal.tasks.execution.SkipUpToDateTaskExecuter.execute(SkipUpToDateTaskExecuter.java:62)
	at org.gradle.api.internal.tasks.execution.ValidatingTaskExecuter.execute(ValidatingTaskExecuter.java:58)
	at org.gradle.api.internal.tasks.execution.SkipEmptySourceFilesTaskExecuter.execute(SkipEmptySourceFilesTaskExecuter.java:88)
	at org.gradle.api.internal.tasks.execution.ResolveTaskArtifactStateTaskExecuter.execute(ResolveTaskArtifactStateTaskExecuter.java:46)
	at org.gradle.api.internal.tasks.execution.SkipTaskWithNoActionsExecuter.execute(SkipTaskWithNoActionsExecuter.java:51)
	at org.gradle.api.internal.tasks.execution.SkipOnlyIfTaskExecuter.execute(SkipOnlyIfTaskExecuter.java:54)
	at org.gradle.api.internal.tasks.execution.ExecuteAtMostOnceTaskExecuter.execute(ExecuteAtMostOnceTaskExecuter.java:43)
	at org.gradle.api.internal.tasks.execution.CatchExceptionTaskExecuter.execute(CatchExceptionTaskExecuter.java:34)
	at org.gradle.execution.taskgraph.DefaultTaskGraphExecuter$EventFiringTaskWorker$1.execute(DefaultTaskGraphExecuter.java:236)
	at org.gradle.execution.taskgraph.DefaultTaskGraphExecuter$EventFiringTaskWorker$1.execute(DefaultTaskGraphExecuter.java:228)
	at org.gradle.internal.Transformers$4.transform(Transformers.java:169)
	at org.gradle.internal.progress.DefaultBuildOperationExecutor.run(DefaultBuildOperationExecutor.java:106)
	at org.gradle.internal.progress.DefaultBuildOperationExecutor.run(DefaultBuildOperationExecutor.java:61)
	at org.gradle.execution.taskgraph.DefaultTaskGraphExecuter$EventFiringTaskWorker.execute(DefaultTaskGraphExecuter.java:228)
	at org.gradle.execution.taskgraph.DefaultTaskGraphExecuter$EventFiringTaskWorker.execute(DefaultTaskGraphExecuter.java:215)
	at org.gradle.execution.taskgraph.AbstractTaskPlanExecutor$TaskExecutorWorker.processTask(AbstractTaskPlanExecutor.java:77)
	at org.gradle.execution.taskgraph.AbstractTaskPlanExecutor$TaskExecutorWorker.run(AbstractTaskPlanExecutor.java:58)
	at org.gradle.execution.taskgraph.DefaultTaskPlanExecutor.process(DefaultTaskPlanExecutor.java:32)
	at org.gradle.execution.taskgraph.DefaultTaskGraphExecuter.execute(DefaultTaskGraphExecuter.java:113)
	at org.gradle.execution.SelectedTaskExecutionAction.execute(SelectedTaskExecutionAction.java:37)
	at org.gradle.execution.DefaultBuildExecuter.execute(DefaultBuildExecuter.java:37)
	at org.gradle.execution.DefaultBuildExecuter.access$000(DefaultBuildExecuter.java:23)
	at org.gradle.execution.DefaultBuildExecuter$1.proceed(DefaultBuildExecuter.java:43)
	at org.gradle.execution.DryRunBuildExecutionAction.execute(DryRunBuildExecutionAction.java:32)
	at org.gradle.execution.DefaultBuildExecuter.execute(DefaultBuildExecuter.java:37)
	at org.gradle.execution.DefaultBuildExecuter.execute(DefaultBuildExecuter.java:30)
	at org.gradle.initialization.DefaultGradleLauncher$RunTasksAction.execute(DefaultGradleLauncher.java:256)
	at org.gradle.initialization.DefaultGradleLauncher$RunTasksAction.execute(DefaultGradleLauncher.java:253)
	at org.gradle.internal.Transformers$4.transform(Transformers.java:169)
	at org.gradle.internal.progress.DefaultBuildOperationExecutor.run(DefaultBuildOperationExecutor.java:106)
	at org.gradle.internal.progress.DefaultBuildOperationExecutor.run(DefaultBuildOperationExecutor.java:56)
	at org.gradle.initialization.DefaultGradleLauncher.doBuildStages(DefaultGradleLauncher.java:175)
	at org.gradle.initialization.DefaultGradleLauncher.doBuild(DefaultGradleLauncher.java:119)
	at org.gradle.initialization.DefaultGradleLauncher.run(DefaultGradleLauncher.java:102)
	at org.gradle.launcher.exec.GradleBuildController.run(GradleBuildController.java:71)
	at org.gradle.tooling.internal.provider.ExecuteBuildActionRunner.run(ExecuteBuildActionRunner.java:28)
	at org.gradle.launcher.exec.ChainingBuildActionRunner.run(ChainingBuildActionRunner.java:35)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter.execute(InProcessBuildActionExecuter.java:41)
	at org.gradle.launcher.exec.InProcessBuildActionExecuter.execute(InProcessBuildActionExecuter.java:26)
	at org.gradle.tooling.internal.provider.ContinuousBuildActionExecuter.execute(ContinuousBuildActionExecuter.java:75)
	at org.gradle.tooling.internal.provider.ContinuousBuildActionExecuter.execute(ContinuousBuildActionExecuter.java:49)
	at org.gradle.tooling.internal.provider.ServicesSetupBuildActionExecuter.execute(ServicesSetupBuildActionExecuter.java:49)
	at org.gradle.tooling.internal.provider.ServicesSetupBuildActionExecuter.execute(ServicesSetupBuildActionExecuter.java:31)
	at org.gradle.launcher.cli.RunBuildAction.run(RunBuildAction.java:51)
	at org.gradle.internal.Actions$RunnableActionAdapter.execute(Actions.java:173)
	at org.gradle.launcher.cli.CommandLineActionFactory$ParseAndBuildAction.execute(CommandLineActionFactory.java:244)
	at org.gradle.launcher.cli.CommandLineActionFactory$ParseAndBuildAction.execute(CommandLineActionFactory.java:217)
	at org.gradle.launcher.cli.JavaRuntimeValidationAction.execute(JavaRuntimeValidationAction.java:33)
	at org.gradle.launcher.cli.JavaRuntimeValidationAction.execute(JavaRuntimeValidationAction.java:24)
	at org.gradle.launcher.cli.ExceptionReportingAction.execute(ExceptionReportingAction.java:33)
	at org.gradle.launcher.cli.ExceptionReportingAction.execute(ExceptionReportingAction.java:22)
	at org.gradle.launcher.cli.CommandLineActionFactory$WithLogging.execute(CommandLineActionFactory.java:210)
	at org.gradle.launcher.cli.CommandLineActionFactory$WithLogging.execute(CommandLineActionFactory.java:174)
	at org.gradle.launcher.Main.doAction(Main.java:33)
	at org.gradle.launcher.bootstrap.EntryPoint.run(EntryPoint.java:45)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.gradle.launcher.bootstrap.ProcessBootstrap.runNoExit(ProcessBootstrap.java:60)
	at org.gradle.launcher.bootstrap.ProcessBootstrap.run(ProcessBootstrap.java:37)
	at org.gradle.launcher.GradleMain.main(GradleMain.java:23)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.gradle.wrapper.BootstrapMainStarter.start(BootstrapMainStarter.java:30)
	at org.gradle.wrapper.WrapperExecutor.execute(WrapperExecutor.java:129)
	at org.gradle.wrapper.GradleWrapperMain.main(GradleWrapperMain.java:61)

e: Compiler terminated with internal error
:compileKotlin FAILED

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':compileKotlin'.
> Internal compiler error. See log for more details

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.

BUILD FAILED

Total time: 35.935 secs

```
