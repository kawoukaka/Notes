# Data Quality

## Quality Dimensions
- Accuracy, completeness, timeliness, consistency, uniqueness.
- Freshness: delay between source and availability.

## Practices
- Define data contracts between producers and consumers.
- Validate schemas and enforce type checks.
- Monitor quality metrics and alert on anomalies.

## Real-World Examples
- Null rate checks on critical columns.
- Duplicate detection for event IDs.
- Drift detection for feature distributions.

## Senior mindset
- Treat data quality as a product SLA.
- Automate rollback or quarantine for bad data.
