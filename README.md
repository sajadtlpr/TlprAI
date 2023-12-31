
# TlprAI - AI Cybersecurity Chatbot
```text

  _______ _                   _____  
 |__   __| |            /\   |_   _| 
    | |  | |_ __  _ __ /  \    | |   
    | |  | | '_ \| '__/ /\ \   | |   
    | |  | | |_) | | / ____ \ _| |_  
    |_|  |_| .__/|_|/_/    \_\_____| 
           | |                       
           |_|                       

```

## Introduction

Welcome to TlprAI, an AI-powered cybersecurity chatbot designed to provide helpful and accurate answers to your cybersecurity-related queries and also do code analysis and scan analysis. Whether you are a security researcher, an ethical hacker, or just curious about cybersecurity, TlprAI is here to assist you in finding the information you need.

TlprAI utilizes the powerful language model Meta-LLama2 through the "LlamaCpp" library. This allows TlprAI to respond to your questions in a coherent and relevant manner. Please make sure to keep your queries in English and adhere to the guidelines provided to get the best results from TlprAI.

## Features
- **Local AI/ Runpod Deployment Support:** I have added an option using which you can easily deploy the TlprAI chat interface and use llama in 2 ways:
 - *Using RunPod:* You can use runpod serverless endpoint deployment of llama and connect them to the chatbot by changing the `AI_OPTION` section of the .env file for `Runpod you need to use RUNPOD` and for `Local Llama deployment LOCALLLAMA`. `RUNPOD` & `LOCALLLAMA`
 - *Key Notes:* For the runpod version of the llama to work you need to make sure the `RUNPOD ID` and your `RUNPOD API KEY` are set. 
- **AI Cybersecurity Chat:** TlprAI can answer various cybersecurity-related queries, helping you with penetration testing, security analysis, and more.
- **Interactive Interface:** The chatbot provides an interactive command-line interface, making it easy to have conversations with TlprAI.
- **Clear Output:** TlprAI presents its responses in a well-formatted markdown, providing easily readable and organized answers.
- **Static Code Analysis:** Utilizes the provided scan data or log file for conducting static code analysis. It thoroughly examines the source code without executing it, identifying potential vulnerabilities, coding errors, and security issues.
- **Vulnerability Analysis:** Performs a comprehensive vulnerability analysis using the provided scan data or log file. It identifies and assesses security weaknesses, misconfigurations, and potential exploits present in the target system or network.

The prompt for the model usage looks like this:
```prompt
[INST] <<SYS>> {user_instruction}<</SYS>> NMAP Data to be analyzed: {user_message} [/INST]
```
The instructions looks like this:
```prompt
    Do a NMAP scan analysis on the provided NMAP scan information. The NMAP output must return in a asked format accorging to the provided output format. The data must be accurate in regards towards a pentest report.
    The data must follow the following rules:
    1) The NMAP scans must be done from a pentester point of view
    2) The final output must be minimal according to the format given.
    3) The final output must be kept to a minimal.
    4) If a value not found in the scan just mention an empty string.
    5) Analyze everything even the smallest of data.
    6) Completely analyze the data provided and give a confirm answer using the output format.
    7) mention all the data you found in the output format provided so that regex can be used on it.
    8) avoid unnecessary explaination.
    9) the critical score must be calculated based on the CVE if present or by the nature of the services open
    10) the os information must contain the OS used my the target.
    11) the open ports must include all the open ports listed in the data[tcp] and varifying if it by checking its states value.  you should not negect even one open port.
    12) the vulnerable services can be determined via speculation of the service nature or by analyzing the CVE's found.
    The output format:
        critical score:
        - Give info on the criticality
        "os information":
        - List out the OS information
        "open ports and services":
        - List open ports
        - List open ports services
        "vulnerable services
        - Based on CVEs or nature of the ports opened list the vulnerable services
        "found cve":
        - List the CVE's found and list the main issues.
```

Using the instruction set and the data provided via the prompt the llama AI generates its output.

