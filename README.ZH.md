# Swar's Chia Plot Manager 

#### 它是一个 chia 绘图管理器: https://www.chia.net/
[English](README.md) / [Русский](README.RU.md) / [中文](README.ZH.md)

![The view of the manager](https://i.imgur.com/hIhjXt0.png "View")

##### 开发版本: v0.1.0

这是一个跨平台的 Chia 绘图管理器，它可以运行在主流操作系统上。这不是一个绘图器。该库的目的是管理您的绘图，并使用您配置的设置来启动新的绘图。每个人的系统都是独一无二的，所以定制化是这个库的一个重要特点。

该库很简单，易用且可靠，可确保绘图的生成。

该库已经在 Windows 和 Linux 上进行测试。

## 功能

* 交错安排您的绘图，这样您的资源就可以避免高峰拥挤。
* 允许最终目录列表。
* 利用临时空间的最大潜力，尽早开始一个新的绘图。
* 同时运行最大数量的绘图，以避免出现瓶颈或限制资源占用。
* 更深入的绘图任务显示。

## 赞助 / 支持该库

该库花了很多时间和精力才有了今天的它。考虑赞助或支持该库，这不是必须的，但更多的是一种友善的支持。

* XCH Address: xch134evwwqkq50nnsmgehnnag4gc856ydc7ached3xxr6jdk7e8l4usdnw39t
* ETH Address: 0xf8F7BD24B94D75E54BFD9557fF6904DBE239322E
* BTC Address: 36gnjnHqkttcBiKjjAekoy68z6C3BJ9ekS
* Paypal: https://www.paypal.com/biz/fund?id=XGVS7J69KYBTY

## 支持 / 问题

请不要使用 GitHub 的 issues 来发布您自己的个人设置。问题应该与代码和想法中的实际错误有关。在这个问题上，它已经在 Windows, Linux 和 Mac OS 上进行了测试。因此，任何有关技术支持、配置设置或与您个人用例有关的问题都应该发布在下面的任意一个链接上。

* Discord Server: https://discord.gg/XyvMzeQpu2
* This is the Official Discord Server - Swar's Chia Community 
* Official Chia Keybase Team: https://keybase.io/team/chia_network.public
* The channel is #swar 
* GitHub Discussion Board: https://github.com/swar/Swar-Chia-Plot-Manager/discussions

## 常见问题

##### 我能重新加载我的配置吗？
* 是的，您的配置可以通过 `python manager.py restart` 命令来重新加载，或者单独停止并重新启动管理器。请注意，您的任务数将被重置！temporary2和最终目录的顺序也将被重置。
* 请注意，如果您修改任何目录的作业，它将扰乱现有的作业，并且 `manager` 和 `view` 将不能识别旧的作业。如果您正在更改作业目录，同时正在执行绘图任务，请将当前作业的 `max_plots` 更改为0，并使用新目录创建一个单独的作业。我**不建议**在plots运行时修改目录。

##### 如果我停止管理器，我的plots进程是否会被杀掉？
* 不。plots是在后台运行的，它们不会杀掉您现有plots进程。如果您想结束进程，您可以查看进程ID，可以使用该pid在任务管理器(或适合您操作系统的软件)中跟踪它们，并手动杀掉它们。请注意，您也必须手动删除.tmp文件。我不会帮您处理这件事。

##### 如果我有一个列表，如何选择temporary2目录和最终目录？
* 他们是按顺序被选中的。假设有两个目录，第一个 plot 将选择第一个，第二个 plot 将选择第二个，第三个 plot 将选择第一个。

##### 什么是 `temporary2_destination_sync`?
* 有些用户喜欢选择始终具有相同的 temporary2 和最终目录。启用这个设置将总是让 temporary2 作为目的地的驱动器。如果您使用这个设置，您可以使用一个空的 temporary2

##### 我的最佳配置是什么
* 请将此问题转发到 Keybase 或 Discussion。

## 全部命令

##### 命令的使用示例
```text
> python3 manager.py start

> python3 manager.py restart

> python3 manager.py stop

> python3 manager.py view

> python3 manager.py status

> python3 manager.py analyze_logs
```

### start

该命令将在后台启动管理器。一旦启动，它将一直运行，除非所有作业`max plot`都完成了或出现错误。错误将记录在创建的 `debug.log` 文件中。

### stop

该命令将在后台终止管理器。它不会停止 plots 的运行，它只会阻止新 plots 的生成。

### restart

该命令将依次运行 start 和 stop。

### view

该命令将显示一个视图，您可以使用该视图跟踪正在运行的 plots。这将按照 `config.yaml` 定义的每x秒更新一次。

### status

该命令将生成视图的单个快照。它不会更新。

### analyze_logs

该命令将分析日志文件夹中所有已完成的 plot 日志，并为计算机配置计算适当的权重和线。只需配置 `config.yaml` 中的 `progress`部分的值。这只会影响进度条。

## 安装

该库的安装非常简单。 我在下面附上了详细的说明，应该可以帮助您入门。

#### NOTE: If `python` does not work, please try `python3`.

1. Download and Install Python 3.7 or higher: https://www.python.org/
2. `git clone` this repo or download it.
3. Open CommandPrompt / PowerShell / Terminal and `cd` into the main library folder.
   * Example: `cd C:\Users\Swar\Documents\Swar-Chia-Plot-Manager`
4. OPTIONAL: Create a virtual environment for Python. This is recommended if you use Python for other things.
	1. Create a new python environment: `python -m venv venv`
	   * The second `venv` can be renamed to whatever you want. I prefer `venv` because it's a standard.
	2. Activate the virtual environment. This must be done *every single time* you open a new window.
	   * Example Windows: `venv\Scripts\activate`
	   * Example Linux: `. ./venv/bin/activate` or `source ./venv/bin/activate`
	   * Example Mac OS: `/Applications/Chia.app/Contents/Resources/app.asar.unpacked/daemon/chia`
	3. Confirm that it has activated by seeing the `(venv)` prefix. The prefix will change depending on what you named it.
5. Install the required modules: `pip install -r requirements.txt`
	* If you plan on using Notifications or Prometheus then run the following to install the required modules: `pip install -r requirements-notification.txt`
6. Copy `config.yaml.default` and name it as `config.yaml` in the same directory.
7. Edit and set up the config.yaml to your own personal settings. There is more help on this below.
	* You will need to add the `chia_location` as well! This should point to your chia executable.
9. Run the Manager: `python manager.py start`
   * This will start a process in the background that will manage plots based on your inputted settings.
10. Run the View: `python manager.py view`
   * This will loop through a view screen with details about active plots.


## Configuration

The configuration of this library is unique to every end-user. The `config.yaml` file is where the configuration will live. 

This plot manager works based on the idea of jobs. Each job will have its own settings that you can configure and customize. No two drives are unique so this will provide flexibility for your own constraints and requirements.

### chia_location

This is a single variable that should contain the location of your chia executable file. This is the blockchain executable.

* Windows Example: `C:\Users\<USERNAME>\AppData\Local\chia-blockchain\app-1.1.2\resources\app.asar.unpacked\daemon\chia.exe`
* Linux Example: `/usr/lib/chia-blockchain/resources/app.asar.unpacked/daemon/chia`
* Another Linux Example: `/home/swar/chia-blockchain/venv/bin/chia`

### manager

These are the config settings that will only be used by the plot manager.

* `check_interval` - The number of seconds to wait before checking to see if a new job should start.
* `log_level` - Keep this on ERROR to only record when there are errors. Change this to INFO in order to see more detailed logging. Warning: INFO will write a lot of information.

### log

* `folder_path` - This is the folder where your log files for plots will be saved.

### view

These are the settings that will be used by the view.

* `check_interval` - The number of seconds to wait before updating the view.
* `datetime_format` - The datetime format that you want displayed in the view. See here for formatting: https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes
* `include_seconds_for_phase` - This dictates whether seconds are included in the phase times.
* `include_drive_info` - This dictates whether the drive information will be showed.
* `include_cpu` - This dictates whether the CPU information will be showed.
* `include_ram` - This dictates whether the RAM information will be showed.
* `include_plot_stats` - This dictates whether the plot stats will be showed.

### notifications

These are different settings in order to send notifications when the plot manager starts and when a plot has been completed.

### instrumentation

Settings for enabling Prometheus to gather metrics.

* `prometheus_enabled` - If enabled, metrics will be gathered and an HTTP server will start up to expose the metrics for Prometheus.
* `prometheus_port` - HTTP server port.

List of Metrics Gathered

- **chia_running_plots**: A [Gauge](https://prometheus.io/docs/concepts/metric_types/#gauge) to see how many plots are currently being created.
- **chia_completed_plots**: A [Counter](https://prometheus.io/docs/concepts/metric_types/#counter) for completed plots.

### progress

* `phase_line_end` - These are the settings that will be used to dictate when a phase ends in the progress bar. It is supposed to reflect the line at which the phase will end so the progress calculations can use that information with the existing log file to calculate a progress percent. 
* `phase_weight` - These are the weight to assign to each phase in the progress calculations. Typically, Phase 1 and 3 are the longest phases so they will hold more weight than the others.

### global
* `max_concurrent` - The maximum number of plots that your system can run. The manager will not kick off more than this number of plots total over time.
* `max_for_phase_1` - The maximum number of plots that your system can run in phase 1.
* `minimum_minutes_between_jobs` - The minimum number of minutes before starting a new plotting job, this prevents multiple jobs from starting at the exact same time. This will alleviate congestion on destination drive. Set to 0 to disable.

### job

Each job must have unique temporary directories.

These are the settings that will be used by each job. Please note you can have multiple jobs and each job should be in YAML format in order for it to be interpreted correctly. Almost all the values here will be passed into the Chia executable file. 

Check for more details on the Chia CLI here: https://github.com/Chia-Network/chia-blockchain/wiki/CLI-Commands-Reference

* `name` - This is the name that you want to give to the job.
* `max_plots` - This is the maximum number of jobs to make in one run of the manager. Any restarts to manager will reset this variable. It is only here to help with short term plotting.
* [OPTIONAL]`farmer_public_key` - Your farmer public key. If none is provided, it will not pass in this variable to the chia executable which results in your default keys being used. This is only needed if you have chia set up on a machine that does not have your credentials.
* [OPTIONAL]`pool_public_key` - Your pool public key. Same information as the above. 
* `temporary_directory` - Can be a single value or a list of values. This is where the plotting will take place. If you provide a list, it will cycle through each drive one by one. These directories must be unique from one another.
* [OPTIONAL]`temporary2_directory` - Can be a single value or a list of values. This is an optional parameter to use in case you want to use the temporary2 directory functionality of Chia plotting.
* `destination_directory` - Can be a single value or a list of values. This is the final directory where the plot will be transferred once it is completed. If you provide a list, it will cycle through each drive one by one.  
* `size` - This refers to the k size of the plot. You would type in something like 32, 33, 34, 35... in here.
* `bitfield` - This refers to whether you want to use bitfield or not in your plotting. Typically, you want to keep this as true.
* `threads` - This is the number of threads that will be assigned to the plotter. Only phase 1 uses more than 1 thread.
* `buckets` - The number of buckets to use. The default provided by Chia is 128.
* `memory_buffer` - The amount of memory you want to allocate to the process.
* `max_concurrent` - The maximum number of plots to have for this job at any given time.
* `max_concurrent_with_start_early` - The maximum number of plots to have for this job at any given time including phases that started early.
* `initial_delay_minutes` - This is the initial delay that is used when initiate the first job. It is only ever considered once. If you restart manager, it will still adhere to this value.
* `stagger_minutes` - The amount of minutes to wait before the next plot for this job can get kicked off. You can even set this to zero if you want your plots to get kicked off immediately when the concurrent limits allow for it.
* `max_for_phase_1` - The maximum number of plots on phase 1 for this job.
* `concurrency_start_early_phase` - The phase in which you want to start a plot early. It is recommended to use 4 for this field.
* `concurrency_start_early_phase_delay` - The maximum number of minutes to wait before a new plot gets kicked off when the start early phase has been detected.
* `temporary2_destination_sync` - This field will always submit the destination directory as the temporary2 directory. These two directories will be in sync so that they will always be submitted as the same value.
* `exclude_final_directory` - Whether to skip adding `destination_directory` to harvester for farming. This is a Chia feature.
* `skip_full_destinations` - When this is enabled it will calculate the sizes of all running plots and the future plot to determine if there is enough space left on the drive to start a job. If there is not, it will skip the destination and move onto the next one. Once all are full, it will disable the job.
* `unix_process_priority` - UNIX Only. This is the priority that plots will be given when they are spawned. UNIX values must be between -20 and 19. The higher the value, the lower the priority of the process.
* `windows_process_priority` - Windows Only. This is the priority that plots will be given when they are spawned. Windows values vary and should be set to one of the following values:
	* 16384 `BELOW_NORMAL_PRIORITY_CLASS`
	* 32    `NORMAL_PRIORITY_CLASS`
	* 32768 `ABOVE_NORMAL_PRIORITY_CLASS`
	* 128   `HIGH_PRIORITY_CLASS`
	* 256   `REALTIME_PRIORITY_CLASS`
* `enable_cpu_affinity` - Enable or disable cpu affinity for plot processes. Systems that plot and harvest may see improved harvester or node performance when excluding one or two threads for plotting process.
* `cpu_affinity` - List of cpu (or threads) to allocate for plot processes. The default example assumes you have a hyper-threaded 4 core CPU (8 logical cores). This config will restrict plot processes to use logical cores 0-5, leaving logical cores 6 and 7 for other processes (6 restricted, 2 free).
