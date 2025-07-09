## 📌 Project: Email Automation with n8n

Demonstration of no-code automation using n8n, where contact data from a Google Sheet is read and personalized emails are sent via Gmail SMTP.

<img src="Screenshot (1103).png" alt="Screenshot" width="400"/>

## 🚀 Workflow Overview

The automation performs the following steps:

1. **Trigger** – A Schedule node to start the workflow manually or at set times
2. **Google Sheets Node** – Reads rows of contact data
3. **SplitInBatches** – Iterates through each contact
4. **Send Email Node** – Sends a customized email using SMTP credentials

---

## 📝 Sample Google Sheet Data

| Name  | Email             | Company    | CustomMessage                      |
|-------|-------------------|------------|------------------------------------|
| Riya  | riya@example.com  | Alpha Inc  | Here's your onboarding doc.        |
| Aarav | aarav@example.com | Beta Ltd.  | See you at the kickoff call.       |
| Kiran | kiran@example.com | Delta Corp | Welcome aboard, let’s get started! |


---


### 📂 Files:
- `workflow.json` - exported n8n workflow
- `workflow.png` - screenshot of the workflow
- 🔗 View-only sample sheet: [Google Sheet Link](https://docs.google.com/spreadsheets/d/1UcEXq1SiNRUdXt57SeVi1e-5zSgqY2PG5u_09CJzLeM/edit?usp=sharing)

Example template:

####Subject: 
```
Welcome to {{ $json["Company"] }}, {{ $json["Name"] }}!
```

####Body:

```
Hi {{ $json["Name"] }},
We're excited to have you on board at {{ $json["Company"] }}.
{{ $json["CustomMessage"] }}
Best regards,
GigFloww
```

### 🔧 Tech Stack:
- [n8n](https://n8n.io/) – Automation workflow builder
- [Google Sheets](https://sheets.google.com/) – For storing contact info
- Gmail SMTP – To send customized emails
- [Docker](https://www.docker.com/) – To run n8n locally
- [ngrok](https://ngrok.com/downloads) (static domain) – For exposing local instance securely online


## For ngrok :

👉 Download ngrok and unzip
```
ngrok config add-authtoken <YOUR_NGROK_AUTH_TOKEN>

ngrok http --domain=your-subdomain.ngrok.io 5678
```


## For Docker :
👉 Download and Install 
use docker image 
Search >n8nio/n8n > Pull > Run 

N8N_ENVIRONEMTN_URL > place the static domain url from ngrok

WEBHOOK_URL > place the static domain url from ngrok

```
docker pull n8nio/n8n
```

```
docker run -it --rm \
  -p 5678:5678 \
  -e N8N_ENVIRONMENT_URL=https://your-subdomain.ngrok.io \
  -e WEBHOOK_URL=https://your-subdomain.ngrok.io \
  n8nio/n8n

```

** update port if 5678 doesn't work
