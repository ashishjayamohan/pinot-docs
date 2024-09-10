---
description: This section contains reference documentation for the toEpochBucket functions.
---

# ToEpochBucket

Convert epoch milliseconds to epoch , and divided by bucket size (Bucket size is defined in ). The following time units are supported:

* SECONDS
* MINUTES
* HOURS
* DAYS

## Signature

> ToEpoch\<TIME\_UNIT>Bucket(timeInMillis, bucketSize)

## Usage Examples

```sql
select ToEpochSecondsBucket(1613472303000, 1000) AS bucket
FROM ignoreMe
```

| bucket  |
| ------- |
| 1613472 |

```sql
select ToEpochMinutesBucket(1613472303000, 10) AS bucket
FROM ignoreMe
```

| bucket  |
| ------- |
| 2689120 |

```sql
select ToEpochHoursBucket(1613472303000, 5) AS bucket
FROM ignoreMe
```

| bucket |
| ------ |
| 89637  |

```sql
select ToEpochDaysBucket(1613472303000, 10) AS bucket
FROM ignoreMe
```

| bucket |
| ------ |
| 1867   |
