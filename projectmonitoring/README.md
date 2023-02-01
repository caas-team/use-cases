# Example of project monitoring with Alarming in Webex

1. Install demoapp

```bash
kubectl -n demoapp apply -f demoapp-deployment.yaml
kubectl -n demoapp apply -f demoapp-service.yaml
```

2. Configure and install Rancher Project Monitoring

```bash
kubectl -n cattle-project-<project-id> apply -f projecthelmchart.yaml
```

3. Configure and install ServiceMonitor for demoapp

```bash
kubectl -n demoapp apply -f demoapp-servicemonitor.yaml
```

4. Install Dashboard for demoapp

```bash
kubectl -n demoapp apply -f configmap-dashboard-flask.yaml
```

5. Use demoapp

```bash
kubectl -n demoapp apply -f demoapp-job.yaml
sleep 10
kubectl -n demoapp delete -f demoapp-job.yaml
```

6. Configure and install Prometheusrule for demoapp

```bash
kubectl -n demoapp apply -f demoapp-prometheus-rule.yaml
```

7. Configure and install Webex Receiver

see [repo](https://github.com/mcsps/alertmanager-webhook-webex-teams)

8. Review Settings

9. Use demoapp again (wrong to trigger alerts)

```bash
kubectl -n demoapp apply -f demoapp-wrong-job.yaml
sleep 10
kubectl -n demoapp delete -f demoapp-wrong-job.yaml
```

10. Review Results in Alertmanager

11. Review Result in Webex

