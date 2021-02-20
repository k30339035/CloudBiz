```
aws ce get-cost-and-usage --time-period Start=2021-02-01,End=2021-02-20  --granularity MONTHLY --metrics "BlendedCost" "UnblendedCost" "UsageQuantity" \ --group-by Type=DIMENSION,Key=SERVICE Type=TAG,Key=Environment \ --filter file://filters.json

# max 14 days and payer account
aws ce get-cost-and-usage --time-period Start=2021-02-19T12:00:00Z,End=2021-02-20T12:00:00Z --granularity HOURLY --metrics "BlendedCost"


# AmortizedCost , BlendedCost , NetAmortizedCost , NetUnblendedCost , NormalizedUsageAmount , UnblendedCost , and UsageQuantity .
aws ce get-cost-and-usage --time-period Start=2021-02-01,End=2021-02-20  --granularity DAILY --metrics "BlendedCost"

aws ce get-cost-and-usage --time-period Start=2021-02-18,End=2021-02-20  --granularity DAILY --metrics "BlendedCost" "UnblendedCost" "UsageQuantity"


aws ce get-cost-and-usage --time-period Start=2021-02-01,End=2021-02-20  --granularity MONTHLY --metrics "BlendedCost"

```