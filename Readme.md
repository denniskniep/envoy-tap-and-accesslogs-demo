Start envoy
```
sudo docker-compose up
```

Subscribing with Tap via AdminEndpoint to Requests/Responses
```
curl -X POST http://localhost:9901/tap  -H "Content-Type: application/yaml" \
-d 'config_id: downstream_tap
tap_config:
  match_config:
    any_match: true
  output_config:
    sinks:
      - format: JSON_BODY_AS_STRING  
        streaming_admin: {}'\
> traces
```

or looking at the produced access logs in StdOut:

- DownstreamStart
- UpstreamPoolReady
- UpstreamEnd
- DownstreamEnd


Further Reading:
* 
* https://www.funnel-labs.io/2022/09/27/envoyproxy-reverse-proxy/