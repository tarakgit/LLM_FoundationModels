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

https://github.com/user-attachments/assets/167c7b39-007f-4c10-97e6-6d26dc2b67bf


### Quick Start with Docker 🐳

> [!NOTE]  
> Please note that for certain Docker environments, additional configurations might be needed. If you encounter any connection issues, our detailed guide on [Open WebUI Documentation](https://docs.openwebui.com/) is ready to assist you.

> [!WARNING]
> When using Docker to install Open WebUI, make sure to include the `-v open-webui:/app/backend/data` in your Docker command. This step is crucial as it ensures your database is properly mounted and prevents any loss of data.

> [!TIP]  
> If you wish to utilize Open WebUI with Ollama included or CUDA acceleration, we recommend utilizing our official images tagged with either `:cuda` or `:ollama`. To enable CUDA, you must install the [Nvidia CUDA container toolkit](https://docs.nvidia.com/dgx/nvidia-container-runtime-upgrade/) on your Linux/WSL system.

### Installation with Default Configuration

- **If Ollama is on your computer**, use this command:

  ```bash
  docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
  ```

- **If Ollama is on a Different Server**, use this command:

  To connect to Ollama on another server, change the `OLLAMA_BASE_URL` to the server's URL:

  ```bash
  docker run -d -p 3000:8080 -e OLLAMA_BASE_URL=https://example.com -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
  ```

- **To run Open WebUI with Nvidia GPU support**, use this command:

  ```bash
  docker run -d -p 3000:8080 --gpus all --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:cuda
  ```

### Installation for OpenAI API Usage Only

- **If you're only using OpenAI API**, use this command:

  ```bash
  docker run -d -p 3000:8080 -e OPENAI_API_KEY=your_secret_key -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
  ```

### Installing Open WebUI with Bundled Ollama Support

This installation method uses a single container image that bundles Open WebUI with Ollama, allowing for a streamlined setup via a single command. Choose the appropriate command based on your hardware setup:

- **With GPU Support**:
  Utilize GPU resources by running the following command:

  ```bash
  docker run -d -p 3000:8080 --gpus=all -v ollama:/root/.ollama -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:ollama
  ```

- **For CPU Only**:
  If you're not using a GPU, use this command instead:

  ```bash
  docker run -d -p 3000:8080 -v ollama:/root/.ollama -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:ollama
  ```

Both commands facilitate a built-in, hassle-free installation of both Open WebUI and Ollama, ensuring that you can get everything up and running swiftly.

After installation, you can access Open WebUI at [http://localhost:3000](http://localhost:3000). Enjoy! 😄

### Other Installation Methods

We offer various installation alternatives, including non-Docker native installation methods, Docker Compose, Kustomize, and Helm. Visit our [Open WebUI Documentation](https://docs.openwebui.com/getting-started/) or join our [Discord community](https://discord.gg/5rJgQTnV4s) for comprehensive guidance.

### Troubleshooting

Encountering connection issues? Our [Open WebUI Documentation](https://docs.openwebui.com/troubleshooting/) has got you covered. For further assistance and to join our vibrant community, visit the [Open WebUI Discord](https://discord.gg/5rJgQTnV4s).


In the last part of the command, replace `open-webui` with your container name if it is different.

Check our Migration Guide available in our [Open WebUI Documentation](https://docs.openwebui.com/tutorials/migration/).



## License 📜

This project is licensed under the [MIT License](LICENSE) - see the [LICENSE](LICENSE) file for details. 📄



