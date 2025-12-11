Titanic Survival Prediction — Full ML Workflow (With & Without Pipeline)

This project demonstrates two complete machine-learning workflows on the Titanic dataset:

Without Pipeline – every preprocessing step is done manually

With Pipeline – preprocessing and model training are automated inside a single pipeline

You also get two separate prediction scripts to compare real-world usage in both cases.

🚀 1. Project Structure
├── titanic_using_pipeline.py
├── titanic_without_using_pipeline.py
├── predict_using_pipeline.py
├── predict_without_pipeline.py
├── models/
│   ├── ohe_sex.pkl
│   ├── ohe_embarked.pkl
│   └── clf.pkl
└── pipe.pkl

🧠 2. Approach 1 — Without Pipeline

This version handles everything manually:

Steps

Missing value imputation (Age, Embarked)

One-hot encoding (Sex, Embarked)

Concatenation of all transformed columns using NumPy

Training a DecisionTreeClassifier

Measuring accuracy

Saving models:

ohe_sex.pkl

ohe_embarked.pkl

clf.pkl

Pros

Full control

Good for understanding internal workflow

Cons

Messy

High risk of mistakes

Hard to maintain or deploy

⚙️ 3. Approach 2 — With Pipeline

Here everything is streamlined using Pipeline and ColumnTransformer.

Pipeline includes

Imputation

One-Hot Encoding

Feature Scaling

Feature Selection (SelectKBest)

Decision Tree model

Extras

Displaying the pipeline diagram

Cross-validation

GridSearchCV hyperparameter tuning

Exporting the final trained pipeline → pipe.pkl

Pros

Clean

Reproducible

Deployment-ready

All preprocessing is stored inside the model

Cons

More abstract for beginners

🔮 4. Predicting With Pipeline

File: predict_using_pipeline.py

Flow

Load pipe.pkl

Prepare user input:

[Pclass, Sex, Age, SibSp, Parch, Fare, Embarked]


Call pipe.predict()

Output: 0 = Not Survived, 1 = Survived

Why it’s simple

The pipeline does all transformations internally — zero manual steps.

🔧 5. Predicting Without Pipeline

File: predict_without_pipeline.py

Flow

Load encoders + classifier

One-hot encode Sex

One-hot encode Embarked

Keep numerical columns separate

Concatenate everything manually

Predict using clf.predict()

Why it’s messy

You must maintain the exact feature order and manually ensure transformations match the training stage.

📊 6. Key Takeaways

Pipelines drastically reduce code complexity and eliminate preprocessing mistakes.

Manual processing gives transparency but becomes painful as complexity increases.

Prediction with pipeline is clean, while prediction without pipeline is error-prone.

📁 7. How to Run
Train Models
python titanic_using_pipeline.py
python titanic_without_using_pipeline.py

Make Predictions
python predict_using_pipeline.py
python predict_without_pipeline.py
