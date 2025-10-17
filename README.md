# 🤖 Oliver's Personal AI Assistant

### Talk to your documents using AI! 💬

This is a smart chatbot that reads **your** documents and answers questions about them. It's like having a personal assistant who has read everything you've written!

---

## 🎯 What Does This Do?

Imagine you have hundreds of pages of documents - resumes, LinkedIn profiles, papers, company info. Instead of searching through them manually, you can just **ask questions** like:

- "What projects did I work on?"
- "What are my skills?"
- "Tell me about my experience"

The AI reads all your documents and gives you answers! ✨

---

## 📋 What You Need Before Starting

Don't worry - we'll explain everything step by step!

### 1️⃣ **A Computer**
   - Mac, Windows, or Linux - any computer works!

### 2️⃣ **Python Installed**
   - Python is a programming language
   - Download it here: [python.org](https://www.python.org/downloads/)
   - Choose version 3.8 or newer

### 3️⃣ **An OpenAI Account** (for the AI brain 🧠)
   - Go to: [openai.com](https://openai.com)
   - Sign up for a free account
   - You'll need to add a payment method (costs about $0.01 per chat!)

---

## 🚀 How to Set This Up (Step by Step)

### Step 1: Download This Project

**Option A - Easy Way (Download ZIP):**
1. Click the green "Code" button at the top of this page
2. Click "Download ZIP"
3. Unzip the file on your computer

**Option B - Using Git (if you know how):**
```bash
git clone https://github.com/pppop00/personalAI.git
cd personalAI
```

---

### Step 2: Open Terminal/Command Prompt

**On Mac:**
- Press `Command + Space`
- Type "Terminal"
- Press Enter

**On Windows:**
- Press `Windows key`
- Type "cmd" or "Command Prompt"
- Press Enter

**On Linux:**
- Press `Ctrl + Alt + T`

---

### Step 3: Go to the Project Folder

In the Terminal/Command Prompt, type:

**On Mac/Linux:**
```bash
cd Desktop
cd "Personal AI"
```

**On Windows:**
```bash
cd Desktop
cd "Personal AI"
```

💡 *Tip: The folder might be in "Downloads" instead if you downloaded the ZIP file!*

---

### Step 4: Install the Required Tools

Copy and paste this command, then press Enter:

```bash
pip install -r requirements.txt
```

⏰ *This might take 2-5 minutes. Don't close the window! You'll see lots of text - that's normal.*

---

### Step 5: Get Your OpenAI API Key

1. Go to: [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
2. Click "Create new secret key"
3. Give it a name like "Personal AI"
4. Copy the key (it looks like: `sk-abc123xyz...`)
5. ⚠️ **Save it somewhere safe! You can only see it once!**

---

### Step 6: Create Your Secret Key File

1. In the project folder, create a new file called `.env`
   - On Mac: Right-click → New File → name it `.env`
   - On Windows: New → Text Document → name it `.env` (remove the .txt)

2. Open the `.env` file with any text editor (Notepad, TextEdit, etc.)

3. Type this (replace `your-key-here` with your actual key):
   ```
   OPENAI_API_KEY=sk-abc123xyz...your-actual-key-here
   ```

4. Save and close the file

---

### Step 7: Add Your Documents

1. In the project folder, you should see a folder called `oliver-knowledge-base`
2. Inside it, create folders for different types of documents:
   - `Linkedin` - put LinkedIn profile info here
   - `ResumeLetter` - put resumes and cover letters
   - `Git` - put GitHub project info
   - `Paper` - put research papers
   - `Company` - put company information
   - Any other folders you want!

3. Save your documents as `.md` files (Markdown format)
   - You can convert Word docs to .md using online converters
   - Or just create .md files in any text editor

📝 *Example: Save a file as `my-resume.md`*

---

### Step 8: Run the App! 🎉

In Terminal/Command Prompt, type:

```bash
python app.py
```

✅ **Success!** You'll see:
- Text appearing in the terminal
- A web browser will open automatically
- You'll see a chat interface

---

## 💬 How to Use It

1. The app will open in your web browser
2. You'll see a chat box
3. Type any question about your documents
4. Press Enter and wait for the AI to respond!

**Example Questions:**
- "What jobs have I worked at?"
- "What are my technical skills?"
- "Summarize my education background"
- "What projects did I work on at [company name]?"

---

## 💰 Cost Information

This uses OpenAI's GPT-4o-mini model, which is **very cheap**:
- About **$0.01** for 100 questions
- A full month of heavy use might cost $1-3

You can check your usage at: [platform.openai.com/usage](https://platform.openai.com/usage)

---

## 🆓 Want to Use It for FREE?

You can use **local models** (runs on your computer, no cost):

1. Install Ollama: [ollama.com](https://ollama.com)
2. In Terminal, type: `ollama pull llama3.2`
3. In `app.py`, find this line:
   ```python
   llm = ChatOpenAI(temperature=0.7, model_name=MODEL)
   ```
4. Comment it out and uncomment the next line:
   ```python
   # llm = ChatOpenAI(temperature=0.7, model_name=MODEL)
   llm = ChatOpenAI(temperature=0.7, model_name='llama3.2', base_url='http://localhost:11434/v1', api_key='ollama')
   ```

Now it's completely free! 🎉

---

## 🛠️ Troubleshooting (If Something Goes Wrong)

### Problem: "pip: command not found"
**Solution:** Install Python first from [python.org](https://www.python.org/downloads/)

### Problem: "No module named 'gradio'"
**Solution:** Run `pip install -r requirements.txt` again

### Problem: "OpenAI API key not found"
**Solution:** 
- Make sure your `.env` file is in the right folder
- Make sure it's named `.env` (not `.env.txt`)
- Check that your API key is correct

### Problem: "No documents found"
**Solution:** 
- Add `.md` files to your `oliver-knowledge-base` folder
- Make sure they're in subfolders

### Problem: Browser doesn't open automatically
**Solution:** 
- Look for a link in the terminal like `http://127.0.0.1:7860`
- Copy and paste it into your web browser

---

## 📁 Project Structure

```
Personal AI/
├── app.py                    # Main program (don't change this!)
├── requirements.txt          # List of tools needed
├── .env                      # Your secret API key (create this!)
├── oliver-knowledge-base/    # Put your documents here!
│   ├── Linkedin/            # LinkedIn profiles (.md files)
│   ├── ResumeLetter/        # Resumes and letters (.md files)
│   ├── Git/                 # GitHub project info (.md files)
│   └── ...                  # Add more folders as needed!
└── vector_db/               # Created automatically (don't touch!)
```

---

## 🎓 How It Works (Simple Explanation)

1. **📖 Reading:** The app reads all your `.md` documents
2. **🧩 Chunking:** Breaks them into small pieces
3. **🔢 Embedding:** Converts text into numbers the AI understands
4. **💾 Storing:** Saves everything in a database
5. **❓ Questioning:** When you ask a question, it finds relevant pieces
6. **🤖 Answering:** Sends those pieces to OpenAI to generate an answer

---

## 🔒 Privacy & Security

- ✅ Your documents are stored only on **your computer**
- ✅ Only the relevant parts are sent to OpenAI when you ask questions
- ✅ OpenAI doesn't train on your data (when using API)
- ⚠️ Don't share your `.env` file - it has your secret key!

---

## 🆘 Need More Help?

1. **Create an Issue:** Click the "Issues" tab above and describe your problem
2. **Check Documentation:** See `SETUP_LOCAL_LLM.md` for advanced options
3. **OpenAI Help:** [help.openai.com](https://help.openai.com)

---

## 📝 Credits

- Built with [LangChain](https://www.langchain.com/)
- Powered by [OpenAI](https://openai.com)
- UI by [Gradio](https://gradio.app/)
- Vector Database: [Chroma](https://www.trychroma.com/)

---

## 📜 License

This project is open source and free to use!

---

## ⭐ Like This Project?

Give it a star ⭐ on GitHub to help others find it!

---

**Made with ❤️ by Oliver**

*Last updated: October 17, 2025*

