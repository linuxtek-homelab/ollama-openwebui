# ollama-openwebui
Configuration for Ollama and OpenWebUI to create chat interface


## Install ROCm (AMD GPU) on Direct Machine
https://rocm.docs.amd.com/projects/radeon/en/latest/docs/install/native_linux/install-radeon.html

Commands:
```
sudo apt update
wget https://repo.radeon.com/amdgpu-install/6.3.2/ubuntu/noble/amdgpu-install_6.3.60302-1_all.deb
sudo apt install ./amdgpu-install_6.3.60302-1_all.deb
sudo amdgpu-install --list-usecase
sudo amdgpu-install --usecase=graphics,multimedia,rocm,rocmdev,rocmdevtools,hip
```


## Using Docker
To run Ollama using Docker with AMD GPUs, use the rocm tag and the following command:
docker run -d --device /dev/kfd --device /dev/dri -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama:rocm

## Adding Models

To add models, can go to:

Admin Panel
    ➡️ Settings
        ➡️Connections
             ➡️ Manage Ollama API connections
                ➡️ Manage Ollama - Pull a model from Ollama.com


Alternatively, in Ollama CLI - would need to go exec into the container and use `ollama pull <modelname>` to download it.  When doing this, need to restart openwebui to pick up the new model.

## References
https://community.amd.com/t5/ai/running-llms-locally-on-amd-gpus-with-ollama/ba-p/713266

https://hub.docker.com/r/ollama/ollama

## Ollama Configuration

https://github.com/ollama/ollama/blob/main/docs/faq.md#how-can-i-enable-flash-attention