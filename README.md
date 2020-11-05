# Http Probe
HTTP Probe uses GO <a href="https://blog.golang.org/http-tracing"> httptrace </a> module to provide telemetry to each event in a http lifecycle to measure readings for DNS lookup, TCP Connect, TLS Handshake, Time-to-First-Byte, Time-to-Last-Byte and Total Duration. 

Event Readings calculated includes
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

Usage: httpProbe [options...] [URL]
Options:
  -v  enable verbosity to include more informations (RemoteServerIP, TLS Version, CipherSuite)
  -f  saving output to json file, the saved json file will be created and save as result.json
  -h  help menu
  URL URL using FQDN only including http or https, TLS requires host header and cannot use only IP Address without host header
  
-f will save the output into a json file, result.json that can be used for other program for consumption. A good example of this is providing reports or the key/value can be used for making geo-routing decision.

<h3>Caveats </h3>
1. Testing has been done on using IP address instead of FQDN. For http request, IP address will work fine (no DNS lookup is performed), for https, httpprobe does not provide a Host Header or SNI, so TLS handshake will fail for most sites. For Https telemetry a FQDN is recommended. <br>
2. Results has been compared with <a href="https://github.com/davecheney/httpstat/blob/master/main.go"> httpstat </a> another great telemetry program written in GO, curl and Firefox. Details can be found in the Wiki.
