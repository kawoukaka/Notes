# Linux (Senior SRE Notes)

## Core Concerns
- Process management, signals, and exit codes.
- File descriptors and limits (ulimit).
- Networking stack: ports, TCP states, DNS.

## Operational Practices
- Use systemd for service management and restart policies.
- Monitor disk, inode usage, and IO saturation.
- Maintain consistent time sync (NTP).

## Troubleshooting Mindset
- Start with resource saturation (CPU, memory, disk, network).
- Confirm process health and logs.
- Validate DNS and routing for connectivity issues.

## Failure Patterns
- File descriptor exhaustion.
- Disk full due to log growth.
- Zombie processes or unhandled signals.

## Useful Linux Commands
- `top`: real-time process and resource usage overview.
- `htop`: interactive process viewer with sorting and filtering.
- `ps aux`: snapshot of all running processes.
- `pidstat`: per-process CPU/memory/IO usage over time.
- `free -h`: memory usage summary.
- `vmstat 1`: CPU, memory, and IO stats at 1s intervals.
- `iostat -xz 1`: disk IO utilization and latency.
- `df -h`: disk usage by filesystem.
- `du -sh <path>`: size of a directory or file.
- `lsof -p <pid>`: open files for a process.
- `lsof -i :<port>`: processes listening on a port.
- `netstat -tulpn`: active listeners and ports (legacy).
- `ss -tulpn`: active listeners and ports (modern).
- `ip addr`: network interfaces and IPs.
- `ip route`: routing table.
- `dig <host>`: DNS lookup and resolution details.
- `curl -v <url>`: HTTP request with verbose diagnostics.
- `journalctl -u <service>`: logs for a systemd service.
- `systemctl status <service>`: service status and recent logs.
- `dmesg -T`: kernel ring buffer messages with timestamps.
- `tail -f <file>`: follow a log file in real time.
- `grep -R \"pattern\" <path>`: recursive search for a pattern.
- `awk '{print $1}' <file>`: column-based text processing.
- `sed -n '1,20p' <file>`: print specific line ranges.
- `ln -s <file> <file>`: create symbolic flink.
- `ssh user@host`: connect to remote machine. 
