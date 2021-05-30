# Ticket-Office

gcloud beta container --project "ticket-office-46601" clusters create-auto "autopilot-cluster-1" --region "europe-central2" --release-channel "rapid" --network "projects/ticket-office-46601/global/networks/default" --subnetwork "projects/ticket-office-46601/regions/europe-central2/subnetworks/default" --cluster-ipv4-cidr "/17" --services-ipv4-cidr "/22"
