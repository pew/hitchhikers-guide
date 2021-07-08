# tor

## use SSH via Tor

Just open up Tor Browser, it'll expose the service and port for proxying traffic.

```
ssh -o ProxyCommand="nc -X 5 -x localhost:9150 %h %p" user@example.com
```