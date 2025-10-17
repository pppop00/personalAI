# ⚡ Quick Start Guide

Get up and running in 5 minutes!

## 🎯 Super Simple Steps

### 1. Install Python
```bash
# Download from python.org if you don't have it
python --version  # Check if you have Python 3.8+
```

### 2. Install Requirements
```bash
pip install -r requirements.txt
```

### 3. Get OpenAI API Key
1. Go to https://platform.openai.com/api-keys
2. Create new key
3. Copy it

### 4. Create .env File
```bash
# Create a file called .env and add:
OPENAI_API_KEY=your-key-here
```

### 5. Add Your Documents
- Put `.md` files in `oliver-knowledge-base/` folders
- At least one document is needed!

### 6. Run It!
```bash
python app.py
```

### 7. Chat!
- Browser opens automatically
- Ask questions about your documents
- Enjoy! 🎉

## 🆘 Common Issues

**"No documents found"**
→ Add `.md` files to oliver-knowledge-base folders

**"API key not found"**
→ Check your `.env` file is in the right place

**"pip: command not found"**
→ Install Python first

## 💡 Tips

- Each question costs about $0.0001 (very cheap!)
- You can add documents anytime - just rerun the app
- Press Ctrl+C in terminal to stop the app

**That's it!** For detailed instructions, see the main [README.md](README.md)

