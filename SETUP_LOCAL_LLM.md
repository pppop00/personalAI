# Setup Guide: Local LLM RAG System

This guide will help you set up the RAG system to use local models (Llama 3.2 or Qwen) instead of OpenAI's API.

## Step 1: Install Ollama

### macOS (you're on macOS)
```bash
# Download and install from https://ollama.ai
# Or use Homebrew:
brew install ollama
```

### Start Ollama service
```bash
ollama serve
```
(Keep this running in a separate terminal window)

## Step 2: Download Models

Choose one or more models to download:

```bash
# Llama 3.2 (1B - fastest, lowest quality)
ollama pull llama3.2:1b

# Llama 3.2 (3B - balanced)
ollama pull llama3.2:3b

# Llama 3.2 (default, usually 3B)
ollama pull llama3.2

# Qwen 2.5 (various sizes)
ollama pull qwen2.5:0.5b  # Smallest
ollama pull qwen2.5:1.5b  # Small
ollama pull qwen2.5:3b    # Medium
ollama pull qwen2.5:7b    # Larger (needs more RAM)
```

## Step 3: Install Python Dependencies

```bash
pip install -r requirements.txt
```

## Step 4: Update Your Code

The key changes made:

1. **Replaced `ChatOpenAI`** with **`ChatOllama`**:
   ```python
   from langchain_ollama import ChatOllama
   
   llm = ChatOllama(
       model="llama3.2",  # or "qwen2.5"
       temperature=0.7,
   )
   ```

2. **Replaced `OpenAIEmbeddings`** with **`HuggingFaceEmbeddings`**:
   ```python
   from langchain.embeddings import HuggingFaceEmbeddings
   
   embeddings = HuggingFaceEmbeddings(
       model_name="sentence-transformers/all-MiniLM-L6-v2"
   )
   ```

3. **Removed OpenAI API key requirement** - everything runs locally!

## Step 5: Run Your Application

```bash
python local_llm_rag.py
```

## Model Recommendations

### For Speed (4-8GB RAM):
- `llama3.2:1b` - Fast, good for simple queries
- `qwen2.5:0.5b` or `qwen2.5:1.5b` - Very fast

### For Quality (8-16GB RAM):
- `llama3.2:3b` - **Recommended balance**
- `qwen2.5:3b` - Also excellent

### For Best Quality (16GB+ RAM):
- `qwen2.5:7b` - High quality responses
- `llama3.1:8b` - Very capable

## Switching Models

To switch models, just change the `MODEL` variable in your code:

```python
MODEL = "qwen2.5:3b"  # Change this line
```

Then restart your application.

## Troubleshooting

### "Connection refused" error
- Make sure Ollama is running: `ollama serve`

### Model not found
- Pull the model first: `ollama pull llama3.2`

### Out of memory
- Try a smaller model (1b or 0.5b versions)
- Close other applications

### Slow embedding generation (first time)
- HuggingFace will download the embedding model on first run
- This is a one-time download (~80MB)

## Performance Comparison

| Model | Size | Speed | Quality | RAM Needed |
|-------|------|-------|---------|------------|
| llama3.2:1b | 1.3GB | ⚡⚡⚡ | ⭐⭐ | 4GB |
| llama3.2:3b | 2GB | ⚡⚡ | ⭐⭐⭐ | 8GB |
| qwen2.5:3b | 2.5GB | ⚡⚡ | ⭐⭐⭐⭐ | 8GB |
| qwen2.5:7b | 4.7GB | ⚡ | ⭐⭐⭐⭐⭐ | 16GB |

## Benefits of Local LLMs

✅ **No API costs** - runs completely free  
✅ **Privacy** - your data never leaves your machine  
✅ **No rate limits** - use as much as you want  
✅ **Works offline** - no internet required after setup  
✅ **Fast** - no network latency  

## Optional: Advanced Configuration

You can customize Ollama settings:

```python
llm = ChatOllama(
    model="llama3.2",
    temperature=0.7,      # Creativity (0-1)
    top_p=0.9,           # Nucleus sampling
    top_k=40,            # Top-k sampling
    num_ctx=2048,        # Context window size
)
```

