# Http Probe
HTTP Probe uses GO <a href="https://blog.golang.org/http-tracing"> httptrace </a> module to provide telemetry to each event in a http lifecycle to measure readings for DNS lookup, TCP Connect, TLS Handshake, Time-to-First-Byte, Time-to-Last-Byte and Total Duration. 

Event Readings Calculated includes
1. DNS LookUp Duration 
2. TCP Connect Duration
3. TLS Handshake (if https)
4. Time to First Byte
5. Time to Last Byte
6. Total Duration

If verbosity is enabled, it provides 
1. RemoteServerIP and Port
2. TLS Version in decimal code
3. CipherSuite in decimal code
To obtain the code, please refer to <a href="https://golang.org/pkg/crypto/tls/#CipherSuiteName"> GO TLS </a> library 

<h2> Usage </h2>

