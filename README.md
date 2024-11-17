 # Deploying the static website in azure Storage account and ChatBot
## Project overview:
Deploying the static website in azure storage account and chatbot.
## Project Goal:
 Deploying a responsive and user-friendly static website using Azure
 Storage Account with seamless chatbot integration for interactive user
 engagement and support.
## Project Scope:
 . Static Website: A website that consists of HTML, CSS, andJavaScript files. These files are pre-rendered and don't require server side processing.<br>
 . Azure Storage Account: A cloud storage solution for storing large amounts of unstructured data, including text, images, videos, and more. It can also host static websites.<br>
 . Azure CLI:Acommand-line interface for managing Azure resources.<br>
 . ARM Templates: JSON-based templates that define the infrastructure to be deployed.<br>
 ## Technologies and Azure Services Used:
 1. ARM Templates: Used to automate the deployment of resources including Azure Storage Accounts, Azure Bot Services for the static website and chatbot.
 2. Azure CLI: Can be used in combination with ARM templates for initial setup or to perform additional configurations that are not covered by the ARM template.
 3. Azure Storage Account: ARM template provisions and configures the storage account to enable static website hosting, including creating the $web container.
 4. Azure Bot Service: provides a comprehensive environment for building, deploying, and managing chatbots. It includes integrated
 tools to handle both the backend and frontend aspects of chatbot development.
 5. Web Chat Channel: Used to integrate the chatbot with your website or web application, enabling users to interact with the bot directly from a webpage.
 6. The Direct Line Channel: provides a simple, secure communication line between the bot and external applications (like mobile apps or websites). It can be embedded into a 
 website or mobile app for realtime chat functionality.
 ## Project Approach:
 1. Download and install the Azure CLI from the official website.
 2. Login into the Azure portal by using the command az login.<br>
 ![image alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/8bf27ccb421e15db53474932517828239d7472c0/Triomd/az%20login.png)<br>
 3. Create a resource group using Azure CLI command.
 [az group create--name <resource-group-name>--location <location name> ] <br>
 ![image alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/af38b3f48e9f108d8c2e30988068515017f8396d/Triomd/cli%20resouce.png)<br>
 The resource group with “trio” is created in portal.<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/af38b3f48e9f108d8c2e30988068515017f8396d/Triomd/az%20resource%20group.png)<br>
 4. Create an ARM template by defining your infrastructure resources in a JSON format.<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/af38b3f48e9f108d8c2e30988068515017f8396d/Triomd/arm%20template.png)<br>
 5. Deploy the ARM template by using Azure CLI command.<br>
 [az deployment group create --resource-name <RESOURCE-NAME> --template-file  storageAccountWithWeb.json --parameters storageAccountName=<STORAGE-ACCOUNT-NAME>]<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/af38b3f48e9f108d8c2e30988068515017f8396d/Triomd/cli%20storage.png)<br>
 The storage account “kkm12345” is created in the resource group “trio” in the azure portal.<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/af38b3f48e9f108d8c2e30988068515017f8396d/Triomd/az%20storage.png)<br>
 The container $web is created in the storage account “kkm12345”in the Azure portal.<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/af38b3f48e9f108d8c2e30988068515017f8396d/Triomd/az%20container.png)<br>
 6. Enable the static website using Azure CLI command.<br>
 [az storage blob service-properties update--account-name <STORAGE_ACCOUNT_NAME>--static-website--index-document index.html ]<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/af38b3f48e9f108d8c2e30988068515017f8396d/Triomd/cli%20enable%20static.png)<br>
 We can see the static website is enabled in azure portal.<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/da0578e05c90ef518457e90954c40cd29d56f724/Triomd/az%20static%20enable.png)<br>
 7. Upload the website file using Azure CLI command.
 [az storage blob upload-batch --account-name <STORAGE_ACCOUNT_NAME> --source <SOURCE_DIRECTORY> --destination '$web']
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/da0578e05c90ef518457e90954c40cd29d56f724/Triomd/cli%20upload%20files.png)<br>
 8. You can access your static website using the endpoint provided by Azure.Paste the endpoint in the browser.<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/da0578e05c90ef518457e90954c40cd29d56f724/Triomd/az%20static%20enable.png)<br>
 When the private endpoint is pasted in the browser the website is opened as follows,
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/f06311773bb44e60d50085afec504613d9c0c96b/Triomd/website%20storage.jpg)<br>
 9. In Azure portal search azure ai services and create a language service.<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/f06311773bb44e60d50085afec504613d9c0c96b/Triomd/az%20ai%20service.png)<br>
 10. The language service “kkmlang” is created.
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/f06311773bb44e60d50085afec504613d9c0c96b/Triomd/az%20lang%20.png)<br>
 11. Create language studio in Azure portal.
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/f06311773bb44e60d50085afec504613d9c0c96b/Triomd/az%20lang%20studio.png)<br>
 12. Deploy a file like excel sheet which contains question and answers.<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/f06311773bb44e60d50085afec504613d9c0c96b/Triomd/excel.jpg)<br>
 13. Navigate to channels section and click on web chat ,you will get a screate key and script copy them ,Then go to $web container in which it has index.html file paste the 
 script and secrete key in that and save it.<br>
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/f06311773bb44e60d50085afec504613d9c0c96b/Triomd/webchat.jpg)<br>
 14. Paste the primary endpoint in the browser. We wil get our website with chatbot option.
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/f06311773bb44e60d50085afec504613d9c0c96b/Triomd/chatbotweb.jpg)<br>
 When we click on chatbot  and provide a question from excel sheet we will get as follows,
 ![img alt](https://github.com/KeerthanaVelpuri/storageaccount-project/blob/f06311773bb44e60d50085afec504613d9c0c96b/Triomd/chatbotlast.jpg)<br>
 ## Conclusion:
 In this project, we successfully deployed a static website in an Azure Storage Account and integrated a chatbot powered by Azure’s Language Services. This solution combines 
 two powerful Azure services: Storage Accounts for hosting static web content and Azure Bot Services for building and deploying intelligent chatbots.
 

 
 
 

 
