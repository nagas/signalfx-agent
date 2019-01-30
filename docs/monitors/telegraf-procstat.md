<!--- GENERATED BY gomplate from scripts/docs/monitor-page.md.tmpl --->

# telegraf/procstat

 This monitor reports metrics about processes.
This monitor is based on the Telegraf procstat plugin.  More information about the Telegraf plugin
can be found [here](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/procstat).

Please note that the Smart Agent only supports the `native` pid finder and the options
`cgroup` and `systemd unit` are not supported at this time.

On Linux hosts, this monitor relies on the `/proc` filesystem.
If the underlying host's `/proc` file system is mounted somewhere other than
/proc please specify the path using the top level configuration `procPath`.

Sample Yaml Configuration

```yaml
procPath: /proc
monitors:
 - type: telegraf/procstat
   exe: "signalfx-agent*"
```


Monitor Type: `telegraf/procstat`

[Monitor Source Code](https://github.com/signalfx/signalfx-agent/tree/master/internal/monitors/telegraf/monitors/procstat)

**Accepts Endpoints**: No

**Multiple Instances Allowed**: Yes

## Configuration

| Config option | Required | Type | Description |
| --- | --- | --- | --- |
| `exe` | no | `string` | The name of an executable to monitor.  (ie: `exe: "signalfx-agent*"`) |
| `pattern` | no | `string` | Pattern to match against.  On Windows the pattern should be in the form of a WMI query. (ie: `pattern: "%signalfx-agent%"`) |
| `user` | no | `string` | Username to match against |
| `pidFile` | no | `string` | Path to Pid file to monitor.  (ie: `pidFile: "/var/run/signalfx-agent.pid"`) |
| `processName` | no | `string` | Used to override the process name dimension |
| `prefix` | no | `string` | Prefix to be added to each dimension |
| `pidTag` | no | `bool` | Whether to add PID as a dimension instead of part of the metric name (**default:** `false`) |
| `cGroup` | no | `string` | The name of the cgroup to monitor.  This cgroup name will be appended to the configured `sysPath`.  See the agent config schema for more information about the `sysPath` agent configuration. |
| `WinService` | no | `string` | The name of a windows service to report procstat information on. |




## Metrics

The following table lists the metrics available for this monitor. Metrics that are not marked as Custom are standard metrics and are monitored by default.

| Name | Type | Custom | Description |
| ---  | ---  | ---    | ---         |
| `procstat.cpu_time` | gauge | X | Amount of cpu time consumed by the process. |
| `procstat.cpu_usage` | gauge | X | CPU used by the process. |
| `procstat.involuntary_context_switches` | gauge | X | Number of involuntary context switches. |
| `procstat.memory_data` | gauge | X | VMData memory used by the process. |
| `procstat.memory_locked` | gauge | X | VMLocked memory used by the process. |
| `procstat.memory_rss` | gauge | X | VMRSS memory used by the process. |
| `procstat.memory_stack` | gauge | X | VMStack memory used by the process. |
| `procstat.memory_swap` | gauge | X | VMSwap memory used by the process. |
| `procstat.memory_vms` | gauge | X | VMS memory used by the process. |
| `procstat.nice_priority` | gauge | X | Nice priority number of the process. |
| `procstat.num_fds` | gauge | X | Number of file descriptors.  This may require the agent to be running as root. |
| `procstat.num_threads` | gauge | X | Number of threads used by the process. |
| `procstat.read_bytes` | gauge | X | Number of bytes read by the process.  This may require the agent to be running as root. |
| `procstat.read_count` | gauge | X | Number of read operations by the process.  This may require the agent to be running as root. |
| `procstat.realtime_priority` | gauge | X | Real time priority of the process. |
| `procstat.rlimit_cpu_time_hard` | gauge | X | The hard cpu rlimit. |
| `procstat.rlimit_cpu_time_soft` | gauge | X | The soft cpu rlimit. |
| `procstat.rlimit_file_locks_hard` | gauge | X | The hard file lock rlimit. |
| `procstat.rlimit_file_locks_soft` | gauge | X | The soft file lock rlimit. |
| `procstat.rlimit_memory_data_hard` | gauge | X | The hard data memory rlimit. |
| `procstat.rlimit_memory_data_soft` | gauge | X | The soft data memory rlimit. |
| `procstat.rlimit_memory_locked_hard` | gauge | X | The hard locked memory rlimit. |
| `procstat.rlimit_memory_locked_soft` | gauge | X | The soft locked memory rlimit. |
| `procstat.rlimit_memory_rss_hard` | gauge | X | The hard rss memory rlimit. |
| `procstat.rlimit_memory_rss_soft` | gauge | X | The soft rss memory rlimit. |
| `procstat.rlimit_memory_stack_hard` | gauge | X | The hard stack memory rlimit. |
| `procstat.rlimit_memory_stack_soft` | gauge | X | The soft stack memory rlimit. |
| `procstat.rlimit_memory_vms_hard` | gauge | X | The hard vms memory rlimit. |
| `procstat.rlimit_memory_vms_soft` | gauge | X | The soft vms memory rlimit. |
| `procstat.rlimit_nice_priority_hard` | gauge | X | The hard nice priority rlimit. |
| `procstat.rlimit_nice_priority_soft` | gauge | X | The soft nice priority rlimit. |
| `procstat.rlimit_num_fds_hard` | gauge | X | The hard file descriptor rlimit. |
| `procstat.rlimit_num_fds_soft` | gauge | X | The soft file descriptor rlimit. |
| `procstat.rlimit_realtime_priority_hard` | gauge | X | The hard realtime priority rlimit. |
| `procstat.rlimit_realtime_priority_soft` | gauge | X | The soft realtime priority rlimit. |
| `procstat.rlimit_signals_pending_hard` | gauge | X | The hard pending signal rlimit. |
| `procstat.rlimit_signals_pending_soft` | gauge | X | The soft pendidng signal rlimit. |
| `procstat.signals_pending` | gauge | X | The number of signals pending. |
| `procstat.write_bytes` | gauge | X | Number of bytes written by the process.  This may require the agent to be running as root. |
| `procstat.write_count` | gauge | X | Number of write operations by the process.  This may require the agent to be running as root. |
| `procstat_lookup.pid_count` | gauge | X | The number of pids. This metric emits with the plugin dimension set to "procstat_lookup". |


To specify custom metrics you want to monitor, add a `metricsToInclude` filter
to the agent configuration, as shown in the code snippet below. The snippet
lists all available custom metrics. You can copy and paste the snippet into
your configuration file, then delete any custom metrics that you do not want
sent.

Note that some of the custom metrics require you to set a flag as well as add
them to the list. Check the monitor configuration file to see if a flag is
required for gathering additional metrics.

```yaml

metricsToInclude:
  - metricNames:
    - procstat.cpu_time
    - procstat.cpu_usage
    - procstat.involuntary_context_switches
    - procstat.memory_data
    - procstat.memory_locked
    - procstat.memory_rss
    - procstat.memory_stack
    - procstat.memory_swap
    - procstat.memory_vms
    - procstat.nice_priority
    - procstat.num_fds
    - procstat.num_threads
    - procstat.read_bytes
    - procstat.read_count
    - procstat.realtime_priority
    - procstat.rlimit_cpu_time_hard
    - procstat.rlimit_cpu_time_soft
    - procstat.rlimit_file_locks_hard
    - procstat.rlimit_file_locks_soft
    - procstat.rlimit_memory_data_hard
    - procstat.rlimit_memory_data_soft
    - procstat.rlimit_memory_locked_hard
    - procstat.rlimit_memory_locked_soft
    - procstat.rlimit_memory_rss_hard
    - procstat.rlimit_memory_rss_soft
    - procstat.rlimit_memory_stack_hard
    - procstat.rlimit_memory_stack_soft
    - procstat.rlimit_memory_vms_hard
    - procstat.rlimit_memory_vms_soft
    - procstat.rlimit_nice_priority_hard
    - procstat.rlimit_nice_priority_soft
    - procstat.rlimit_num_fds_hard
    - procstat.rlimit_num_fds_soft
    - procstat.rlimit_realtime_priority_hard
    - procstat.rlimit_realtime_priority_soft
    - procstat.rlimit_signals_pending_hard
    - procstat.rlimit_signals_pending_soft
    - procstat.signals_pending
    - procstat.write_bytes
    - procstat.write_count
    - procstat_lookup.pid_count
    monitorType: telegraf/procstat
```



