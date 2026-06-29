# Run Pipelines in Azure Machine Learning - Exercise Guide

This folder (`C:\Users\Gaming pc\Desktop\AI300\pipeline_building`) contains all the lab files for the **Run pipelines in Azure Machine Learning** exercise.

---

## 🚀 Phase 1: Create the GitHub Repository (`pipeline-building`)
1. Click this direct link to create your new GitHub repository: 👉 **[Create New Repository on GitHub](https://github.com/new)**
2. Enter the Repository name: **`pipeline-building`**
3. Make sure it is **Public** or **Private**, leave "Add a README file" **unchecked**, and click **Create repository**.
4. Once created, push your local files to GitHub by running this command in PowerShell or VS Code:
   ```powershell
   cd "C:\Users\Gaming pc\Desktop\AI300\pipeline_building"
   git push -u origin main --force
   ```

---

## ☁️ Phase 2: Provision Azure Workspace & Compute (SKIP IF REUSING)
> [!TIP]
> Since you already have the active resource group **`rg-ai300-lc9b35460640d4583af`** and workspace **`mlw-ai300-lc9b35460640d4583af`** created from your earlier lab, **you can completely skip this step and save 10 minutes!** Go directly to Phase 3.

1. *(Only if starting from scratch)* Open the [Azure Portal](https://portal.azure.com/) Cloud Shell and run `./setup.sh`.

---

## 🔬 Phase 3: Run the Pipeline Job in Azure ML Studio
1. Navigate to your new workspace (`mlw-ai300-...`) in the Azure Portal and select **Launch studio**.
2. In Azure ML Studio, go to the **Compute** page on the left sidebar. Verify your Compute Instance is **Running**.
3. Under the **Compute instances** tab, click **Terminal** next to your compute instance.
4. Run these commands in the terminal to reinstall the Python SDK and clone the materials into your workspace:
   ```bash
   pip uninstall azure-ai-ml -y
   pip install azure-ai-ml
   git clone https://github.com/MicrosoftLearning/mslearn-mlops.git mslearn-mlops
   ```
5. In the left sidebar, click **Notebooks** (or Files) and refresh (`↻`).
6. Open the folder `mslearn-mlops/experimentation` and click on **`Run a pipeline job.ipynb`**.
7. Ensure the kernel at the top right is set to **Python 3.10 - AzureML**.
8. Click **Run all cells** (or run cell-by-cell) to orchestrate and execute the machine learning pipeline!

---

## 🧹 Phase 4: Clean Up Azure Resources
Once your pipeline finishes running successfully, avoid Azure charges by deleting the resource group:
In Cloud Shell:
```bash
for rg in $(az group list --query "[?starts_with(name, 'rg-ai300')].name" -o tsv); do
    az group delete --name $rg --yes --no-wait
done
```
