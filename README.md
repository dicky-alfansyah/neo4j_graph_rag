## Instalasi Frontend :
- Frontend :
  ```bash
  cd frontend
  cp example.env .env
  yarn
  yarn dev
  ```
## Instalasi Backend :
- Backend :
  ```bash
  cd backend
  cp example.env .env
  python3 -m venv .venvNeo4j
  . .venvNeo4j/bin/activate
  pip install -r requirements.txt
  uvicorn main:app
  ```
## Add Support for Custom RAGAS

To enable **RAGAS evaluation** for custom LLMs:

1. Open path `frontend/utils/Constants.ts`
2. Add your model to:

```
export const supportedLLmsForRagas = [
  'deepseek-r1',
  '...........'
];
```

## Backend Setup

To enable **RAGAS evaluation** for custom language models (LLMs), follow these steps:

Open the `.env` file located in the `backend` directory and add the custom model configurations as shown below:

**Example:**
```
LLM_MODEL_CONFIG_deepseek-r1="deepseek-r1,<YOUR_ENDPOINT>,<YOUR_API_KEY>"
LLM_MODEL_CONFIG_deepseek-v3="deepseek-v3,<YOUR_ENDPOINT>,<YOUR_API_KEY>"
LLM_MODEL_CONFIG_gemma3-27b="gemma3:27b,<YOUR_ENDPOINT>,<YOUR_API_KEY>"
LLM_MODEL_CONFIG_llama3.3-70b="llama3.3:70b,<YOUR_ENDPOINT>,<YOUR_API_KEY>"
```

## Frontend Setup

To enable the frontend to support the custom RAGAS models, follow these steps:

Open the `.env` file located in the `frontend` directory and add the custom models in the `VITE_LLM_MODELS` and `VITE_LLM_MODELS_PROD` variables.

**Example:**
```
VITE_LLM_MODELS="deepseek-r1,deepseek-v3,gemma3-27b,llama3.3-70b"
VITE_LLM_MODELS_PROD="deepseek-r1,deepseek-v3,gemma3-27b,llama3.3-70b"
```

## Ports

- **Frontend**: [http://localhost:8080](http://localhost:8080)
- **Backend**: [http://localhost:8000](http://localhost:8000)

## Run Frontend and Backend with PM2

To run both the frontend and backend using pm2, follow these steps:

- Install pm2 :
  ```
  sudo npm install -g pm2
  ```
- Run use pm2 Frontend  :
   ```
  cd frontend
  cp example.env .env
  yarn
  pm2 start "yarn dev" --name frontend-app
  ```
- Run use pm2 Backend  :
   ```
  cd backend
  cp example.env .env
  python3 -m venv .venvNeo4j
  . .venvNeo4j/bin/activate
  pip install -r requirements.txt
  pm2 start "uvicorn main:app" --name backend-app
  ```
## Run Frontend and Backend with Docker Compose

To run both the frontend and backend using Docker with one command, use:
```
docker-compose up -d

```

## Note:
If you encounter an error related to `magiclib`, you can resolve it by installing the required package. Use the following command to install it:

```
pip install python-magic-bin
```
Alternatively, if you need a specific version, use:
```
pip install python-magic-bin==0.4.13
```
## Screenshot

![Screenshot](https://i.ibb.co.com/SwSqrHvr/Screenshot-2025-03-27-001604.png)

![Screenshot](https://i.ibb.co.com/4wNK7gVm/Screenshot-2025-03-27-001501.png)

![Screenshot](https://i.ibb.co.com/ccSgbw7M/Screenshot-2025-03-27-001932.png)