### Chat:
![TlprAI_chat](https://github.com/sajadtlpr/TlprAI/assets/70637311/01a95209-6037-45c6-aadc-30919abccf7e)

### Static Code analysis:
![code_analysis](https://github.com/sajadtlpr/TlprAI/assets/70637311/52ef1b07-4cf0-464e-91ac-9e3b7d015cb2)

### Vulnerability analysis:
![vuln_analysis](https://github.com/sajadtlpr/TlprAI/assets/70637311/6683b226-425e-4862-b254-f155f8f7b57d)

## Installation

### Prerequisites

Before you proceed with the installation, ensure you have the following prerequisites:

- Python (3.11 or later)
- `pip3` package manager
- `Visual studio Code` - Follow the steps in this link [llama-cpp-prereq-install-instructions](https://github.com/abetlen/llama-cpp-python)
- `cmake`

### Step 1: Clone the Repository

```bash
git clone https://github.com/sajadtlpr/TlprAI.git
cd TlprAI
```

### Step 2: Install Dependencies

```bash
pip3 install -r requirements.txt
```

### Step 3: Download the AI Model

```bash
python3 TlprAI.py
```

The first time you run TlprAI, it will check for the AI model required for the chatbot. If the model is not present, it will be automatically downloaded and saved as "llama-2-7b-chat.ggmlv3.q4_0.bin" in the project directory.

## Usage

To start a conversation with TlprAI, run the following command:

### For Local LLama users
The `.env` file must look like this:
```env
RUNPOD_ENDPOINT_ID = ""
RUNPOD_API_KEY = ""
AI_OPTION = "LLAMALOCAL"
```
After that is done run this.
```bash
python TlprAI.py
```
### For RunPod LLama users
The `.env` file must look like this:
```env
RUNPOD_ENDPOINT_ID = "<<SERVERLESS ENDPOINT ID>>"
RUNPOD_API_KEY = "<<RUNPOD API KEY>>"
AI_OPTION = "RUNPOD"
```
After that is done run this.
```bash
python3 TlprAI.py
```

TlprAI will display a banner and wait for your input. You can ask cybersecurity-related questions, and TlprAI will respond with informative answers. To exit the chat, simply type "quit_bot" in the input prompt.

Here are some additional commands you can use:

- `clear_screen`: Clears the console screen for better readability.
- `quit_bot`: This is used to quit the chat application
- `bot_banner`: Prints the default bots banner.
- `contact_dev`: Provides my contact information.
- `save_chat`: Saves the current session interactions.
- `vuln_analysis`: Does a Vuln analysis using the scan data or log file.
- `static_code_analysis`: Does a Static code analysis using the scan data or log file.

**Note:** I am working on more addons and more such commands to give a more chatGPT experience

**Please Note:** TlprAI's responses are based on the Meta-LLama2 AI model, and its accuracy depends on the quality of the queries and data provided to it.

I am also working on AI training by which I can teach it how to be more accurately tuned to work for hackers on a much more professional level.

## Contributing

We welcome contributions to improve TlprAI's functionality and accuracy. If you encounter any issues or have suggestions for enhancements, please feel free to open an issue or submit a pull request. Follow these steps to contribute:

1. Fork the repository.
2. Create a new branch with a descriptive name.
3. Make your changes and commit them.
4. Push your changes to your forked repository.
5. Open a pull request to the `main` branch of this repository.

Please maintain a clean commit history and adhere to the project's coding guidelines.

## AI training
If anyone with the know-how of training text generation models can help improve the code. For the AI training part, I have prepared a dataset and a working code for the training but I am facing issues with the training part and collaboration on that will be appreciated.
You can view the dataset on :
- [HuggingFace](https://huggingface.co/datasets/morpheuslord/cve-llm-training)
- [GitHub](https://github.com/morpheuslord/CVE-llm_dataset)

The Github version of the dataset is for the OpenAI training and the other is for Llama2-7b from meta. The AIM of the dataset is to try and possibly generate an AI model capable enough to better work with CVE data. If you feel the dataset is lacking then feel free to modify and share your views.

## Contact

For any questions, feedback, or inquiries related to TlprAI, feel free to contact the project maintainer:

- Email: abdullasajad01@gmail.com
- Twitter: [@msajadtlpr](https://twitter.com/sajadtlpr)
- LinkedIn: [ChiranjeeviG](https://www.linkedin.com/in/Abdulla sajad/)
