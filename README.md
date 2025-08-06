# **Travel Insurance Risk Analysis Report**

---

### **Executive Summary**

This report presents the findings from the analysis of flight-related risks for the optimization of travel insurance pricing. The primary goal is to classify flights as high-risk or low-risk based on various operational factors such as airline, route, operational period, and seasonal patterns. By doing so, we can tailor insurance premiums accordingly, offering lower rates for low-risk flights and higher rates for high-risk flights. This report outlines the key factors driving risk, model performance, and recommendations for pricing strategies and business implementation.

---

### **1. Business Context & Objectives**

* **Insurance Claim Triggers**:

  * A claim is triggered if a flight is delayed by more than **180 minutes** or if it is **canceled**.
  * The payout for each qualifying claim is **\$800**.

* **Objective**:
  The aim is to implement **risk-based pricing** for travel insurance that adjusts premiums based on the likelihood of flight delays and cancellations, thus optimizing customer acquisition while effectively managing risk.

---

### **2. Data Preparation & Claim Simulation**

* **Data Overview**:
  The dataset contains **899,114 flight records**. After cleaning the data (removing 1,714 records with missing airline data), the key analysis was based on the **claim logic**:

  * Claims are triggered by delays greater than 180 minutes or cancellations.
  * The **average expected payout** per flight was **\$22.87**.
  * The **overall claim rate** is **2.86%**, leading to a total **potential exposure** of **\$20,522,400**.

---

### **3. Risk Segmentation for Pricing Model**

#### **Airline Risk Analysis**:

* **Top 5 Highest Risk Airlines**:
  Airlines with the highest claim rates:

  * **Airline O8**: Claim rate of **30.32%**.
  * **Airline E8**: Claim rate of **25.89%**.
  * **Airline OX**: Claim rate of **24.74%**.

* **Top 5 Lowest Risk Airlines**:
  Airlines with the lowest claim rates:

  * **Airline GK**: Claim rate of **0.12%**.
  * **Airline VA**: Claim rate of **0.04%**.
  * **Airline KC**: Claim rate of **0.00%**.

#### **Operational Period Risk**:

* Flights operating in the **morning** had the highest claim rate (**3.23%**), followed by the **evening** (3.05%) and **afternoon** (2.95%). **Night** flights had the lowest risk (**1.86%**).

#### **Day of Week Risk Patterns**:

* **Highest Claim Rate Days**:

  * **Tuesday**: Claim rate of **3.32%**.
  * **Wednesday**: Claim rate of \*\*3.19%.

* **Lowest Claim Rate Days**:

  * **Friday**: Claim rate of **2.40%**.
  * **Sunday**: Claim rate of **2.46%**.

---

### **4. Predictive Model for Risk Pricing**

A **Logistic Regression** model was trained to predict the likelihood of a flight triggering an insurance claim. Key metrics from the model:

* **Training Accuracy**: **97.1%**.
* **Testing Accuracy**: **97.1%**.
* **AUC Score**: **0.806** (Indicating strong discrimination between high-risk and low-risk flights).

#### **Business Impact Metrics**:

* **True Negatives (Low-Risk Correctly Identified)**: 261,468
* **False Positives (Overpriced Low-Risk)**: 56
* **False Negatives (Underpriced High-Risk)**: 7,648
* **True Positives (High-Risk Correctly Identified)**: 48

#### **Model Performance**:

* **Precision** (High-risk accuracy): **46.2%**.
* **Recall** (High-risk coverage): **0.6%**.

---

### **5. Risk Factor Analysis for Pricing Algorithm**

#### **Top 10 Risk-Increasing Factors**:

* **Airline\_BG**: Premium increase of **44.17x**.
* **Airline\_JW**: Premium increase of **35.46x**.
* **Arrival\_OKJ**: Premium increase of **25.12x**.

#### **Top 10 Risk-Decreasing Factors**:

* **Arrival\_HND**: Premium decrease of **0.04x**.
* **Airline\_AK**: Premium decrease of **0.06x**.
* **Arrival\_AKL**: Premium decrease of **0.06x**.

