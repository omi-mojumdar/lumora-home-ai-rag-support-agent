# 🤖 Lumora Home — RAG Customer Support Agent

An AI-powered customer support agent built with n8n, Google Gemini, and Pinecone for Lumora Home. It retrieves answers from a company knowledge base using RAG, looks up live order status with identity verification, routes escalations to the right team automatically, and logs every conversation — fully automated, zero manual intervention.

## 🚀 Demo

🎬 [Watch Demo Video](https://drive.google.com/file/d/1jEDK2KoqZZDGY9F4IOWuh-FvyHSFIgij/view?usp=drive_link)  
🌐 [Live Chat](https://lumi-home-conversation.lovable.app/)

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| n8n | Workflow automation engine |
| Google Gemini | LLM for responses + embeddings |
| Pinecone | Vector database for RAG knowledge base |
| Google Sheets | Live order lookup + conversation logging |
| Webhook / Chat Trigger | Customer-facing chat interface |

## 📌 Project Overview

Lumora Home customers struggle with:

❌ Waiting hours for answers to basic support questions  
❌ No way to check order status without calling the business  
❌ Support messages getting missed or going unanswered  
❌ Agents wasting time on repetitive FAQ questions  
❌ No record of past conversations for review or follow-up  

This system solves all of that:

✅ Instantly answers questions from the company playbook using RAG  
✅ Looks up live order status with Order ID + email verification  
✅ Routes complex issues to the right human team automatically  
✅ Logs every conversation to Google Sheets for owner review  
✅ Filters irrelevant queries using a relevance threshold to prevent hallucinated answers  

## ⚡ How It Works

Customer Sends Message
↓
Relevance Check (is query related to Lumora Home?)
Irrelevant? ——→ Polite Out-of-Scope Reply → STOP
↓ Relevant
Pinecone Vector Search (RAG retrieval from playbook PDF)
↓
Order Lookup Intent Check (does query ask about order status?)
Yes ——→ Identity Verification (Order ID + Email match)
Verified? ——→ Google Sheets Order Lookup → Return Status
Not Verified? ——→ Ask for Credentials → STOP
↓ No
LLM Response Generation (Gemini + retrieved context)
↓
Escalation Router (can AI resolve this?)
No ——→ Route to Billing / Technical / General Team
↓ Yes
Send Response to Customer
↓
Conversation Logger (save to Google Sheets)


## 🖥️ Workflow Screenshot

<img width="1913" height="805" alt="image" src="https://github.com/user-attachments/assets/9f5987c7-81d1-4ec3-8c5f-8710bccfd62c" />

## 🔧 Workflow Nodes (10 Nodes)

| Node | Name | Description |
|------|------|-------------|
| 1 | Chat Trigger | Receives customer messages in real time |
| 2 | Relevance Checker | Scores query relevance against Lumora Home topics |
| 3 | Relevance Router | IN SCOPE → continue / OUT OF SCOPE → stop |
| 4 | Pinecone Retriever | Searches vector DB for matching knowledge chunks |
| 5 | Order Intent Detector | Checks if query is about order status |
| 6 | Identity Verifier | Matches Order ID + email against orders sheet |
| 7 | Google Sheets Lookup | Fetches live order data for verified customers |
| 8 | LLM Response Node | Generates answer using Gemini + RAG context |
| 9 | Escalation Router | Routes unresolvable issues to the right human team |
| 10 | Conversation Logger | Saves full conversation log to Google Sheets |

## 📊 Google Sheets Structure

**Orders Table**
- Order ID
- Customer Email
- Customer Name
- Product
- Order Status
- Delivery Date
- Notes

**Conversation Log**
- Timestamp
- Customer Message
- Bot Response
- Escalated (Yes / No)
- Escalation Team
- Session ID

## 💡 What I Learned

- Building a RAG pipeline with Pinecone vector search and Gemini embeddings
- Implementing identity verification logic inside n8n for secure order lookups
- Designing multi-tier escalation routing for different issue types
- Using relevance thresholds to prevent hallucinated out-of-scope answers
- Logging structured conversation data to Google Sheets from n8n
- Managing Pinecone stale chunk deletion during document re-indexing
- Connecting live data sources with AI-generated responses in one unified workflow

## 🔗 Links

- 🎬 [Demo Video](https://drive.google.com/file/d/1jEDK2KoqZZDGY9F4IOWuh-FvyHSFIgij/view?usp=drive_link)
- 📁 [Workflow JSON](https://drive.google.com/file/d/1J3uwdHh6fLNBMpHB_Re0muK-PwlwEb4a/view?usp=drive_link)
- 🌐 [Live Chat](https://lumi-home-conversation.lovable.app/)

## 👤 About Me

**Omi Mojumdar** — AI Automation Freelancer

- 🔗 [LinkedIn](#)
- 📧 omimojumdar88@gmail.com
