## Build LLM's(foundation models) like Llama 3.2, Gemma2, MISTRAL on local machine using OLLAMA, Docker, Open WebUI 👋

OLLAMA is an open-source platform that allows users to run large language models (LLMs) on Local Machine.

Docker is an open-souce Containerization tool that allows run Open WebUI as  containerized application on local Machine.

Open WebUI is feature-rich, and user-friendly self-hosted WebUI designed to operate entirely offline. It supports various LLM runners, including Ollama and OpenAI-compatible APIs. 

https://github.com/user-attachments/assets/692487f0-0fc7-4338-b513-c4978d557e3a



## How to Install and Configure 🚀

1. **Download and Install OLLAMA on your Machine**:

   [Download OLLAMA](https://ollama.com/download) based on you Operating System
   
   
3. **Install LLM models on your Machine from OLLAMA Library**:
   Open your terminal and run the following command to install and run Meta's llama3.2,Google's gemma2,IBM's granite3:

   ```bash
   ollama run llama3.2
   ollama run gemma2:2b
   ollama run granite3-dense
   ```
   
   These will install the Meta's llama3.2 and Google's gemma2 , 2b billion parameter Model , we can add more models like MISTRAL,Microsoft Phi3,llava..
   If we have teh model istalled it will run , else it will download the model's and run, Model Details can be found at https://ollama.com/library

4. **Install Docker Desktop**:
   Downdload and Install Docker-Desktop on you local Machine
   
5. **Open your terminal and run the following command to install Open WebUI**

   ```bash
   docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open- 
   webui:main
   ```
   
   This will start the Open WebUI server, which you can access at [http://localhost:3000](http://localhost:3000) .The Default port is 8080 but we have mapped it to 3000 in 
   Docker container.


## Model Customization

   You can Customize the model prompts and other parameters like temperature as well.

   Let's Create Model Watson, which can respond like a professor Watson a Professor in Science.


1. **Create a file Modelfile with below content**

   ```bash
    FROM llama3.2
    
    # set the temperature to 1 [higher is more creative, lower is more coherent]
    PARAMETER temperature 1
    
    # set the system message
    SYSTEM """
    You are Watson a scientist and Professor. Respond as a knowledgable  guy who can guide  and answer me.
    """
   ```

2. **Run below command to build the Model with customization**

   ```bash
    ollama create watson  -f ./Modelfile
   ```

3. **Start the model watson**
   ```bash
    ollama run watson
   ```

Lets see the demo

https://github.com/user-attachments/assets/167c7b39-007f-4c10-97e6-6d26dc2b67bf


