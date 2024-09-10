---
description: >-
  This section contains reference documentation for the EXPR_MIN and EXPR_MAX
  function.
---

# EXPR\_MIN / EXPR\_MAX

This function scans the given dataset to identify the maximum and minimum values in the specified measuring columns. Once these extreme values (the maxima and minima) are found, the function locates the corresponding entries in the projection column. These entries are associated with the rows where the extreme values were found in the measuring columns. The function then returns these projection column values, providing a way to link the extreme measurements with their corresponding data in another part of the dataset.

## Prerequisite

This function has to be used with the following configuration on the broker:

<pre><code>pinot.broker.query.rewriter.class.names: DEFAULT_QUERY_REWRITERS_CLASS_NAMES + ",org.apache.pinot.sql.parsers.rewriter.ExprMinMaxRewriter"
<strong>pinot.broker.result.rewriter.class.names: "org.apache.pinot.core.query.utils.rewriter.ParentAggregationResultRewriter"
</strong></code></pre>

## Signature

> EXPR\_MIN (projectionCol, measuringCol1, measuringCol2, measuringCol3)
>
> EXPR\_MAX (projectionCol, measuringCol1, measuringCol2, measuringCol3)

## Usage Examples

Find the user with maximum activity. If there are multiple users, break the tie with their last\_activity\_date. If still a tie, break with user\_id. And project user\_id.

```sql
SELECT EXPR_MAX(user_id, activity, last_activity_date, user_id)
FROM userEngagmentTable
```

More useful is that this multiple such aggregation function can be used with GROUP BY

```sql
SELECT user_region, EXPR_MAX(user_id, activity, last_activity_date, user_id),
    EXPR_MIN(user_id, user_satisfaction)
FROM userEngagmentTable
GROUP BY user_region
```

Note:

1. In cases where multiple rows share the same extreme values in the measuring columns, all such rows will be returned by the function.
2. If the goal is to project multiple different columns that correspond to the same set of measuring columns, you can achieve this by invoking the function multiple times, each time specifying a different projection column.
3. This impl does not work with AS clause (e.g. `SELECT exprmin(longCol, doubleCol) AS exprmin` won't work)
4. Putting `exprmin/exprmax` column inside order by clause (e.g. `SELECT intCol, exprmin(longCol, doubleCol) FROM table GROUP BY intCol ORDER BY exprmin(longCol, doubleCol)`) is not supported as semantically ordering multi-column multi-row `exprmin/exprmax` results doesn't make sense
5. Currently projecting MV bytes column doesn't work for now due to an issue

For more detailed examples, see: [https://github.com/apache/pinot/pull/10636](https://github.com/apache/pinot/pull/10636)
