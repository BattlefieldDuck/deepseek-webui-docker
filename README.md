# deepseek-webui-docker

This repository contains the necessary configuration to deploy DeepSeek-R1 and Open WebUI locally using Docker Compose.

## Getting Started

Follow these instructions to get your deployment up and running.

### Prerequisites

Make sure you have Docker and Docker Compose installed on your machine.

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Installation

1. **Clone this repository:**

```bash
git clone https://github.com/BattlefieldDuck/deepseek-webui-docker.git
cd deepseek-webui-docker
```

2. **Build and run the services:**

```bash
docker compose up -d
```

![image](https://github.com/user-attachments/assets/333b66c5-ca79-4f70-80ea-540090c0e7ef)

### Accessing the Web Interface

1. **Open your browser** and go to `http://localhost:3000` to access the Open WebUI interface.

![localhost_3000_auth(Nest Hub)](https://github.com/user-attachments/assets/4bda8a79-b615-4fcc-bf49-e02ee3a08d45)

### Registering an Account

1. **Register a local account** on the Open WebUI.

### Downloading the DeepSeek Model

1. Go to `http://localhost:3000/admin/settings`.
2. Navigate to the **Models** tab.
3. Click **Manage Models**.
4. Enter the model tab and type:

```shell
deepseek-r1:1.5b
```

You can find the list of available DeepSeek-R1 models [here](https://ollama.com/library/deepseek-r1).

![localhost_3000_admin_settings(Nest Hub)](https://github.com/user-attachments/assets/a383eb2f-981c-4765-8a4a-1589dd0d1ace)

Start chatting!

![localhost_3000_admin_settings(Nest Hub) (1)](https://github.com/user-attachments/assets/57fe5387-5018-47db-8eba-d353bf8f8e90)

### Stopping the Services

To stop the services, run:

```bash
docker compose down
```

## Configuration

The `docker-compose.yml` file in this repository includes the following configurations:

```yaml
services:
  open-webui:
    image: ghcr.io/open-webui/open-webui:ollama
    container_name: open-webui
    ports:
      - "3000:8080"
    volumes:
      - ollama:/root/.ollama
      - open-webui:/app/backend/data
    restart: unless-stopped
    # Uncomment the following block if your system has NVIDIA GPUs
    # and you want to leverage GPU acceleration
    #
    # deploy:
    #   resources:
    #     reservations:
    #       devices:
    #         - driver: nvidia
    #           count: all
    #           capabilities: [ gpu ]

volumes:
  ollama:
  open-webui:
```

## Notes

- Ensure that your system's GPU is compatible with NVIDIA drivers, as specified in the `docker-compose.yml` file.
- Modify the `docker-compose.yml` file as needed to fit your specific configuration.
- Check the list of available DeepSeek-R1 models [here](https://ollama.com/library/deepseek-r1).

## Contributing

Feel free to open issues or submit pull requests if you want to contribute.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
