#!/bin/bash
#############################
# Run this tool to find projects that you have access to in your GCP organization.
# use gcloud auth print-access-token
##############################

for i in $(gcloud projects list |  sed 1d | cut -f1 -d$' '); do 
    curl -s -X POST -H "Authorization: Bearer \"ya29.axxxxyoutokenhere\"" -H "Content-Type: application/json; charset=utf-8" https://cloudresourcemanager.googleapis.com/v1/projects/$i:getAncestry | jq -c '.ancestor | .[].resourceId | select(.type | IN("project","organization")) | "\(.type)"+":"+ "\(.id)" ' | paste -d "|" - - 
done;
