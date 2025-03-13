**Experiment 7: Tracing Website Paths with `tracert`**

**Aim:** To trace the network path to a website using the `tracert` command and understand its options and output.

**Theory:**

`tracert` (Trace Route) is a command-line utility used to determine the route taken by packets across an IP network. It displays each router (hop) along the path to a destination, along with the round-trip time (RTT) for each hop. This helps in diagnosing network connectivity issues and understanding network topology.

**Command Syntax:**


tracert [options] <destination>

* **`<destination>`:** The IP address or hostname of the target website.

**`tracert` Options (Common):**

* **`-d`:** Do not resolve hostnames to IP addresses. This speeds up the process by avoiding DNS lookups.
* **`-h <maximum_hops>`:** Specifies the maximum number of hops to search for the target.
* **`-j <host-list>`:** Specifies loose source routing along the host list.
* **`-w <timeout>`:** Specifies the timeout (in milliseconds) to wait for each reply.
* **`-4`:** Forces the use of IPv4.
* **`-6`:** Forces the use of IPv6.

**Procedure:**

1.  **Open Command Prompt/Terminal:** Open a command prompt (Windows) or terminal (macOS/Linux).
2.  **Execute `tracert`:** Type `tracert <website_address>` (e.g., `tracert google.com`) and press Enter.
3.  **Analyze Output:** Observe the output, which shows the sequence of hops, RTTs, and IP addresses of each router along the path.
4.  **Experiment with Options:** Try using different options (e.g., `tracert -d google.com`) to see their effects.

**Example Output (Windows):**


Tracing route to google.com [142.250.184.142]
over a maximum of 30 hops:
1    <1 ms    <1 ms    <1 ms  192.168.1.1
2     1 ms     1 ms     1 ms  10.0.0.1
3     * * * 172.16.10.1
4    10 ms    11 ms    10 ms  203.0.113.10
5    12 ms    12 ms    13 ms  64.233.174.129
6    11 ms    12 ms    11 ms  142.250.236.177
7    11 ms    11 ms    12 ms  142.250.184.142
Trace complete.

**Explanation of Output Columns:**

* **Hop Number:** The sequence number of each hop.
* **RTT 1, 2, 3 (ms):** Round-trip times in milliseconds for three probes sent to each hop.
* **IP Address/Hostname:** The IP address and, if available, the hostname of the router.
* **`*`:** Indicates a timeout (no response received).

**Analysis:**

* The output shows the path taken by packets from your computer to the destination website.
* The RTT values indicate the latency at each hop. Higher RTTs may indicate network congestion or slow routers.
* `*` indicates a lost packet or a router that is not responding to ICMP echo requests.
* The final line "Trace complete" indicates that the trace has finished successfully.

**Conclusion:**

The `tracert` command is a powerful tool for network diagnostics. By tracing the path to a website, you can identify potential network bottlenecks and understand the route taken by packets across the internet. Experimenting with different options helps in fine-tuning the trace and obtaining more detailed information.

