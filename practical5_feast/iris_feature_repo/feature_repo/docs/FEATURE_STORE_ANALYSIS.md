# Feature Store Analysis

## Observed Benefits

### 1. Elimination of Training-Serving Skew

The same `iris_engineered_features` definitions are served both online in Step 6 and offline in Steps 7-8. This helps maintain consistency between training and serving.

### 2. Reusability

Step 8 reused the registered features for a different model without re-implementing the feature engineering logic.

### 3. Centralized Governance

The `features.py` file acts as the single source of truth for the registered features used by consuming models.