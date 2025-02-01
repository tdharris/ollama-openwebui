# Self-Host AI with Ollama, OpenWebUI and Authelia

This project provides a Docker-based setup to self-host AI services using Ollama, OpenWebUI and Authelia (OIDC). Follow the instructions below to get started.

## Prerequisites

- Docker
- Docker Compose
- NVIDIA GPU with drivers installed (for GPU acceleration)
- [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html#installation) (if necessary)

## Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/tdharris/ollama-openwebui.git
   cd ollama-openwebui
   ```

2. **Copy the sample environment file and update it with your configuration:**

   ```bash
   cp .env.sample .env
   ```

   Edit the `.env` file to set your specific configuration values.

3. **Build and start the services:**

   ```bash
   docker compose up -d
   ```

   This will start the Ollama and OpenWebUI services.

## Configuration

### Environment Variables

- `OLLAMA_IMAGE_VERSION`: Version of the Ollama image to use (default: `latest`).
- `OLLAMA_PORT`: Port on which Ollama will be accessible (default: `11434`).
- `OPEN_WEBUI_IMAGE_VERSION`: Version of the OpenWebUI image to use (default: `cuda`).
- `OPEN_WEBUI_PORT`: Port on which OpenWebUI will be accessible (default: `3002`).
- `OAUTH_CLIENT_ID`: OAuth client ID for OpenWebUI.
- `OAUTH_CLIENT_SECRET`: OAuth client secret for OpenWebUI.
- `OPENID_PROVIDER_URL`: URL of the OpenID provider.
- `OAUTH_PROVIDER_NAME`: Name of the OAuth provider.
- `OPENID_REDIRECT_URI`: Redirect URI for OpenID authentication.

**Note**: See [Authelia OIDC Open WebUI](https://www.authelia.com/integration/openid-connect/open-webui/) for more information on how to configure Authelia with OpenWebUI.

### Volumes

- `ollama`: Stores Ollama data.
- `open-webui`: Stores OpenWebUI data.

## Usage

### Accessing the Services

- **Ollama**: Accessible at `http://localhost:${OLLAMA_PORT}`
- **OpenWebUI**: Accessible at `http://localhost:${OPEN_WEBUI_PORT}`

### Stopping the Services

To stop the services, run:

```bash
docker compose down
```

### Updating the Services

To update the services to the latest version, pull the latest images and restart the services:

```bash
docker compose pull
docker compose up -d
```

### Download Models

More models can be found on the [Ollama library](https://ollama.com/library)⁠.

To download a model, use the following command:

```console
docker exec -it ollama ollama run llama3
```

**Note**: Replace `llama3` with the model name.

## Troubleshooting

Check the logs of the services if you encounter any issues:

```bash
docker compose logs -f
```

## License

This project is licensed under the MIT License.
