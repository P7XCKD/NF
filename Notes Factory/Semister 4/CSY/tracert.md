### Tracert Commands with Examples and Uses

- **Command:** `tracert [hostname]`
  - **Example:** `tracert google.com`
  - **Use:** This command is used to trace the route packets take to a destination host, showing all the intermediary routers.

- **Command:** `tracert -d [hostname]`
  - **Example:** `tracert -d google.com`
  - **Use:** This command prevents the DNS resolution of hostnames, displaying only IP addresses in the trace.

- **Command:** `tracert -h [max_hops] [host]`
  - **Example:** `tracert -h 10 google.com`
  - **Use:** This command limits the trace to a specified number of hops (routers).

- **Command:** `tracert -w [timeout] [host]`
  - **Example:** `tracert -w 5000 google.com`
  - **Use:** This command sets a timeout in milliseconds for each hop, useful for controlling how long to wait for a response.

- **Command:** `tracert -4 [hostname]`
  - **Example:** `tracert -4 google.com`
  - **Use:** This command forces the trace to use IPv4 addresses only, bypassing IPv6 if available.

- **Command:** `tracert -6 [hostname]`
  - **Example:** `tracert -6 google.com`
  - **Use:** This command forces the trace to use IPv6 addresses only.