
# ollama-project

**Offline Ollama Deployment Stack with Streamlit, FastAPI, and Docker**

This repository contains a self-hosted, offline-capable large language model (LLM) stack powered by Ollama. It includes a web interface built with Streamlit, an API backend using FastAPI, and Docker Compose for containerized deployment. The stack is designed for secure environments such as legal, healthcare, and air-gapped systems.

---

## Features

- Ollama for local LLM inference (supports LLaMA3, Mistral, and custom models)
- Streamlit frontend for user interaction
- FastAPI backend for model communication
- Whisper, PyTesseract, and FFmpeg for media, audio, and document processing
- Docker Compose for managing multi-container environments
- Fully functional offline with local `.deb` package installation

---

## Technologies

- Python 3.12
- Streamlit
- FastAPI
- Docker and Docker Compose
- Ollama
- Whisper, FFmpeg, PyTesseract

---

## Architecture Overview

```
[User] --> [Streamlit Frontend] --> [FastAPI Backend] --> [Ollama LLM Engine]
                           ↘                ↘
                        [Whisper]        [OCR Tools]
```

- Components are modular and containerized
- Can be hosted locally or with network-attached storage

---

## Project Structure

```
ollama-project/
├── api/                 # FastAPI backend services
├── streamlit_app/       # Streamlit frontend interface
├── offline_pkgs/        # Offline .deb packages for isolated environments
├── docker-compose.yml   # Docker Compose stack file
├── requirements.txt     # Python package list
├── .env                 # Optional configuration variables
└── README.md            # Project documentation
```

---

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/abcomputersatl/ollama-project.git
cd ollama-project
```

### Launch with Docker

```bash
docker-compose up -d
```

This will start the Streamlit frontend and the FastAPI backend. Ollama should be installed and running locally on your machine or in a separate container.

---

## Access

- Streamlit Interface: http://localhost:8501
- FastAPI Swagger Docs: http://localhost:8000/docs
- Ollama API: http://localhost:11434

You can change these ports in the `.env` file or in `docker-compose.yml`.

---

## Offline Deployment

To run this stack in an environment with no internet access:

1. Place required `.deb` packages in the `offline_pkgs/` directory
2. Modify Dockerfiles to install packages from local sources only
3. Use pre-downloaded Python wheels (optional) if pip cannot access PyPI
4. Pre-build and export Docker images as `.tar` files if deploying elsewhere

An NFS-mounted share can be used to manage large model files securely.

---

## Customization

- Store local models in `ollama/models/`
- Edit `main.py` in `streamlit_app/` to change UI logic
- Modify or extend `api/routes/` in the FastAPI service for custom API endpoints

---

## Development and Rebuild

To rebuild everything from scratch:

```bash
docker-compose down -v
docker-compose build
docker-compose up
```

To stop and remove containers:

```bash
docker-compose down
```

---

## License

This project is licensed under the MIT License. You may freely use, modify, and distribute the code with attribution. Refer to the [LICENSE](LICENSE) file for details.

---

## Contributing

Contributions are welcome. Please open issues or submit pull requests for enhancements, bug fixes, or documentation improvements.

---

## Maintainer

Marcusfixmyphone  
GitHub: [@abcomputersatl](https://github.com/abcomputersatl)  
Da Lab MSP | Denver, Colorado

---

Built for secure, offline AI deployment and professional environments where privacy and performance are essential.
