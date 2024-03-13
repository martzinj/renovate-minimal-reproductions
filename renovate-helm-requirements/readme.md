# Renovate minimal reproduction
This is a Renovate minimal reproduction Repo to reproduce the issue that Renovate cannot check for new Helm Chart versions when using a custom AWS ECR OCI registry.

## Current behavior
Renovate cannot check for new Helm Chart versions due to the "invalid-url" error.

Log output:
````bash
"helm-requirements": [
{
    "deps": [
    {
        "depName": "external-secrets",
        "currentValue": "0.1.2",
        "registryUrls": [
        "aws-account-id.dkr.ecr.eu-central-1.amazonaws.com/charts"
        ],
        "skipReason": "invalid-url",
        "updates": [],
        "packageName": "external-secrets"
        }
    ]
    }
````

## Expected behavior
Renovate checks whether new Helm Charts are available in the private AWS ECR OCI registry. 

## In this Repo

````bash
├── env
│   └── prd-cluster
│       └── app
│           ├── Charts.yaml
│           ├── requirements.yaml
│           └── values.yaml
├── readme.md
└── renovate.json 
````

### app Folder
Contains all helm3 specific files.

### renovate.json
Contains a not working example to replace/set the correct registryURL + depName path.