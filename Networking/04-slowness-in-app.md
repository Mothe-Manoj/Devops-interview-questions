### A user reports that the application is slow.

### 1. Clarify the Scope
- Is the slowness reported by one user or many?
- Is it on specific pages, actions, or times of day?
- Which environment? (Production, staging, etc.)

### 2. Backend API Performance
- Check server response times (via APM tools like New Relic, Datadog, Prometheus).
- Identify slow endpoints or increased latency.
- Look for spikes in request durations.

### 3. Database Slowness

- Monitor CPU and disk I/O on DB server.
- Check for missing indexes.

### 4. Infrastructure & Resource Usage

- Check CPU, memory, disk I/O using:
- ```top, htop, vmstat, iostat```
- Check container or pod resource limits (Kubernetes).
- Scale up if usage is near limits (AutoScaling, HPA).

### 5. Monitor Logs & Alerts
- Check application and server logs for errors or latency.
- Look for recent deployments or changes that may correlate with slowness.
- Verify alert dashboards.

### 6. Caching & CDN Checks
- Is the cache being missed or expired too frequently?
- Is your CDN serving static content properly?
- Validate that backend isn’t overloaded due to missing cache.

### 7. Network or DNS Latency
- Run ping, traceroute, or mtr to check connectivity.
- Check if DNS lookup times are high.
- Consider edge latency if serving users globally.

### 8. After Fix: Monitor & Prevent
- Add better performance alerts (latency, CPU, DB).
- Set SLOs for key endpoints.
- Add automated profiling for slow endpoints.

### Summary:
App slowness can come from frontend, backend, DB, infrastructure, or network. Use a systematic layer-by-layer approach to isolate and fix the issue. Focus first on scope, then verify each component with logs, metrics, and tools.


