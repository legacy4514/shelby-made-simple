# Shelby CLI Setup Guide (WSL)

This guide walks you through setting up the **Shelby CLI** on **Windows Subsystem for Linux (WSL)** and uploading your first file. It is written for both technical and non-technical users, with clear steps you can follow directly from your terminal.

---

## What is Shelby?

Shelby is a decentralized hot storage network designed for fast uploads and quick access to data. It runs on a dedicated fiber network and is built to support modern, data-heavy applications.

### Key Features

* Simple file uploads
* Fast data retrieval
* Global network coverage
* Ready for developers and applications

### Common Use Cases

* AI-ready data access
* Content that earns value when read or accessed
* Serving real-world data at scale
* Creator-owned data platforms

---

## What You’ll Need

Before you begin, make sure you have:

* **Windows Subsystem for Linux (WSL)** (Ubuntu recommended)
* **Node.js**
* **npm** (Node Package Manager)
* **Shelby CLI**

---

## Step 1: Install Node.js and npm in WSL

First, update your package list:

```bash
sudo apt update
```

Enter your password when prompted.

Next, install Node.js and npm:

```bash
sudo apt install nodejs npm -y
```

Verify that both are installed correctly:

```bash
node --version
npm --version
```

---

## Step 2: Install the Shelby CLI

Install the Shelby CLI globally using npm:

```bash
npm install -g @shelby-protocol/cli
```

Check that the installation worked:

```bash
shelby --version
```

---

## Step 3: Initialize the Shelby CLI

Start the setup process:

```bash
shelby init
```

During initialization, you will be asked for an **API key**.

### Getting an API Key

1. Visit the [GEOMI](https://geomi.dev/)
2. Create an account (if you don’t already have one)
3. Go to **Overview**
4. Click **Create API Keys**
5. Fill in the form:

   * **Network**: Select *Shelbynet*
   * **Resource Name**: Any descriptive name
   * **Usage Description**: Short explanation of how you’ll use Shelby
6. Create the API key

Copy the API key and paste it into your terminal when prompted.

### CLI Prompts (Recommended Choices)

* Create or update account: **Yes**
* Default name: press **Enter**
* Signature scheme: press **Enter**
* Private key: leave **blank**

Your configuration will be saved to:

```
~/.shelby/config.yaml
```

### Verify Initialization

View your config file:

```bash
cat ~/.shelby/config.yaml
```

List available networks:

```bash
shelby context list
```

List your accounts:

```bash
shelby account list
```

Take note of your **account address** — you’ll need it for funding.

---

## Step 4: Fund Your Account

You need **two types of tokens**:

* **APT** – for transaction (gas) fees
* **ShelbyUSD** – for uploads and downloads

Get the faucet link:

```bash
shelby faucet --no-open
```

Open the link in your browser and click **Fund** to receive both tokens.

Check your balance:

```bash
shelby account balance
```

You should see both **APT** and **ShelbyUSD** listed.

---

## Step 5: Upload Your First File

Create a simple test file:

```bash
echo Hello > test.txt
```

Upload the file to Shelby:

```bash
shelby upload ~/test.txt files/test.txt -e tomorrow --assume-yes
```

### About Expiration

Each upload requires an expiration time. Examples you can use:

* `tomorrow`
* `in 2 days`
* `next Friday`
* `2025-12-31`

---

## Step 6: Verify and Download

List all stored files:

```bash
shelby account blobs
```

Download your file:

```bash
shelby download files/test.txt ./test-downloaded.txt
```

---

## Troubleshooting

### Insufficient Shelby Tokens

* Make sure you have **ShelbyUSD**, not just APT
* Run:

  ```bash
  shelby faucet --no-open
  ```
* Fund your account in the browser
* Recheck balance:

  ```bash
  shelby account balance
  ```

### Command Not Found

* Ensure npm’s global bin directory is in your PATH:

  ```bash
  export PATH="$HOME/.npm-global/bin:$PATH"
  ```
* Add it to `~/.bashrc` to make it permanent

### File Path Issues in WSL

* WSL paths look like:

  ```
  /home/username/file.txt
  ```
* Windows files from WSL:

  ```
  /mnt/c/Users/YourName/Desktop/file.txt
  ```

---

## Quick Command Reference

```bash
shelby context list
shelby account list
shelby account balance
shelby upload <local-path> <blob-name> -e <expiration> --assume-yes
shelby account blobs
shelby download <blob-name> <local-path>
shelby faucet --no-open
```

---

## About

This README provides a simple walkthrough for installing the Shelby CLI on WSL and uploading files to the Shelby network.

If you have questions, feel free to reach out.

**LEGACY**
