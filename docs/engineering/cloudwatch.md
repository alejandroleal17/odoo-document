

---

### CONSULTING LOGS IN CLOUDWATCH
In Cloudwatch, use these Fluent queries for log extraction.

For a complete overview of Cloudwatch, review the documentation: [here](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)

Steps to perform the queries:
 1. Go to AWS Cloudwatch.
 2. Select the N. Virginia region.
 3. Select Logs > Logs Insights.
 4. Select the log group: fluent-bit-cloudwatch.
 
## Log Extraction:

 You can consult the endpoint by changing the @logStream for the required application or API, for example:

- `dataintegrator-worker-production` for Workers logs.
- `navigator-api-production` for Navapi log queries.
- `dataintegrator-production` for scheduler-related logs.
 
Example:
```plaintext
fields @message 
| sort @timestamp asc
| limit 10000
| filter @logStream like /dataintegrator-worker-production/ 
| filter @message like /Task Consumed/
```

## Verifying Logs:

```plaintext
fields @timestamp, @message, @logStream, @log
| sort @timestamp desc
| filter @logStream like /dataintegrator-worker-production/
| limit 10000
```

or 

```plaintext
fields @message 
| sort @timestamp asc
| limit 10000
| filter @logStream like /dataintegrator-worker-production/ 
| filter @message like /Task Consumed/
```

This allows us to see the tasks consumed (fully executed) by the workers.

```plaintext
fields @timestamp, @message, @logStream, @log
| sort @timestamp desc
| filter @logStream like /dataintegrator-worker-production-*/
| filter @message like /troc.worked_hours/
| limit 20
```

```plaintext
fields @timestamp, @message, @logStream, @log
| sort @timestamp desc
| filter @logStream like /dataintegrator-worker-production/
| filter @message like /deals_dormant/
| limit 20
```

To validate specific execution time, filter by @timestamp:

```plaintext
fields @timestamp, @message, @logStream, @log
| sort @timestamp desc
| filter @logStream like /dataintegrator-worker-production/
| filter @timestamp >= 1698409500798 and @timestamp <= 1698409500898
| limit 300
```

---