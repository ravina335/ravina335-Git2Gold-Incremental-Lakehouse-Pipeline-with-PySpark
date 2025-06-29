# 🚀 Git2Gold: Incremental Lakehouse Pipeline with PySpark

This project showcases an **end-to-end Data Engineering pipeline** that ingests raw data from a **GitHub-hosted source**, processes it incrementally through **Bronze → Silver → Gold** layers on **Azure Data Lake Storage (ADLS)** using **PySpark**, and builds a **star schema** in the Gold layer for downstream analytics.

---

## 📁 Project Structure
├── part_1(github_to_sql_db)
│ └── Ingest data from GitHub and load to Azure SQL DB
│
├── part_2(incremental_data_pipeline_sqldb_to_bronze)
│ └── Read from SQL DB, apply incremental filter, write to ADLS (Bronze)
│
├── part_3(all_databricks_notebooks)
│ └── PySpark transformation scripts for Silver & Gold layer
│
├── part_4(final_workflow)
│ └── Workflow integration + surrogate key handling + Delta Lake save

## ⚙️ Technologies & Tools

- **Azure Data Lake Storage (Gen2)**
- **Azure SQL Database**
- **Databricks (PySpark notebooks)**
- **Delta Lake**
- **GitHub REST API (source)**
- **Star Schema Modeling (Dim/Fact)**

---

## 🔁 Incremental Load Logic

- Controlled by `incremental_flag` using `dbutils.widgets`.
- If `incremental_flag == 0`, full load is triggered.
- If `incremental_flag == 1`, only data with a newer surrogate key is loaded.
- Surrogate key is managed as `Dim_model_key` in the Gold layer using SQL logic + PySpark.

---

## 🧠 Key Features

- 🔗 **Automated Ingestion** from GitHub to Azure via REST API
- 🪄 **Incremental Pipeline** with config-driven loads
- 🧼 **PySpark Transformations** (Bronze → Silver)
- 🏆 **Dimensional Modeling** with star schema in the Gold layer
- 💾 **Delta Format Tables** optimized for querying

---

## 📌 How to Use

1. Set up your Azure resources: ADLS, SQL DB, Databricks.
2. Connect your GitHub source in `part_1`.
3. Run scripts in order from part_1 to part_4.
4. Modify `dbutils.widgets.get('incremental_flag')` to control the load behavior.
5. Final outputs are saved as Delta tables in the Gold layer.

---

## 📂 Sample Data Files

The following zipped project files were used to support pipeline execution:
- `project_incre.zip`
- `incre_data_pipeline_support_live.zip`
- `source_prep_support_live.zip`

*(now organized under relevant folders for easier understanding)*

---

## 🤝 Contributing

Pull requests and feedback are welcome! Feel free to fork the repo and submit changes.

---

## 📜 License

This project is open-source under the [MIT License](LICENSE).

---

## 👩‍💻 Author

**Ravina Babal**  
_Data Engineer | Azure + PySpark Enthusiast_  
🔗 [LinkedIn](https://www.linkedin.com/in/ravina-babal-7195821b1)
