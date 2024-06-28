# AKV-automation

This repository contains automation scripts for rotating secrets in Azure Key Vault (AKV) using Azure Pipelines. The project is structured with two YAML files: `azure-pipeline.yaml` and `secret-rotation-template.yaml`.

## Repository Structure

- `azure-pipeline.yaml`: Defines the main pipeline, specifying different stages for secret rotation based on the targeted environment (Development, QA, Stage, Production).
- `secret-rotation-template.yaml`: Contains the template for the secret rotation process, including the actual steps for updating secrets in AKV.

## azure-pipeline.yaml

This file sets up a pipeline with different stages for secret rotation, based on the selected environment. It includes parameters for specifying the environment and utilizes a template for the actual rotation process.

### Parameters

- **targetedStage**: The environment where the secrets will be rotated. Options include:
  - Development
  - QA
  - Stage
  - Production

### Stages

Depending on the selected environment, the pipeline triggers different stages:
- `Development`
- `QA`
- `Stage`
- `Production`

Each stage uses the `secret-rotation-template.yaml` to perform the secret rotation.

## secret-rotation-template.yaml

This template defines the steps required to rotate secrets in AKV. It includes parameters for various configurations and stages to perform the rotation and retrieve secret names.

### Parameters

- **libraryVariables**: List of variables to be rotated in AKV.
- **variableGroup**: The variable group to be pushed to AKV.
- **stageName**: Name of the stage.
- **stageDisplayName**: Display name of the stage.
- **vaultName**: Name of the Azure Key Vault.
- **serviceConnectionName**: Name of the service connection for AKV.
- **adoEnvironment**: The Azure DevOps environment.

### Stages

1. **Approval Gate**: An approval step before proceeding with the secret rotation.
2. **rotateSecrets**: The job that performs the actual secret rotation.
3. **getSecretNames**: Retrieves the names of the secrets in the specified AKV.

## How to Use

1. **Clone the Repository**: Clone this repository to your local machine.
2. **Configure the Pipeline**: Update the `azure-pipeline.yaml` file with the appropriate values for your environment.
3. **Run the Pipeline**: Trigger the pipeline from your Azure DevOps project.

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.
