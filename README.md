### 🚀 Machine Learning Pipeline with DVC, AWS, and GitHub Actions

This project demonstrates the end-to-end process of building a machine learning pipeline using **DVC** for data versioning, **AWS S3** for remote storage, and **GitHub Actions** for CI/CD automation. The pipeline includes data ingestion, validation, transformation, model training, evaluation, and deployment.

---

### 🏆 **Project Highlights**
✅ Automated Pipeline with **DVC**  
✅ Experiment Tracking with **DVC Live**  
✅ Remote Storage Integration with **AWS S3**  
✅ CI/CD with **GitHub Actions**  
✅ Scalable and Reproducible Model Training  

---

### 📁 **Project Structure**
```
├── src/                   # Source code (components)
├── data/                  # Raw and processed data (ignored)
├── models/                # Trained models (ignored)
├── reports/               # Reports and metrics (ignored)
├── params.yaml            # Parameter configuration
├── dvc.yaml               # DVC pipeline stages
├── .gitignore             # Ignored files
├── README.md              # Project documentation
```

---

## 🛠️ **Setup and Configuration**

### 1. ✅ **Building the Pipeline**
1. Create a GitHub repository and clone it locally.  
2. Create a `src/` folder with individual components (data ingestion, transformation, model training, etc.).  
3. Add `data/`, `models/`, and `reports/` to `.gitignore`.  
4. Use the following commands:  
```bash
git add .
git commit -m "Initial commit"
git push origin main
```

---

### 2. 🚀 **Setting Up the DVC Pipeline (Without Parameters)**
1. Create a `dvc.yaml` file and define pipeline stages.  
2. Initialize DVC and test the pipeline:  
```bash
dvc init
dvc repro
dvc dag
```
3. Commit and push changes:  
```bash
git add .
git commit -m "Add DVC pipeline"
git push origin main
```

---

### 3. 🔧 **Setting Up DVC Pipeline (With Parameters)**
1. Create a `params.yaml` file.  
2. Configure parameters (see example below).  
3. Test the pipeline with parameters:  
```bash
dvc repro
```
4. Commit and push changes:  
```bash
git add .
git commit -m "Add pipeline with params"
git push origin main
```

---

### 4. 🧪 **Experimenting with DVC**
1. Install DVC Live:  
```bash
pip install dvclive
```
2. Add the following code block to log metrics and parameters:  
```python
from dvclive import Live
with Live(save_dvc_exp=True) as live:
    live.log_metric('accuracy', accuracy_score(y_test, y_test))
    live.log_metric('precision', precision_score(y_test, y_test))
    live.log_metric('recall', recall_score(y_test, y_test))
    live.log_params(params)
```
3. Run experiments and track results:  
```bash
dvc exp run
dvc exp show
```
4. Apply or delete experiments (if needed):  
```bash
dvc exp apply {exp-name}
dvc exp remove {exp-name}
```

---

### 5. ☁️ **Adding Remote S3 Storage to DVC**
1. Set up AWS credentials:  
```bash
aws configure
```
2. Install dependencies and add remote storage:  
```bash
pip install dvc[s3]
pip install awscli
dvc remote add -d dvcstore s3://<bucket-name>
```
3. Push experiment results to S3:  
```bash
dvc commit
dvc push
```
4. Commit and push changes to GitHub:  
```bash
git add .
git commit -m "Add remote storage to DVC"
git push origin main
```

---

## ⚙️ **Parameter Setup Example (`params.yaml`)**
Example structure for defining pipeline parameters:
```yaml
data_ingestion:
  test_size: 0.2

feature_engineering:
  max_features: 500

model_building:
  n_estimators: 100
  max_depth: 10
```

**Loading Parameters in Code:**
```python
import yaml

def load_params(params_path: str) -> dict:
    with open(params_path, 'r') as file:
        params = yaml.safe_load(file)
    return params

params = load_params('params.yaml')
test_size = params['data_ingestion']['test_size']
max_features = params['feature_engineering']['max_features']
```

---

## 📊 **Visualize Pipeline**
Generate a DAG to visualize the pipeline structure:
```bash
dvc dag
```

---

## 🚀 **Why This Project Stands Out**
✅ Fully automated and reproducible ML pipeline  
✅ Version-controlled experiments with easy rollback  
✅ Cloud storage integration for scalable data management  
✅ Experiment tracking and visualization with DVC Live  
✅ CI/CD for continuous integration and deployment  

---

## 🏆 **Future Improvements**
- Add more complex feature engineering steps  
- Experiment with different models and hyperparameters  
- Deploy using AWS Lambda or SageMaker  

---

## 🤝 **Contributing**
Feel free to open issues or submit pull requests. Suggestions and improvements are always welcome!  

---

## 📄 **License**
This project is licensed under the [MIT License](LICENSE).  

---

💡 *If you like this project, give it a ⭐ on GitHub!*  
