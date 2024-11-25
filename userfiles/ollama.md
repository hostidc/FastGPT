# ollama-ui workspaces

cd userfiles

mkdir /tmp/ollamamodels
curl -fsSL https://ollama.com/install.sh | sh

export OLLAMA_MODELS=/tmp/ollamamodels

export OLLAMA_HOST=0.0.0.0
export OLLAMA_ORIGINS=*

export OLLAMA_MAX_LOADED_MODELS=3
export OLLAMA_NUM_PARALLEL=5
export OLLAMA_KEEP_ALIVE=-1

nohup ollama serve > ollama.log 2>&1 &

ps -ef |grep ollama

df -h
ollama list
ollama pull qwen2.5:7b
ollama pull llama3.1:8b

ollama pull qwen2.5:3b
ollama pull llama3.2:3b

ollama pull nomic-embed-text:latest


ollama pull gemma2:9b
ollama pull glm4:9b

ollama pull smartcreation/bge-large-zh-v1.5:latest
ollama pull nomic-embed-text:latest
ollama pull davisgao/m3e:latest


df -h
cd /workspaces/ollama-ui

nohup make > ui.log 2>&1 &

open http://localhost:8000 # in browser

tail -n 300 -f ollama.log 
tail -n 300 -f oneapi/logs/oneapi-20241122.log
ifconfig get ipaddress

ps -ef |grep ollama

