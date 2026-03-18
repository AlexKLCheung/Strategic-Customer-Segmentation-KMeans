# Strategic Customer Segmentation: Behavioral Profiling for Telco Retention
**Author:** Alex Cheung  
**Tech Stack:** Python, Scikit-Learn (K-Means), Pandas, Seaborn, Matplotlib

## 📌 Project Overview
In the telecommunications industry, churn prediction is common, but understanding the **behavioral archetypes** of customers is what allows for truly personalized retention. 

This project uses **Unsupervised Machine Learning (K-Means Clustering)** to segment 7,043 customers into three distinct "Personas." By identifying these groups, I uncovered a high-value segment with a churn rate nearly **4x higher** than the company average, providing a clear roadmap for targeted marketing interventions.

## 📊 Key Insights
* **The "At-Risk High-Rollers":** Identified a segment with short tenure (~13 months) but high monthly spend (~$75). This group has a staggering **47.2% churn rate**.
* **The "Flagship Loyalists":** A high-value, long-tenure group (avg. 58 months) that provides the company's most stable revenue stream.
* **The "Budget Mainstays":** Stable, low-cost users who are prime candidates for "lite" value-added service upsells.

## 🛠 Technical Workflow

### 1. Feature Engineering & Scaling
Since K-Means is a distance-based algorithm, I utilized the "Value Triad" (`tenure`, `MonthlyCharges`, `TotalCharges`). 
* **Imputation:** Handled missing values in `TotalCharges` (typically new customers with tenure=0) using median imputation to maintain data integrity.
* **Standardization:** Applied `StandardScaler` to ensure features with larger scales (TotalCharges) did not bias the cluster formation.

### 2. Model Optimization (The Elbow Method)
I utilized the **Elbow Method** to determine the optimal $K$. While $K=4$ showed a further decrease in SSE, I selected **$K=3$** to balance model performance with **business interpretability**, ensuring the resulting segments were distinct and actionable.



### 3. Cluster Validation
To validate the clusters, I cross-referenced the unsupervised labels with actual churn data. This revealed a clear correlation between the behavioral segments and the likelihood of cancellation.



## 🚀 Strategic Recommendations
* **Priority 1:** Launch a "First-Year Loyalty" campaign specifically for **Cluster 2** to convert them from month-to-month to annual contracts.
* **Priority 2:** Introduce premium concierge support for **Cluster 1** to protect the highest Lifetime Value (LTV) customers.
* **Priority 3:** Test "Entry-level" digital add-ons for **Cluster 0** to increase ARPU (Average Revenue Per User) without increasing price-sensitivity.

## 📂 Project Structure
* `Customer_Segmentation.ipynb`: The primary analysis and modeling notebook.
* `clean_df.parquet`: The processed dataset used for clustering.
* `images/`: Visualizations of the Elbow Method and Cluster distributions.

## 🔧 How to Run
1. Clone the repository: `git clone https://github.com/your-username/Telco-Customer-Segmentation-Strategy.git`
2. Install dependencies: `pip install pandas scikit-learn seaborn matplotlib`
3. Run the Jupyter Notebook: `jupyter notebook notebooks/Customer_Segmentation.ipynb`
