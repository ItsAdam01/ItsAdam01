# Adam Atienza

I build secure systems and research how they fail. Most of my work involves
bridging the gap between software development and defensive operations. I have a
particular interest in identity management, network security, and file system
integrity.

I value operational reliability and clear security logic over theoretical best
practices. My focus is currently on web defense and protecting data at rest
without sacrificing application usability.

## Featured Projects

### Lynx: File Integrity Monitor

I built this host-based IDS in Go to handle real-time monitoring of file system
changes. One of the main hurdles was dealing with 'atomic saves' in modern
editors like Vim and Nano, which trigger multiple kernel events for a single
save. I solved this by implementing a 500ms debouncer to consolidate noise into
accurate alerts. To protect the source of truth, I used HMAC-SHA256 to sign the
baseline. If the agent detects a signature mismatch at startup, it sends an
emergency alert via webhook before shutting down, ensuring the team is never
left in the dark. [View Repository](https://github.com/ItsAdam01/Lynx)

### Network Intrusion Detection & WAF

This is a dual-layer security dashboard that combines network sniffing with
application-level filtering. I used Python and Scapy to inspect traffic, but had
to move to Layer 2 sockets to get full visibility on Linux loopback interfaces.
To keep the alert feed clean, I explicitly excluded the dashboard's own service
ports from SYN flood and port scan tracking. This prevents the system's own
Socket.IO traffic from triggering false positives while still catching actual
external threats.
[View Repository](https://github.com/ItsAdam01/Network-Intrusion-Detection)

### Sentinel Vault: IAM PoC

This project explores identity management and the importance of security
telemetry. Instead of managing raw passwords, I integrated GitHub OAuth 2.0 to
focus on the application's audit trail. I used ua-parser-js to break down User
Agent strings into specific OS and browser profiles. This high-fidelity data
makes it possible to spot session anomalies, like a user suddenly switching
devices or locations during a sensitive operation.
[View Repository](https://github.com/ItsAdam01/Sentinel-Vault)

### Resort Booking Security Hardening

I took a functional prototype and hardened it for production to meet Philippine
Data Privacy Act (DPA) requirements. The biggest challenge was securing guest
PII while keeping the admin dashboard searchable. I settled on a Blind Indexing
pattern: encrypting names and emails with AES-256-GCM for storage, but creating
a separate HMAC-SHA256 index for exact-match searches. This keeps the data
secure but usable for the resort staff.

## Technical Skills

- Security Operations: WAF tuning, Identity & Access Management (IAM), PII
  protection, DPA compliance.
- Languages: Go, Python, TypeScript, JavaScript.
- Tools: Next.js, Payload CMS, Docker, Scapy, Prisma, PostgreSQL, SQLite.

## Contact

- Email: adamatnza01@gmail.com
- Portfolio: ItsAdam01.github.io

I am always looking for complex security problems that require deep research and
practical solutions. Reach out if you want to discuss security or collaborate on
a project.
