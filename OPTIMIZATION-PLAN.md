# EC2 Cost Optimization Plan

## 1. Executive Summary
This plan outlines the technical strategies to minimize AWS EC2 expenditures while maintaining system performance and reliability.[cite: 1]

## 2. Targeted Optimization Strategies

### A. Instance Right-Sizing
- **Current State**: t3.micro is running at < 1% CPU utilization.[cite: 1]
- **Target**: Evaluate switching to `t3.nano` if memory allows, or moving to `AWS Lambda` for event-driven tasks.[cite: 1]
- **Estimated Savings**: Up to 50% of the compute cost per instance.[cite: 1]

### B. Automated Scheduling (Start/Stop)
- **Objective**: Implement automated scripts to stop instances during non-study hours (e.g., 8 PM to 8 AM).[cite: 1]
- **Tooling**: Use `AWS Instance Scheduler` or a custom `Lambda + EventBridge` function.[cite: 1]
- **Estimated Savings**: ~70% savings by running 60 hours/week instead of 168 hours.[cite: 1]

### C. Storage Lifecycle Management
- **Action 1**: Enforce `gp3` as the default volume type for all new instances.[cite: 1]
- **Action 2**: Enable "Delete on Termination" for all non-critical EBS volumes.[cite: 1]
- **Action 3**: Setup a monthly script to identify and delete "Available" (unattached) EBS volumes and old snapshots.[cite: 1]

## 3. Implementation Roadmap
- **Phase 1**: Manual cleanup of orphaned Elastic IPs and EBS volumes.[cite: 1]
- **Phase 2**: Migration of existing `gp2` volumes to `gp3`.[cite: 1]
- **Phase 3**: Automation of instance power-cycling using AWS CLI or SDK.[cite: 1]