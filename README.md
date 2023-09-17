# Public CaaS Use Cases

## [projectmonitoring](./projectmonitoring)

### AlertmanagerConfig for Webex Teams

Preparation:

1. Create a Bot in [Webex Teams](https://developer.webex.com/my-apps/).
2. Grab the generated `access_token` and invite the Bot in a channel (or create a new one).
3. Call the API for the `room_id`

```
curl -s -X GET -H 'Authorization: Bearer XXXXXXXXXXXXX' https://webexapis.com/v1/rooms | jq .
```

4. Create a K8S secret in the namespace where the AlertManager exists
with the Webex API Bearer Token:

```
kubectl -n demoapp create secret generic alertmanager-webex \
  --from-literal=WEBEX_TOKEN='XXXXXXXX' \
```

5. Provide `roomID` in one of these examples:

## [Webex Catchall Example](./projectmonitoring/alertmanagerconfig-webex-all.yaml)
## [Webex Route Example](./projectmonitoring/alertmanagerconfig-webex-route.yaml)

## [gatekeeper](./gatekeeper)

Gatekeeper Constraint Templates
