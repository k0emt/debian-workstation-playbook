# How to test in a WSL2 instance

Create a new WSL2 instance based on debian:

1. **Install WSL2**:
   Ensure you have WSL2 installed on your Windows machine. You can follow the official Microsoft documentation [here](https://docs.microsoft.com/en-us/windows/wsl/install).

2. **Install Ubuntu for WSL2**:
   Ubuntu is the default distribution that is used with WSL2.

3. **Set up the WSL2 instance**:
   Once installed, you can set up your WSL2 instance by running the following command in PowerShell:

   ```powershell
   wsl --set-version <Distro> 2
   ```

4. **Launch Linux**:
   Open Ubuntu from your Start menu or by running the following command in PowerShell:

   ```powershell
   wsl -d <Distro>
   ```

5. **Update and upgrade packages**:
   Once inside the Ubuntu terminal, update and upgrade your packages:

   ```powershell
   wsl --set-version <Distro> 2
   sudo apt update
   sudo apt upgrade -y
   ```

6. **Clone this repo**:
   Change into the cloned directory.

7. **Run your Ansible playbook**:
   You can now run your Ansible playbook as described in the [README.md](README.md).
