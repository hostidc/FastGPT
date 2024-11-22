# ollama-ui workspaces

cd /workspaces/
mkdir /tmp/ollamamodels
export OLLAMA_MODELS=/tmp/ollamamodels
curl -fsSL https://ollama.com/install.sh | sh

export OLLAMA_HOST=0.0.0.0
export OLLAMA_ORIGINS=*

nohup ollama serve > ollama.log 2>&1 &

df -h
ollama run qwen2.5:7b
ollama run llama3.1:8b
ollama pull nomic-embed-text
df -h
cd /workspaces/ollama-ui

nohup make > ui.log 2>&1 &

open http://localhost:8000 # in browser

tail -n 100 -f ollama.log 

