# auto-ai-email-filterHow to Automate Email Categorization with n8n and LLM
I got tired of waiting for Gmail to figure out which emails actually matter to me. After three months of letting AI handle my personal email categorization, I can't imagine going back to manual sorting.

My system is embarrassingly simple: every email gets sorted into one of three buckets by GPT-5-nano. Archive it, read it, or answer it. That's it.

The whole thing runs on n8n and costs me almost nothing since I'm using the cheapest OpenAI model with structured output. Sure, OpenAI now sees all my personal emails, but let's be honest—they probably know more about me from my ChatGPT conversations anyway.

This isn't some theoretical concept I'm pitching. I've been running this in production for three months, and it saves me hours every week.

Why I Built This Email Automation System
I receive way too many emails. Newsletter subscriptions, service notifications, actual important messages from real humans—it all lands in the same inbox. Gmail's built-in categorization kept missing obvious patterns, and I was spending 20 minutes every morning just deciding what to read.

The breaking point came when I realized I was archiving 80% of my emails without reading them. If most emails don't need my attention, why am I the one deciding which ones do?

Prefer Video Tutorial? I've created a step-by-step video demonstration of this entire email automation workflow. Watch Email Automation with n8n and LLM Tutorial to see the complete setup process in action.

Email automation workflow with n8n and LLM demonstration

The Three-Category System That Actually Works
My AI categorizes every email into exactly three options:

Archive - Newsletters I subscribed to but never read, automated notifications, promotional emails
Read - Content I want to consume but don't need to respond to
Answer - Emails that require a human response from me
No complex folder structures. No priority levels. Just three simple actions that cover 100% of my email.

Setting Up the n8n Workflow
Here's the complete n8n workflow that handles everything automatically:

n8n Email Categorization Workflow

The workflow triggers every time a new email arrives in my Gmail inbox. It grabs the email content, sends it to OpenAI for categorization, then applies the appropriate Gmail label and archives emails that don't need my attention.

Required n8n Nodes
You'll need these nodes in your workflow:

Gmail Trigger - Monitors for new emails
OpenAI Chat Model - Categorizes the email content
Gmail - Applies labels and archives emails
IF conditions - Routes emails based on AI decision
The magic happens in the OpenAI node configuration. Here's how I set it up:

OpenAI LLM Node Configuration in n8n

The LLM Prompt That Makes It Work
The prompt is the heart of this system. After testing dozens of variations, this one gives me the most consistent results:

Note: This is just the LLM prompt for email categorization. If you want the complete n8n workflow automation (including all nodes and connections), scroll down to the "Complete n8n Workflow JSON" section below.

I use structured output to ensure the AI always returns a valid category. No parsing errors, no edge cases where the AI gets creative with its response format.

Three Months of Real-World Results
Since implementing this system:

Time saved: About 15-20 minutes per day on email triage
Accuracy: The AI correctly categorizes roughly 95% of emails
Cost: Under $3 per month using GPT-5-nano
False positives: Maybe 2-3 emails per week get miscategorized
The 5% error rate is totally manageable. When the AI gets it wrong, I just move the email to the right category and move on. Still faster than manually sorting everything.

Security Considerations (And Why I'm Okay With Them)
Yes, OpenAI now processes all my personal emails. This isn't ideal from a privacy standpoint, but I made peace with it for a few reasons:

First, I already use a password manager with 2FA codes (not email-based), so email compromise isn't catastrophic. Second, OpenAI already knows plenty about me from regular ChatGPT usage. Third, the time savings are worth the privacy trade-off for my personal workflow.

If you're handling sensitive business emails, you might want to use a local LLM instead of OpenAI's API. The n8n setup works the same way.

Getting Started With Your Own Email Automation
Here's how to build this system yourself:

Set up n8n - Either self-hosted or use n8n Cloud
Connect Gmail - You'll need to authenticate your Gmail account
Get OpenAI API access - Create an account and grab your API key
Import the workflow - I'll share the JSON export if people want it
Customize the prompt - Adjust the categories for your email patterns
Test with a few emails - Start small before automating everything
The whole setup takes about 30 minutes if you're familiar with n8n. Maybe an hour if you're starting from scratch.

Why This Beats Gmail's Built-in Features
Gmail's automatic categorization is designed for everyone, which means it's optimized for no one. My system learns my specific email patterns and preferences.

Plus, I can modify the logic anytime. Want to add a fourth category? Change the prompt. Need different handling for emails from specific senders? Add a condition node. Gmail's rules are rigid; this system adapts to whatever I need.

The Bottom Line
Three months in, this email automation system has become essential to my daily workflow. It's not perfect, but it's way better than manually sorting hundreds of emails every week.

The setup is straightforward, the ongoing costs are minimal, and the time savings are real. If you're drowning in email like I was, this approach might be worth trying.

Just remember: start simple, test thoroughly, and don't automate anything you can't easily undo.

Complete n8n Workflow JSON
For those ready to implement this system, here's the complete n8n workflow you can import directly:

Import Instructions
Copy the JSON above
Save it to a file with the name email-ai-automation-personal.json
In n8n, go to Workflows → Import from JSON
Select the file you saved and click Import
Configure your Gmail and OpenAI credentials
Update the __REPLACE_WITH_YOUR_PROCESSED_LABEL_ID__ with the ID of the label you want to use for the processed emails
Setup email to send in case of error (fallback)
Test with a few emails before enabling the trigger
Remember to update the OpenAI API key and Gmail authentication after importing the workflow.

Video Tutorial: Watch the Complete Email Automation Setup
If you prefer learning visually, I've created a comprehensive video tutorial that walks through the entire process of setting up this email automation system:

Email Automation with n8n and LLM Video Tutorial

The video demonstrates each step of creating the n8n workflow, configuring the OpenAI integration, setting up Gmail connections, and testing the complete automation. You'll see the exact node configurations, the LLM prompt in action, and how the system categorizes real emails in real-time.

Related Articles
