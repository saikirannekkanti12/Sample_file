# create fleet in gcloud
gcloud container fleet create --display-name=my-gke-fleet

# required api enable for commuincation
gcloud services enable anthos.googleapis.com 

# create auto cluster and standard cluster
gcloud container clusters create-auto --async \
gke-cluster-01-ap --region REGION \
--release-channel rapid --labels mesh_id=proj-PROJECT_NUMBER \
--enable-fleet

gcloud container clusters create \
gke-cluster-02-st --zone ZONE \
--release-channel rapid --num-nodes 2 --labels mesh_id=proj-PROJECT_NUMBER \
--workload-pool=PROJECT.svc.id.goog --gateway-api=standard --enable-fleet --machine-type e2-standard-2

# listing cluster 
gcloud container clusters list

# Manage fleet-level features 
*/ Service Mesh
Config Sync
Continuous validation for Binary Authorization
Policy Controller
Security posture /*

gcloud container fleet mesh enable 
  
