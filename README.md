# Flask Tutorial: Hello World

Welcome to this Flask tutorial! In this guide, you'll learn how to set up a simple Flask web app inside a Fedora 38 Virtual Box VM hosted on Windows 11. After setting up, you'll be able to access the web app from your host machine.

## Prerequisites

- Fedora 38 installed inside a VirtualBox VM.
- VirtualBox configured with two network adapters:
  1. NAT
  2. Bridged Adapter

## Setup Project

Python projects typically utilize virtual environments to prevent package conflicts. It's a best practice to have a separate virtual environment for each project.

### Create Virtual Environment

1. **Open a Terminal** inside your Fedora VM.

2. **Configure Firewall**: To allow external access to your Flask app, open port 5000 (or any other port you prefer) on your VM's firewall:

```bash
sudo firewall-cmd --add-port=5000/tcp --permanent
sudo firewall-cmd --reload
```

3. **Install Required Packages**:

```bash
sudo dnf update -y
sudo dnf install -y python3 python3-pip python3-venv
pip3 install flask
```

4. **Create a Project Directory**:

```bash
mkdir PythonFlaskHelloWorld
cd PythonFlaskHelloWorld
```

5. **Set Up a Virtual Environment**:

```bash
python3 -m venv venv
```

6. **Activate the Virtual Environment**:

```bash
source venv/bin/activate
```

7. **Install Flask Inside the Virtual Environment**:

```bash
pip install flask
```

8. **Create Your Flask App**: Create a file named `app.py`. Refer to the `app.py` file in this repository to view the code.

9. **Run Your Flask App**:

```bash
python3 app.py
```

10. **Identify Your VM's IP Addresses**:

```bash
ip a
```

11. **Identify the IP Associated with the "Bridged Adapter"**: Look for an IP address associated with an interface like enp0s8 or similar. This will typically be the IP address under the "Bridged Adapter" and not the one associated with lo or enp0s3 (which is for NAT)..

12. **Access the Flask App from Your Host**: On your host machine (Windows 11), open a web browser and navigate to the IP address of the VM followed by the port number. For example: `http://192.168.1.15:5000/`.

# Reference

Pythonbasics (2023) Flask Tutorial: Hello World. Retrieved from: https://pythonbasics.org/flask-tutorial-hello-world/ (Accessed: 2023-10-03).

# Git repository config

To automatically create a .gitignore file for a Python project, you can use the git command to generate a .gitignore file:

1. Initialize a new git repository (if you haven't already)

```bash
git init
```

2. Use the following command to create a .gitignore

```bash
git config --global alias.ignore '!gi() { curl -sL https://www.gitignore.io/api/$@ ;}; gi'
```

3. Now, you can generate the .gitignore file with:

```bash
git ignore python > .gitignore
```
