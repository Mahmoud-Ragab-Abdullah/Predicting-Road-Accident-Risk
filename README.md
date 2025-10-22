# Road Accident Risk Prediction System: Leveraging Non-Linear Feature Dynamics

Project Overview
This project delivers a robust predictive model for continuous road accident probability, a critical tool for preventative infrastructure planning. By rigorously applying advanced feature engineering and a Random Forest Regressor, we successfully navigated the highly non-linear nature of road safety data.

The final model achieved an Root Mean Squared Error (RMSE) of 0.0562, representing a 64.9% improvement in predictive accuracy over the simple baseline model RMSE=0.16. This significant reduction in error validates the methodology and provides a reliable framework for targeted risk mitigation.

II. Strategic Data Analysis & Feature Engineering
The challenge was confirming that predictive power resided in non-linear feature interactions, as standard linear methods (Lasso Regression) failed to assign meaningful coefficients.

Feature Importance Validation
Analysis relied on the Gini Importance from the Random Forest model to identify the true drivers of risk, revealing a powerful but concentrated feature set:

Rank   Feature       Importance Score      Domain Insight    
 1     curvature          0.36              Primary Risk Driver: Road geometry is the single most critical factor influencing accident likelihood.
 2     lighting_Ordinal   0.26              Confirms the dramatic and non-linear shift in risk between day and night conditions.
 3     speed_limit        0.25              The legal speed environment is highly correlated with inherent road risk.

Strategic Feature Transformation To maximize signal integrity and combat redundancy, two key transformations were implemented via a ColumnTransformer pipeline:
Ordinal Encoding: The categorical lighting feature was mapped to an ordinal scale (1, 2, 3) to capture the hierarchy of risk.Signal Consolidation: Due to observed multicollinearity and similar low importance. (weather_foggy) and (weather_rainy) were combined into a single binary feature, poor_visibility. This action reduced noise and concentrated the weather risk signal.

Performance Evaluation (RMSE):
The Root Mean Squared Error (RMSE) was chosen as the primary metric, fulfilling the project requirement to heavily penalize large prediction errors.Cross-Validation: Performance was validated using 5-fold Cross-Validation on the training data.Custom Scorer: A critical custom scoring function was implemented to ensure that predictions were inverse-transformed np.expm1 before calculating the RMSE. This guarantees the reported RMSE accurately reflects the error on the original, real-world probability scale.

Conclusion:
The $64.9 error reduction confirms that the combination of domain-driven feature selection (focusing on the top three drivers) and rigorous pipeline management delivers superior predictive accuracy, making this model an immediate asset for proactive road safety management.
