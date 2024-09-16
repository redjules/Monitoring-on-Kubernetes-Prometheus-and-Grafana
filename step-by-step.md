This is the architecture we will follow:

![architecture](pics/architecture.png)

We will use GCP to provision the Kubernetes cluster and the commands in the readme:

![GCP_image](pics/GCP.png)

we do kubectl get nodes to see the cluster is ready:

![kgetnodes](pics/kgetnodes.png)

we deploy Prometheus and Grafana with helm following the commands from the readme:

![prometheus](pics/prometheus.png)

![grafana](pics/grafana.png)

We do first portforwarding to access Prometheus:

![portforwarding](pics/portforwarding.png)

After, instead of doing port forwarding we will change the service type top load balancer to access easier:

![loadbalancer](pics/loadbalancer.png)

In Grafana we put Prometheus as data source adn put the Prometheus server URL with the address from the Prometheus we got before

We will trigger a notification with Slack using the slack api, create an App, from scratch. We activate Incoming Webhooks, we choose a channel and create a secret for the alert manager with the webhook url.

We apply the prometheus alertmanagerconfig.yaml and scale down deployment contacts:

![replicas0](pics/replicas0.png)

Now contacts is unavailable and an alert is fired in slack:

![contactsunavailable](pics/contactsunavailable.png)

![slackmessages](pics/slackmessages.png)

To revert it we scale up to 1 replica:

![replicas0](pics/replicas0.png)
