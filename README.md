## Build LLM's(foundation models) like Meta Llama 3.2,Google Gemma2, MISTRAL, IBM Granite on local machine using OLLAMA, Docker, Open WebUI 👋

OLLAMA is an open-source platform that allows users to run large language models (LLMs) on Local Machine.

Docker is an open-souce Containerization tool that allows run Open WebUI as  containerized application on local Machine.

Open WebUI is feature-rich, and user-friendly self-hosted WebUI designed to operate entirely offline. It supports various LLM runners, including Ollama and OpenAI-compatible APIs. 

https://github.com/user-attachments/assets/692487f0-0fc7-4338-b513-c4978d557e3a



## How to Install and Configure 🚀

1. **Download and Install OLLAMA on your Local Machine**:

   [Download OLLAMA](https://ollama.com/download) based on your Operating System

   <img width="374" alt="Screenshot 2024-10-31 at 12 42 54" src="https://github.com/user-attachments/assets/64ef3a3b-1f60-4e1d-b040-1efe94632f93">
   
2. **Install LLM models on your Machine from OLLAMA Library**:
   Open your terminal and run the following command to install and run Meta's llama3.2,Google's gemma2,IBM's granite3:

   ```bash
   ollama run llama3.2
   ollama run gemma2:2b
   ollama run granite3-dense
   ```
   
   These commands will install the Meta's llama3.2 and Google's gemma2 2b billion parameter Model , we can add more models like MISTRAL,Microsoft Phi3,llava..
   If we have model downloaded it will run , else it will download the model's and run, Model Details can be found at https://ollama.com/library

   Note: Look for model parameters and size of the model which will have its resemblance in its perfromance inlcuded your personal machine resources.

3. **Install Docker Desktop**:

   [Download](https://www.docker.com/products/docker-desktop/) and Install Docker-Desktop on you local Machine

   <img width="1268" alt="Screenshot 2024-11-01 at 12 43 48" src="https://github.com/user-attachments/assets/bb68baae-fbe9-4af0-8041-92ba1b893cd9">

   Intially you might not see any containers running on Docker Destop , but you would see one container running on port 9000,post running the below command. 
   
4. **Open your terminal and run the following command to install Open WebUI**

   ```bash
   docker run -d -p 9000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open- 
   webui:main
   ```
   
   This will start the Open WebUI server, which you can access at [http://localhost:9000](http://localhost:9000) .The Default port is 8080 but we have mapped it to 9000 in 
   Docker container.

   For Other installation options refer [Open-Webui](https://github.com/open-webui/open-webui?tab=readme-ov-file)

## Model Customization

   You can Customize the model prompts and other parameters like temperature as well.

   Let's Create Model Watson, which can respond like Watson a Professor and also a Scientist.
   
1. **Select the Desired Model of your choice**

   pull the model from OLLAMA Library, here I use llama3.2 as i fell in love with it.

   ```bash
      ollama pull llama3.2
   ```
      
2. **Create a file Modelfile with below content**

   ```bash
       FROM llama3.2
       
       # set the temperature to 1 [higher is more creative, lower is more coherent]
       PARAMETER temperature 1
       
       # set the system message
       SYSTEM """
       You are Watson a scientist and Professor. Respond as a knowledgable  guy who can guide  and answer me.
       """
   ```

3. **Run below command to build the Model with customization**

   ```bash
       ollama create watson  -f ./Modelfile
   ```

4. **Start the model watson**
   ```bash
       ollama run watson
   ```

Lets see the demo

https://github.com/user-attachments/assets/167c7b39-007f-4c10-97e6-6d26dc2b67bf

Enjoy! 😄
