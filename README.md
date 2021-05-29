# Ticket-Office

gcloud beta container --project "ticket-office-98746" clusters create "cluster-1" --zone "europe-central2-a" --no-enable-basic-auth --cluster-version "1.20.6-gke.1000" --release-channel "rapid" --machine-type "e2-medium" --image-type "COS_CONTAINERD" --disk-type "pd-standard" --disk-size "100" --metadata disable-legacy-endpoints=true --scopes "https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/monitoring","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management.readonly","https://www.googleapis.com/auth/trace.append" --num-nodes "3" --enable-stackdriver-kubernetes --enable-ip-alias --network "projects/ticket-office-98746/global/networks/default" --subnetwork "projects/ticket-office-98746/regions/europe-central2/subnetworks/default" --no-enable-intra-node-visibility --default-max-pods-per-node "110" --no-enable-master-authorized-networks --addons HorizontalPodAutoscaling,HttpLoadBalancing,GcePersistentDiskCsiDriver --enable-autoupgrade --enable-autorepair --max-surge-upgrade 1 --max-unavailable-upgrade 0 --enable-shielded-nodes --node-locations "europe-central2-a"




---
apiVersion: "v1"
kind: "ConfigMap"
metadata:
  name: "nginx-1-config-kjzy"
  namespace: "default"
  labels:
    app: "nginx-1"
data:
  POSTGRES_PASSWORD: "password"
  POSTGRES_USER: "user"
  POSTGRES_DB: "db_name"
  DATABASE_HOST: "database_host"
  DATABASE_PORT: "5432"
  DATABASE_SOCKET: " "
---
apiVersion: "apps/v1"
kind: "Deployment"
metadata:
  name: "nginx-1"
  namespace: "default"
  labels:
    app: "nginx-1"
spec:
  replicas: 3
  selector:
    matchLabels:
      app: "nginx-1"
  template:
    metadata:
      labels:
        app: "nginx-1"
    spec:
      containers:
