1. fork the repo to your personal repository and then clone it to your local machine.
    https://github.com/Azure-Samples/modern-data-warehouse-dataops/
2. Create PAT of your github account
3. Create a DevOps project in Azure DevOps
4. Update e2e_samples/parking_sensors/.devcontainer/devcontainer.env with your Azure DevOps project URL and your PAT
5. Add --platform=linux/amd64 in Dockerfile
6. Open the project in devcontainer