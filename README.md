Likert Scale Fuzzification using Gaussian Fuzzy Numbers

This project implements an algorithm that converts 5-point Likert scale survey responses into continuous fuzzy numerical values using principles from Triangular Fuzzy Numbers (TFNs) and Center of Gravity (CoG) defuzzification.

The goal is to transform ordinal survey data into a continuous representation that better captures uncertainty and gradation in human responses, making the data more suitable for quantitative modeling and advanced statistical analysis.

🧠 Motivation

Likert-scale responses are ordinal and discrete. Treating them as interval data in statistical models introduces measurement distortion. Fuzzy logic provides a principled way to represent:

Vagueness in human judgment

Overlapping semantic meanings between response categories

Gradual transitions rather than sharp category boundaries

This algorithm converts each Likert value into a fuzzy number and then into a continuous score using defuzzification.

⚙️ Methodology
Step 1 — Define Triangular Fuzzy Numbers (TFNs)

Each Likert category is represented as a TFN:

Likert Value	Lower Bound	Midpoint	Upper Bound
1	0.00	0.00	0.25
2	0.00	0.25	0.50
3	0.25	0.50	0.75
4	0.50	0.75	1.00
5	0.75	1.00	1.00
Step 2 — Defuzzification using Center of Gravity

For each TFN, the crisp value is computed as:

𝐶𝑜𝐺 = (𝑙 + 4𝑚 + 𝑢) / 6

where:

𝑙 = lower bound

𝑚 = midpoint

𝑢 = upper bound

This produces a continuous fuzzy score in 
[0 , 1]


Step 3 — Column-wise Transformation

Each Likert item in the dataset is mapped to its CoG value:

for col in raw_data_CoG.columns:
    raw_data_CoG[col] = raw_data_CoG[col].map(CoG)

📂 Input

A CSV file named:

Fuzzification.csv


Each column should contain integer values 1–5 representing Likert responses.

📤 Output

A transformed dataframe where each Likert response is replaced by its continuous fuzzy equivalent.

This output can be used in:

Regression models

SEM / PLS-SEM

Machine learning

Clustering

Network analysis

🛠 Dependencies

Python 3.x

numpy

pandas

matplotlib

seaborn

📊 Research Use

This method is useful in:

Social sciences

Behavioral research

Decision sciences

Human-centered AI

Policy perception studies

✍️ Author

Sahand E.P. Faez
Political behavior | Quantitative methods | Fuzzy logic in social measurement
