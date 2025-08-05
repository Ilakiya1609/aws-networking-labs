# Lab 01: Internet Protocols – Static and Dynamic IP Addresses

## Scenario
A customer (Bob) from a Fortune 500 company reported that their EC2 instance's public IP address changes every time the instance is stopped and started, breaking critical functionality. As a Cloud Support Engineer at AWS, my task was to investigate and provide a solution.

---

## Objectives

- Analyze the difference between static and dynamic IP addresses in EC2
- Replicate the customer's issue
- Assign a persistent Elastic IP to resolve the issue
- Summarize findings for the customer

---

## Investigation Summary

### Step 1: EC2 Setup
- Launched a new EC2 instance in a public subnet
- Enabled "Auto-assign Public IP"
- Assigned a Name tag: `test instance`

### Step 2: Test Public and Private IP Behavior
- Recorded initial Public and Private IPs
- Stopped and started the instance
- Observed:
  - **Public IP changed** → Dynamic
  - **Private IP remained the same** → Static within the subnet

### Step 3: Elastic IP (EIP) Allocation
- Allocated a new Elastic IP
- Associated it with the `test instance`
- Rebooted the instance
- Observed:
  - **Public IP remained the same** → Now static due to EIP

---

## Conclusion

### Problem:
Customer used dynamic public IP, which changes on every stop/start.

### Solution:
Assigned an **Elastic IP (EIP)** to the EC2 instance to make the public IP persistent.

---

## Key Takeaways

| IP Type         | Changes After Stop/Start | Persistent? |
|----------------|---------------------------|-------------|
| Public (default) |    Yes                   |  No        |
| Private         |    No                     |  Yes       |
| Elastic IP      |    No                     |  Yes       |

---

