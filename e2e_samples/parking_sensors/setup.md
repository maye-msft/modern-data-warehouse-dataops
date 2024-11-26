1. fork the repo to your personal repository and then clone it to your local machine.
    https://github.com/Azure-Samples/modern-data-warehouse-dataops/
2. Create PAT of your github account
3. Create a DevOps project in Azure DevOps
4. Update e2e_samples/parking_sensors/.devcontainer/devcontainer.env with your Azure DevOps project URL and your PAT
5. Add --platform=linux/amd64 in Dockerfile
6. Open the project in devcontainer'
7. az login
8. az devops configure --defaults organization=https://dev.azure.com/<MY_ORG>/ project=<MY_PROJECT>
9. run ./deploy.sh
10. If you need to run the deplument again, please check the service connection in Azure DevOps and remove it. And check the service principal in Azure and remove it. Then run ./deploy.sh again.
11. Follow the instructions about the ADF git integration.



databricks_folder_name="/Workspace/notebooks"

databricks workspace mkdirs ${databricks_folder_name}

databricks workspace import-dir --overwrite "./databricks/notebooks/" "$databricks_folder_name"



databricks fs mkdirs dbfs:/mnt/datalake/sys/databricks/libs/ 

databricks fs cp --recursive --overwrite "./databricks/libs/ddo_transform-localdev-py2.py3-none-any.whl" "dbfs:/mnt/datalake/sys/databricks/libs/ddo_transform-localdev-py2.py3-none-any.whl"

databricks fs mkdirs dbfs:/mnt/datalake/data/lnd/

databricks fs cp --recursive --overwrite "./src/ddo_transform/data" "dbfs:/mnt/datalake/data/lnd/"

