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
