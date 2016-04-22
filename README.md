# metrik
Interfaces for gathering runtime metrics, KPIs, and other stats for Microservice Container Development. Supports Consul, StatsD, InfluxDB and more.

Interface for tracking metrics.

```java
...
public interface MetricsCollector {

    default void increment(final String name) {
        recordCount(name, 1);
    }

    default void recordCount(String name, long count) {
    }

    default void recordLevel(String name, long level) {
    }

    default void recordTiming(String name, long duration) {
    }

}

```


```java
public interface MetricsCollector {


    /**
     * Increment a counter by 1.
     * This is a short cut for recordCount(name, 1);
     *
     * @param name name name of metric, KPI, metric.
     */
    default void increment(final String name) {
        recordCount(name, 1);
    }

    /**
     * Record a a count.
     * Used to record things like how many users used the site.
     *
     * @param name  name of the metric, KPI, stat
     * @param count count to record.
     */
    default void recordCount(String name, long count) {
    }

    /**
     * This is used to record things like the count of current threads or
     * free system memory or free disk, etc.
     * Record Level. Some systems call this a gauge.
     *
     * @param name  name of the gauge or level
     * @param level level
     */
    default void recordLevel(String name, long level) {
    }

    /**
     * This is used to record timings.
     * This would be things like how long did it take this service to call this remote service.
     *
     * @param name     name of the timing
     * @param duration duration
     */
    default void recordTiming(String name, long duration) {
    }

}

```
