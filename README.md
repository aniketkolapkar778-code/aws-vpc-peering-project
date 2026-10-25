# AWS VPC Peering Project

**Name:** Aniket Rajendra Kolapkar  
**Batch:** AWS Internship Batch 1  
**AWS Region:** Asia Pacific (Mumbai) — `ap-south-1`

## Project Overview

This project demonstrates private network communication between two Amazon Virtual Private Clouds (VPCs) using AWS VPC Peering. It covers network planning, subnet configuration, route tables, security groups, EC2 access, connectivity testing, troubleshooting, and resource cleanup.

## Objectives

- Configure two VPCs with non-overlapping IPv4 CIDR ranges.
- Establish a VPC Peering connection.
- Configure forward and return routes.
- Restrict access through security-group rules.
- Validate private connectivity and troubleshoot a controlled connectivity failure.
- Document implementation and cleanup evidence.

## Network Design

| Resource | CIDR / Private IP |
|---|---|
| VPC-A | `10.10.0.0/16` |
| Public subnet A | `10.10.1.0/24` |
| Private subnet A | `10.10.2.0/24` |
| App-A | `10.10.2.10` |
| VPC-B | `10.20.0.0/16` |
| Private subnet B | `10.20.1.0/24` |
| App-B | `10.20.1.10` |

A bastion host in VPC-A was used for administrative SSH access. The application instances had no public IPv4 addresses.

## Implementation

1. Created the VPCs and subnets.
2. Configured the Internet Gateway and route-table associations.
3. Established the VPC Peering connection.
4. Added routes for the remote VPC CIDR in both directions.
5. Configured security groups for SSH administration and ICMP testing.
6. Tested connectivity between the application instances using private IP addresses.

## Testing and Results

- **App-A to App-B:** Four ping replies, with 0% packet loss.
- **App-B to App-A:** Four ping replies, with 0% packet loss.
- **Controlled negative test:** Removing the relevant inbound ICMP Echo Request rule caused 100% packet loss in the tested direction.
- **Recovery test:** Restoring the rule returned the test to four replies, with 0% packet loss.

These results demonstrate the tested private ICMP connectivity and the effect of security-group permissions.

## Security Considerations

- Application instances were accessed through a bastion host.
- SSH and ICMP permissions were scoped to specific source addresses.
- Private IP addresses were used for inter-VPC connectivity tests.
- AWS private keys and credentials must never be committed to this repository.

## Cleanup

Project resources were removed through the AWS Console after evidence collection, as recorded in the project report. The AWS Console and Billing dashboard should be checked to confirm that no billable project resources remain.

## Project Evidence

The accompanying project report and screenshots document the configuration, testing, troubleshooting, and cleanup workflow.

**Note:** The initial pre-peering baseline ping was not captured, so no result is claimed for that test.

## Project Screenshots

Screenshots of the AWS VPC Peering project, from resource creation and connectivity testing to resource cleanup.

### 1. VPC-A Creation
![VPC-A Creation](screenshots/01-vpc-a-create.png)

### 2. VPC-A Details
![VPC-A Details](screenshots/02-vpc-a-details.png)

### 3. VPC-B Creation
![VPC-B Creation](screenshots/03-vpc-b-create.png)

### 4. VPC-B Details
![VPC-B Details](screenshots/04-vpc-b-details.png)

### 5. Subnet Creation
![Subnet Creation](screenshots/05-subnet-create.png)

### 6. Subnet Details
![Subnet Details](screenshots/06-subnet-details.png)

### 7. Route Table Creation
![Route Table Creation](screenshots/07-route-table-create.png)

### 8. VPC Peering Creation
![VPC Peering Creation](screenshots/08-vpc-peering-create.png)

### 9. VPC Peering Acceptance
![VPC Peering Acceptance](screenshots/09-vpc-peering-acceptance.png)

### 10. VPC Peering Details
![VPC Peering Details](screenshots/10-vpc-peering-details.png)

### 11. Security Group List
![Security Group List](screenshots/11-security-group-list.png)

### 12. Security Group Rules
![Security Group Rules](screenshots/12-security-group-rules.png)

### 13. Route Table Routes
![Route Table Routes](screenshots/13-route-table-routes.png)

### 14. EC2 Instances
![EC2 Instances](screenshots/14-ec2-instances.png)

### 15. SSH Connection App-A
![SSH Connection App-A](screenshots/15-ssh-connection-app-a.png)

### 16. SSH Connection Troubleshooting
![SSH Connection Troubleshooting](screenshots/16-ssh-connection-troubleshooting.png)

### 17. SSH Session App-A
![SSH Session App-A](screenshots/17-ssh-session-app-a.png)

### 18. VPC Peering Ping Test
![VPC Peering Ping Test](screenshots/18-vpc-peering-ping-test.png)

### 19. VPC Peering Connectivity Test
![VPC Peering Connectivity Test](screenshots/20-vpc-peering-connectivity-test.png)

### 20. App-A to App-B Ping
![App-A to App-B Ping](screenshots/21-app-a-to-app-b-ping.png)

### 21. App-B to App-A Ping
![App-B to App-A Ping](screenshots/22-app-b-to-app-a-ping.png)

### 22. Ping Test Results
![Ping Test Results](screenshots/23-ping-test-results.png)

### 23. EC2 Instances Terminated
![EC2 Instances Terminated](screenshots/24%20%E2%80%94%20EC2%20instances%20terminated.png)

### 24. Security Groups Deleted
![Security Groups Deleted](screenshots/25%E2%80%94%20security%20groups%20Deletion.png)

### 25. VPC Peering Connection
![VPC Peering Connection](screenshots/26%E2%80%94%20VPC%20Peering%20Connection.png)

### 26. Internet Gateway Detached
![Internet Gateway Detached](screenshots/27-internet-gateway-successfully-detached.png)

### 27. Subnet Deleted
![Subnet Deleted](screenshots/28-Successful-subnet-deletion.png)

### 28. Route Table Deleted
![Route Table Deleted](screenshots/29-Successful-route-table-deletion.png)

### 29. Private Route Table A Deleted
![Private Route Table A Deleted](screenshots/30-Successful-deletion-ewb-rt-a-private-route-table.png)

### 30. Private Route Table B Deleted
![Private Route Table B Deleted](screenshots/31-Successful-deletion-ewb-rt-b-private-route-table.png)

### 31. VPC-B Deleted
![VPC-B Deleted](screenshots/32-Successful-deletion-ewb-vpc-b.png)

### 32. VPC-A Deleted
![VPC-A Deleted](screenshots/33-Successful-deletion-ewb-vpc-a.png)

### 33. Key Pair Deleted
![Key Pair Deleted](screenshots/34-Successful-deletion-1-key-pair.png)








