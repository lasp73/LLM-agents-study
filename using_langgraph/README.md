# Agentes e LLMs com LangChain e LangGraph

Esta seção fala de agentes e aplicações com LLM usando LangChain e LangGraph.

LangChain é um framework para desenvolvimento de aplicações com LLM. LangGraph faz parte do ecossistema do LangChain e permite a orquestração de agentes baseados em LLM. Gosto de pensar que o LangChain oferece o conjunto de componentes e o LangGraph me ajuda a combiná-los para construir agentes com LLM.  

## Frameworks, bibliotecas e ferramentas usadas

Esta seção reúne frameworks, bibliotecas e ferramentas usados nos exemplos.

### UV

Instale o uv (https://docs.astral.sh/uv/getting-started/installation/)

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Ollama

Instale o Ollama (https://ollama.com/download):

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Inicie o Ollama:

```bash
ollama server
```

### Lanfuse

O Langfuse pode ser usado para observar as mensagens trocadas com o LLM.
Siga o processo de instalação e execução local com Docker-Compose:

```bash
git clone https://github.com/langfuse/langfuse.git
cd langfuse
docker compose up
```

Acesse o dashboard do Langfuse: http://localhost:3000/

## Usando modelos locais

Usando o Ollama, podemos baixar e usar os modelos desejados localmente. Claro que isso depende da capacidade de sua máquina (GPU, memória).

O Ollama já vem com alguns modelos pré-carregados, mas você pode baixar outros modelos disponíveis na [documentação do Ollama](https://ollama.com/docs/models).

Por exemplo, baixe o modelo llama3.2 de 3B de parâmetros:

```bash
ollama pull llama3.2
```

## Usando provedores de LLM

Para usar LLMs de provedores como Cerebras, Groq ou OpenAI, você deve configurar a API KEY necessária por meio das variáveis de ambiente configuradas em um arquivo `.env` na base do projeto, por exemplo:

```bash
TAVILY_API_KEY=<INFORME>

CEREBRAS_API_KEY=<INFORME>

GROQ_API_KEY=<INFORME>
```

## Definindo os modelos usados

### Llama

```python
from langchain_ollama import ChatOllama
llm = ChatOllama(
    model="llama3.1", 
    temperature=0.0, 
    max_tokens=1000,
)
```

```python
from langchain_ollama import ChatOllama
llm = ChatOllama(
    model="llama3.2", 
    temperature=0.0, 
    max_tokens=1000,
)
```

Outra possibilidade é usar a função `init_chat_model`.

### Cerebras

```python
from langchain_cerebras import ChatCerebras
llm = ChatCerebras(
    model="llama-3.3-70b",
    temperature=0.0,
    max_tokens=1000,
)
```

```python
from langchain_cerebras import ChatCerebras
llm = ChatCerebras(
    model="llama-3.1-8b",
    temperature=0.0,
    max_tokens=1000,
)
```

### Groq

```python
from langchain_groq import ChatGroq
llm = ChatGroq(
    model="llama3-70b-8192", 
    temperature=0.0, 
    max_tokens=2000,
)
```


## Bibliotecas necessárias

Para executar os códigos apresentados, precisamos antes instalar as bilbiotecas usadas. Essas dependências foram adicionadas ao arquivo `pyproject.toml`, usando o comando `uv add <package>`. Siga as instruções abaixo para instalar essas dependências no ambiente virtual Python com o `uv`.

```bash
# Vá para a pasta do projeto
cd workshop-agentes

# Crie o ambiente virtual com Python 3.11
uv venv --python 3.11

# Instale as dependências do projeto
uv sync
```

## Conteúdo

O objetivo é apresentar um notebook que trate de determinado assunto. Esses conhecimentos podem ser combinados para desenvolver um sistema mais complexo.

1. [Usando LLMs](using-llms.ipynb)

1. [Aplicando RAG](using-rag.ipynb)

1. [Chatbot com memória](chatbot-with-memory.ipynb)

1. [Saída estruturada](structured-output.ipynb)

1. [Gerenciando a memória](managing-memory.ipynb)

1. [Chatbot com LangGraph](chatbot-with-langgraph.ipynb)

1. [Usando ferramentas](using-tools.ipynb)
