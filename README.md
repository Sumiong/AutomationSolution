# NETWORK AUTOMATION ASSIGNMENT (GROUP NO NAME)

## Project Overview: This assignment shows network automation and Linux system monitoring using Docker and Ansible.

This automation project can perform the following tasks:

### Network Device Configuration
- Configuration of Loopback IP Address
- Creation of a secure local user account
- Deployment of login warning banner
- Configuration of interface descriptions
- Add static routes
- Retrieval of device information and export to JSON

### Linux Telemetry Collection
- Hostname
- Current date and time
- CPU information
- Memory usage
- Disk usage
- Logged-in users
- Top 5 CPU-consuming processes

### Automated Report Generation
- Collection of telemetry data
- JSON output files generation
- Produce a final Markdown report using Jinja2 templates

### ------------------------------------------------------------------------------------------------------

## Project Structure

```text
AutomationSolution/
│
├── playbooks/
│   ├── network_config.yml
│   └── linux_telemetry.yml
│
├── templates/
│   └── telemetry_report.md.j2
│
├── .gitignore 
├── device_info.json 
├── docker-compose.yml 
├── final_report.md
├── inventory.ini  
├── linux_telemetry.json
└── site.yml
```

## Technologies Used:
- Docker
- Docker Compose
- Ansible
- Jinja2
- Ubuntu Linux

## Steps to run the project:

### Step 1: Clone Repository
Clone our project repository
```text
git clone <repository-url>
cd AutomationSolution
```

### Step 2: Start the Docker Environment
Build and start all containers, and verify the running containers
```text
docker compose up -d
docker ps
```

| Container | Use |
| -------- | -------- |
| ansible_control | Ansible Control Node |
| sim_router | Simulated Router |
| target_linux | Linux Telemetry Target |

### Step 3: Access the Ansible Control Node
Enter the Ansible container and verify the Ansible installation
```text
docker exec -it ansible_control bash
ansible --version
```

### Step 4: Verify Connection
Test the connectivity to all managed hosts, the results will be SUCCESS
```text
ansible all -i inventory.ini -m ping
```

### Step 5: Execute the Network Automation
Run the network configuration tasks. The **device_info.json** file will be created 
```text
ansible-playbook -i inventory.ini playbooks/network_config.yml
```

### Step 6: Execute the Linux Telemetry Collection
Run the telemetry collection. The **linux_telemetry.json** file will be created 
```text
ansible-playbook -i inventory.ini playbooks/linux_telemetry.yml
```

### Step 7: Run the Complete Automation Workflow
Execute the master playbook. The **final_report.md** file will be created 
```text
ansible-playbook -i inventory.ini site.yml
```

## Summary:

### Files Generated
| File | Descriptiom |
| -------- | -------- |
| device_info.json | Router device information |
| linux_telemetry.json | Linux telemetry data |
| final_report.md | Final telemetry report |

### Sample Output
- Host Information
- CPU Information
- Memory Usage
- Disk Usage
- Logged-in Users
- Top CPU Processes

## Conclusion:
This assignment shows how Ansible can be used in a Docker-based environment to automate report generation, Linux telemetry collection, and network device configuration. Via a repeatable process, the solution lowers the amount of manual configuration work and offers automatic system monitoring.

## Group Members:
| Member | Task |
| -------- | -------- |
| Ong Jin Yie | Infrastructure & Environment Setup |
| Vishali Mogan | Network Automation (Part 1) |
| Mathan Rao Ramavijayan | Network Automation (Part 2) |
| Vibhusha Sampasiva Rao | Linux Telemetry Automation |
| Tishen Santhiragasan | Report Generation & Master Orchestration |
