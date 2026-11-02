# noc-network-monitoring-lab
Hands-on NOC lab using Docker, Uptime Kuma, and Nginx to practice network monitoring, outage detection, troubleshooting, and incident response.  Copy
# NOC Network Monitoring & Incident Response Lab

## Project Overview

Built a virtual network monitoring lab using Docker Desktop, Uptime Kuma, and Nginx to practice service availability monitoring, troubleshooting, and incident response.

This project simulates a basic Network Operations Center (NOC) workflow: detecting a service outage, investigating the cause, restoring service, and verifying recovery.

## Technologies Used

- Docker Desktop
- Uptime Kuma
- Nginx
- macOS Terminal
- HTTP/HTTPS
- Docker bridge networking

## Lab Architecture

The lab runs on an Apple Silicon MacBook Air using Docker Desktop.

Two containers communicate over a custom Docker bridge network named `network-lab`.

- **noc-monitor:** Runs Uptime Kuma to monitor services.
- **noc-demo-web:** Runs an Nginx web server used for outage testing.

### Monitoring Targets

| Target | Monitoring Type | Purpose |
|---|---|---|
| Nginx Web Server | HTTP | Monitor internal service availability |
| Example.com | HTTPS | Monitor an external website |

## Incident Simulation — LAB-001

A controlled outage was simulated by stopping the Nginx container.

1. **Detection:** Uptime Kuma reported the web server as DOWN.
2. **Investigation:** Inspected Docker container status and Nginx logs.
3. **Root Cause:** Intentional administrative shutdown.
4. **Resolution:** Restarted the Nginx container.
5. **Verification:** Uptime Kuma returned to UP and reported HTTP 200 OK.

See [Incident Report LAB-001](incident-LAB-001.md) for the complete investigation.

## Troubleshooting Commands

`docker ps -a` — Inspect all containers.

`docker logs --tail 20 noc-demo-web` — Review recent application logs.

`docker stop noc-demo-web` — Simulate an outage.

`docker start noc-demo-web` — Restore the service.

`docker ps` — Verify container status.

## Skills Demonstrated

- HTTP/HTTPS service monitoring
- Basic Docker networking
- Outage detection
- Log analysis
- Incident response
- Service recovery verification
- Technical documentation

## Project Evidence

Monitoring screenshots and a network architecture diagram are stored in the `screenshots` folder.

## Future Improvements

- Add ICMP monitoring for a home router
- Configure alert notifications
- Add DNS monitoring
- Practice additional outage scenarios