These factors highlight the importance of **airlines** and **arrival locations** in determining the likelihood of claims.

---

### **6. Visualizations**

The following visualizations were generated for a more intuitive understanding of the model’s performance:

1. **Confusion Matrix**: Shows the model's accuracy in classifying flights as low-risk and high-risk.

   * Saved as: **insurance\_risk\_confusion\_matrix.png**.
2. **ROC Curve**: Illustrates the model's ability to distinguish between high-risk and low-risk flights, showing an AUC of **0.806**.

   * Saved as: **insurance\_risk\_roc\_curve.png**.
3. **Feature Importance**: Displays the top 15 most important features influencing the model's predictions.

   * Saved as: **insurance\_pricing\_factors.png**.

---

### **7. Hypothesis Validation & Business Conclusions**

#### **H1 - Airline Risk Differentiation**:

* **Validated**: Several airlines have significantly different claim rates.
* **Actionable Insight**: Implement **airline-specific pricing tiers**.

#### **H2 - Operational Time Risk**:

* **Not Validated**: Operational time (morning, afternoon, evening) did not significantly influence claim rates.
* **Actionable Insight**: No time-based pricing adjustments needed.

#### **H3 - Route-Specific Risk**:

* **Validated**: Certain routes significantly impact risk.
* **Actionable Insight**: Implement **route-specific premiums**.

#### **H4 & H5 - Temporal Patterns**:

* **Not Validated**: Day of the week and seasonal patterns had minimal impact on risk.
* **Actionable Insight**: **Calendar-based pricing** adjustments are not necessary.

---

### **8. Pricing Model Implementation Strategy**

#### **Risk-Based Pricing Tiers**:

* **Tier 1 - Ultra-Low Risk**: Risk ≤ **0.4%** | Premium: **\$50**.
* **Tier 2 - Low Risk**: Risk ≤ **1.2%** | Premium: **\$65**.
* **Tier 3 - Medium Risk**: Risk ≤ **2.4%** | Premium: **\$80**.
* **Tier 4 - High Risk**: Risk ≤ **4.1%** | Premium: **\$95**.
* **Tier 5 - Ultra-High Risk**: Risk ≤ **55.4%** | Premium: **\$110**.

#### **Implementation Recommendations**:

1. **Model Deployment**:

   * Integrate the model into the **booking platform** for real-time pricing.
   * Set the **optimal threshold** at **0.030** for classifying high-risk flights.
   * Implement **A/B testing** for pricing validation.

2. **Pricing Strategy**:

   * Use the **5-tier risk-based pricing** model.
   * Apply **75% average premium adjustment** range.

3. **Business Controls**:

   * **Monthly model retraining** with updated data.
   * **Competitor pricing analysis** to stay competitive.
   * **Customer elasticity testing** for optimal premium pricing.

4. **Risk Management**:

   * **Expected claim rate**: **2.86%**.
   * **Loss ratio target**: **60-70%**.
   * Diversify the portfolio across **low-risk** and **high-risk** segments.

---

### **9. Conclusion**

The analysis provides actionable insights for optimizing travel insurance premiums using a **risk-based pricing model**. Key findings include:

* **Airline-specific pricing tiers** and **route-specific premiums** are critical for differentiating risk.
* **Time of day**, **seasonality**, and **day of the week** were not significant risk factors.
* The **5-tier pricing structure** based on predicted risk will help balance profitability and customer acquisition.

By implementing this model, the company can achieve a more efficient and effective risk management strategy, resulting in improved profitability and customer satisfaction.

---

### **10. Appendices**

* **Appendix A**: Confusion matrix and ROC curve visualizations.
* **Appendix B**: Full list of feature importance and pricing recommendations.
* **Appendix C**: Summary of model performance metrics.

---

This report outlines a clear, actionable strategy for integrating risk-based pricing into travel insurance operations, based on flight delay and cancellation data analysis.
