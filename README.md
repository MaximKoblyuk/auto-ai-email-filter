## Step-by-Step Guide: Automating Email Categorization with n8n and OpenAI

Ready to take control of your inbox? This guide walks you through setting up a simple, powerful email automation system using n8n and an AI model from OpenAI. Let’s get started!

---

### 1. Set Up n8n

- **Option A:** Self-host n8n ([Instructions](https://docs.n8n.io/hosting/installation/))
- **Option B:** Sign up for [n8n Cloud](https://n8n.io/cloud) for a managed service  
Either way, create an n8n account and log in.

---

### 2. Connect Your Gmail Account

- Add a **Gmail Trigger** node in your workflow.
- Authenticate with your Gmail account.
- Set the trigger to fire on new incoming emails.

---

### 3. Get Your OpenAI API Key

- Sign up or log in at [OpenAI](https://platform.openai.com/)
- Navigate to API keys and create a new one.
- Copy the key—you’ll need it for the next step.

---

### 4. Build the Email Categorization Workflow

Add these nodes to your n8n workflow, in order:

1. **Gmail Trigger**: Monitors for new emails.
2. **OpenAI Chat Model**: Sends email text for categorization.
   - Paste your API key into the credentials.
   - Use a prompt like:

     ```
     Categorize this email as one of: Archive, Read, or Answer. Return ONLY the category in structured JSON.
     ```

3. **IF Node(s)**: Evaluates the AI's response.
   - Route emails based on the returned category.

4. **Gmail Node**: Applies labels, archives, or marks emails as needed.

---

### 5. Customize & Test the Workflow

- Adjust the AI prompt to reflect your specific needs or add more categories.
- Set up label IDs for processed emails (replace `__REPLACE_WITH_YOUR_PROCESSED_LABEL_ID__` in the workflow).
- Run some test emails through the workflow to confirm everything works.

---

### 6. (Optional) Set Up Error Handling

- Add a fallback node to send yourself an alert if something goes wrong (e.g., email to self or webhook).

---

### 7. Import Complete Workflow (Advanced)

- Copy the full JSON export (see end of this README).
- Save as `email-ai-automation-personal.json`.
- In n8n: Go to **Workflows → Import from JSON**, select your file, and import.
- Update your Gmail and OpenAI credentials in the workflow.
- Test before enabling live triggers.

---

### 8. Video Walkthrough

Prefer learning visually? Check out the [Email Automation with n8n and LLM Video Tutorial](#) for a full demonstration.

---

### 9. Tips & Best Practices

- **Start simple:** Begin with three categories; add more only if needed.
- **Test thoroughly:** Try with a handful of emails before automating everything.
- **Privacy:** If you want more control over your data, consider using a local LLM instead of OpenAI's API.

---

### 10. Next Steps

- Tweak the workflow to fit your habits.
- Add extra logic for specific senders or email types.
- Enjoy a more organized inbox with minimal manual effort!

---

**Questions?**  
Feel free to open an issue or check out related articles below for more ideas and improvements.
