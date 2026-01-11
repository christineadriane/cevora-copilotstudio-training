# LAB 0 — Check prerequisites & Clone/Download the Workshop Repository

Before starting with the technical labs, we’ll make sure that all workshop prerequisites are met and that you have your own working copy of the lab materials. This lab consists of two parts:

✅ Verifying that all required software, services, and environments are set up

🧬 Forking and cloning the GitHub repository with lab instructions and resources

## ✅ Part 1: Check prerequisites
Review the checklist below.

- 💻 Laptop  
✅ Windows 10/11 or macOS

- 🛡️ Power Platform  
✅ Microsoft 365 tenant [Sign up here](https://signup.microsoft.com/get-started/signup?products=91dcd8b1-3b1b-444d-9cdb-0bc0da3eb40d&mproducts=CFQ7TTC0LH18:0002&fmproducts=CFQ7TTC0LH18:0002&culture=en-us&country=us&ali=1)  
✅ Power Platform Developer Plan [Get started](https://www.microsoft.com/en-us/power-platform/products/power-apps)  
✅ Dataverse-enabled environment (guide) [Guide](https://learn.microsoft.com/en-us/power-platform/admin/create-environment#create-an-environment-with-a-database)  
✅ System Administrator role assigned [Guide](https://learn.microsoft.com/en-us/power-platform/admin/assign-security-roles)  
✅ Access to Copilot Studio [Trial Guide](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-licensing-subscriptions)  

## 🧬 Part 2: Fork and Clone the Workshop Repository  
*Now let’s fork the repository and clone it locally so you can work with lab files in your own environment. I will remove this repository after the workshop so if you want to access the resources after, make sure you fork and clone it or just download as a zip.*

- Create a folder on your laptop where you'll clone the repository. For example, you can create a folder named copilot-studio-workshop on your C: drive.

1. Open the GitHub repo in your browser: [https://github.com/christineadriane/cevora-copilotstudio-training/](https://github.com/christineadriane/cevora-copilotstudio-training/)
2. Click the Fork button in the top right corner and create a copy in your own GitHub account.
3. In your forked repository, click the Code button and copy the Clone URL (HTTPS). Clone URL
4. Open PowerShell or any terminal of your choice.
5. Navigate to a working directory where you want to clone the labs using cd command. For example:
```bash
cd c:\copilot-studio-workshop
```
7. Clone your forked repo (replace with the URL you copied before):
```bash
git clone https://github.com/<YOUR_CLONE_URL>
```
9. Once cloned, open the project in Visual Studio Code:
```bash
code .
```
---

✅ You’re now ready to start the workshop!
