# EC2 Cost Analysis Report

## 1. Inventory Summary
- **Resource**: Troubleshooting Server (Instance ID: `i-0dc7cfd81ebd84a85`)
- **Instance Type**: t3.micro (Burstable Performance Instance)
- **Region**: eu-central-1 (Frankfurt)
- **Status**: Running (Manual lifecycle: Create-Study-Terminate)[cite: 1]

## 2. CloudWatch Performance Observations
- **Metric**: CPU Utilization (Average/Max)[cite: 1]
- **Timeframe**: Last 24 Hours[cite: 1]
- **Observation**: 
    *   The instance shows a baseline CPU utilization of ~0.001%[cite: 1].
    *   Peak utilization reached < 6% during active study sessions[cite: 1].
- **Finding**: The instance is significantly "Over-provisioned" for the current workload, representing a "Right-sizing" opportunity[cite: 1].

## 3. Cost Optimization Actions Taken

### ✅ Storage Optimization (gp2 to gp3 Migration)
- **Action**: Modified the root EBS volume from `gp2` to `gp3`[cite: 1].
- **Benefit**: 
    *   Immediate **20% reduction** in storage costs[cite: 1].
    *   Better baseline performance (3,000 IOPS included) compared to `gp2`[cite: 1].

### ✅ Lifecycle Discipline
- **Action**: Terminating instances immediately after use[cite: 1].
- **Benefit**: Zero "Idle" cost during non-working hours, saving approximately 70% compared to a 24/7 run cycle[cite: 1].

## 4. Recommendations for Future Scaling
1. **Automation**: Implement a Lambda-based "Scheduler" if the environment needs to persist but only during office hours[cite: 1].
2. **Cleanup**: Audit the "Volumes" and "Snapshots" dashboard weekly to ensure no "Available" (orphaned) disks are left behind after instance termination[cite: 1].