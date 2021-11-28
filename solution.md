# Logging

Assignments

1. List some logging and visualization tools available in the market with the preferred senario to use one over other.
2. Mention 10 best practises when logging. Why is log formatting necessary?
3. Create a file in your system. Whenever a someone performs some action(read, write, execute) on that file, the event should be logged somewhere.
4. install logstash in your system. download a sample nginx log from [https://github.com/elastic/examples/blob/master/Common%20Data%20Formats/nginx_logs/nginx_logs](https://github.com/elastic/examples/blob/master/Common%20Data%20Formats/nginx_logs/nginx_logs) , parse the logs using logstash. The parsed output must contain the geogriphical information like country, state etc. that the request is originating from. save the parsed output to a file in your system.

## Q.1.

**Splunk**

Use cases:

- For network monitoring and detecting security issued

**ElasticSearch**

Use cases:

- Large volume of log and performance is of importance

**Kibana:**

Use cases:

- When you need to visualize the data
- Generate reports
- Analytics and insights are needed

**Datadog:**

- ease of use
- faster time to market

## Q.2.

Some of the logging best practices are as:

- Never ever log sensitive information
- Always log in text format and try to follow a format for eg syslog
- Use timestamp for every event and make the time uniform by logging UTC
- Use categorization and severity for eg; CRITICAL, DEBUG, INFO etc
- Log locally to files so that logs are not lost due to backpressure
- Rotate the logs using rotation policy. Your disk will be full if you go on collecting everything. So rotate logs at periodic interval.
- Make the logs human readable and as developer friendly as possible.
- Identify the sources that generated the log and include it in the logs.
- Add context to your log messages
- Don't log to too much or too little
- Make you log easy to parse
- Log for compliance purposes as well

References:

[https://dev.splunk.com/enterprise/docs/developapps/addsupport/logging/loggingbestpractices/](https://dev.splunk.com/enterprise/docs/developapps/addsupport/logging/loggingbestpractices/)

[https://www.comparitech.com/net-admin/log-management-tools/](https://www.comparitech.com/net-admin/log-management-tools/)

[https://www.sentinelone.com/blog/the-10-commandments-of-logging/](https://www.sentinelone.com/blog/the-10-commandments-of-logging/)

## Q.3.

### Step 1: Setup auditd

1.1 Install `auditd`

```bash
	sudo apt install auditd
```

1.2 Enable it at startup

```bash
systemctl enable auditd
```

![Untitled](Logging%2004eabc7058434496adc812647979ed56/Untitled.png)

1.2 Optional

Configure the `auditd` log file stored at `sudo nano /etc/audit/auditd.conf`

### Step 2: Watch the file

2.1 Create a file

```bash
touch sample_file
echo "anything" >> sample_file
```

2.2 Watch the file using `auditctl`

```bash
sudo auditctl -w sample_file -p rwxa
```

2.3 Watch the logs at  `/var/log/audit/audit.log` by  default, the audit system logs audit messages to the `/var/log/audit/audit.log` file.

## Q.4.
