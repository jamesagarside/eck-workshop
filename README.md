# eck-workshop

## Documentation
https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-quickstart.html

## Getting Started - Quicktime
`kubectl apply -f elastic-stack/*`

## Getting Started - Step by Step
### Install ECK Operator
https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-deploy-eck.html

`kubectl create -f https://download.elastic.co/downloads/eck/2.12.1/crds.yaml`
`kubectl apply -f https://download.elastic.co/downloads/eck/2.12.1/operator.yaml`

### Create Elasticsearch cluster
`kubectl apply -f elastic-stack/es.yaml`

Check Elasticsearch is running

`kubectl get elasticsearch -w`

### Create Enterprise Search server
`kubectl apply -f elastic-stack/ent-search.yaml`

Check Enterprisesearch is running

`kubectl get enterprisesearch -w`

### Create Maps Search server
`kubectl apply -f elastic-stack/maps.yaml`

Check Maps server is running

`kubectl get elasticmapsserver -w`

### Create Kibana instance
`kubectl apply -f elastic-stack/kb.yaml`

Check Kibana is running

`kubectl get kibana -w`

### Create APM server
`kubectl apply -f elastic-stack/apm.yaml`

Check APM server is running

`kubectl get apm -w`

### Create Agent service account and cluster role
`kubectl apply -f elastic-stack/agent-sa.yaml`


### Create Fleet server
`kubectl apply -f elastic-stack/fleet.yaml`

Check Fleet server is running

`kubectl get agent -w`

### Create Agent instance
`kubectl apply -f elastic-stack/agent.yaml`

Check Agent is running

`kubectl get agent -w`

### Create Logstash instance
`kubectl apply -f elastic-stack/ls.yaml`

Check Logstach is running

`kubectl get logstash -w`

### Deploy Metricbeat for Stack Monitoring
`kubectl apply -f elastic-stack/mon-mb.yaml`

Check Metricbeat is running

`kubectl get beats -w`

### Deploy Filebeat for Stack Monitoring
`kubectl apply -f elastic-stack/mon-fb.yaml`

Check Filebeat is running

`kubectl get beats -w`


### Get Elastic user creds
ECK has already generated the Elastic users credentials and stored them as a secret within the namespace. Run the following to print the cred to STDOUT.
`kubectl get secret quickstart-es-elastic-user -o go-template='{{.data.elastic | base64decode}}'`

### Access Kibana & Login 
[Open Kibana](https://127.0.0.1:30443/)
