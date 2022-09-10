# kogito-cron-expression-exception

* `quarkus create app kogito-cron-expression-exception -x kogito-quarkus -x resteasy-reactive -x resteasy-reactive-jackson`
* `cd kogito-cron-expression-exception`
* Create [cron-expression.bpmn2](src/main/resources/cron-expression.bpmn2)
* Set timer settings to _Fire multiple times_, select _Cron_ format, enter `0 0/1 * ? * * *`
* `quarkus dev`

```java
2022-09-10 18:32:16,104 ERROR [io.qua.run.Application] (Quarkus Main Thread) Failed to start application (with profile dev): java.lang.RuntimeException: Error parsing time string: [ 0 0/1 * ? * * * ]
	at org.drools.core.time.TimeUtils.parseTimeString(TimeUtils.java:131)
	at org.jbpm.process.core.timer.DateTimeUtils.parseRepeatableDateTime(DateTimeUtils.java:134)
	at org.kie.kogito.process.impl.AbstractProcess.configureTimerInstance(AbstractProcess.java:216)
	at com.example.Cron_expressionProcess_Subclass.configureTimerInstance$$superforward1(Unknown Source)
	at com.example.Cron_expressionProcess_Subclass.configureTimerInstance(Unknown Source)
	at org.kie.kogito.process.impl.AbstractProcess.activate(AbstractProcess.java:196)
	at com.example.Cron_expressionProcess_Subclass.activate$$superforward1(Unknown Source)
	at com.example.Cron_expressionProcess_Subclass.activate(Unknown Source)
	at com.example.Cron_expressionProcess.<init>(Cron_expressionProcess.java:16)
	at com.example.Cron_expressionProcess_Subclass.<init>(Unknown Source)
	at com.example.Cron_expressionProcess_Bean.create(Unknown Source)
	at com.example.Cron_expressionProcess_Bean.create(Unknown Source)
	at io.quarkus.arc.impl.AbstractSharedContext.createInstanceHandle(AbstractSharedContext.java:111)
	at io.quarkus.arc.impl.AbstractSharedContext$1.get(AbstractSharedContext.java:35)
	at io.quarkus.arc.impl.AbstractSharedContext$1.get(AbstractSharedContext.java:32)
	at io.quarkus.arc.impl.LazyValue.get(LazyValue.java:26)
	at io.quarkus.arc.impl.ComputingCache.computeIfAbsent(ComputingCache.java:69)
	at io.quarkus.arc.impl.AbstractSharedContext.get(AbstractSharedContext.java:32)
	at io.quarkus.arc.impl.ClientProxies.getApplicationScopedDelegate(ClientProxies.java:19)
	at com.example.Cron_expressionProcess_ClientProxy.arc$delegate(Unknown Source)
	at com.example.Cron_expressionProcess_ClientProxy.arc_contextualInstance(Unknown Source)
	at com.example.Cron_expressionProcess_Observer_Synthetic_d70cd75bf32ab6598217b9a64a8473d65e248c05.notify(Unknown Source)
	at io.quarkus.arc.impl.EventImpl$Notifier.notifyObservers(EventImpl.java:323)
	at io.quarkus.arc.impl.EventImpl$Notifier.notify(EventImpl.java:305)
	at io.quarkus.arc.impl.EventImpl.fire(EventImpl.java:73)
	at io.quarkus.arc.runtime.ArcRecorder.fireLifecycleEvent(ArcRecorder.java:131)
	at io.quarkus.arc.runtime.ArcRecorder.handleLifecycleEvents(ArcRecorder.java:100)
	at io.quarkus.deployment.steps.LifecycleEventsBuildStep$startupEvent1144526294.deploy_0(Unknown Source)
	at io.quarkus.deployment.steps.LifecycleEventsBuildStep$startupEvent1144526294.deploy(Unknown Source)
	at io.quarkus.runner.ApplicationImpl.doStart(Unknown Source)
	at io.quarkus.runtime.Application.start(Application.java:101)
	at io.quarkus.runtime.ApplicationLifecycleManager.run(ApplicationLifecycleManager.java:110)
	at io.quarkus.runtime.Quarkus.run(Quarkus.java:67)
	at io.quarkus.runtime.Quarkus.run(Quarkus.java:41)
	at io.quarkus.runtime.Quarkus.run(Quarkus.java:120)
	at io.quarkus.runner.GeneratedMain.main(Unknown Source)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:77)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:568)
	at io.quarkus.runner.bootstrap.StartupActionImpl$1.run(StartupActionImpl.java:103)
	at java.base/java.lang.Thread.run(Thread.java:833)
```

Check quartz cron expression here: <https://freeformatter.com/cron-expression-generator-quartz.html>
