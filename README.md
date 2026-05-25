# BBQ Weather Prediction using Deep Learning 🌦️🔥

A Deep Learning project built using **TensorFlow/Keras** to predict outcomes from the BBQ Weather dataset.
This project focuses heavily on **reducing overfitting** using:

* Dropout Regularization
* L2 Regularization
* Validation Monitoring
* Proper Network Architecture

The final model achieved:

✅ **Accuracy: 96.19%**
✅ **F1 Score: 0.95**
✅ Stable validation performance with minimal overfitting

---

# 📌 Project Objective

The goal of this project is to build a robust Neural Network classifier while preventing overfitting and improving generalization on unseen data.

---

# 📂 Dataset Information

Dataset Shape:

```python
(2923, 12)
```

Where:

* **2923** → Number of samples/rows
* **12** → Number of input features

---

# 🧠 Model Architecture

The Neural Network was implemented using Keras Sequential API.

```python
model = Sequential()

model.add(Dense(128,
                activation='relu',
                input_dim=12,
                kernel_regularizer=regularizers.l2(0.001)))

model.add(Dropout(0.5))

model.add(Dense(64,
                activation='relu',
                kernel_regularizer=regularizers.l2(0.001)))

model.add(Dropout(0.2))

model.add(Dense(32,
                activation='relu',
                kernel_regularizer=regularizers.l2(0.001)))

model.add(Dropout(0.2))

model.add(Dense(1, activation='sigmoid'))
```

---

# ⚠️ Problem Faced: Overfitting

Initially, the model started learning the training data too well.

Symptoms observed:

* Validation loss fluctuations
* Unstable validation curve
* Gap between training and validation performance

This indicated the beginning of overfitting.

---

# ✅ Techniques Used to Reduce Overfitting

## 1️⃣ Dropout Regularization

### What is Dropout?

Dropout randomly disables neurons during training.

Example:

```python
Dropout(0.5)
```

means:

* 50% neurons are randomly ignored during each training step.

---

## Why Dropout Helps

Without dropout:

* Neurons become highly dependent on each other
* Model memorizes training data

With dropout:

* Model learns more generalized patterns
* Reduces memorization
* Improves robustness

---

## Dropout Layers Used

| Layer            | Dropout Rate |
| ---------------- | ------------ |
| After Dense(128) | 0.5          |
| After Dense(64)  | 0.2          |
| After Dense(32)  | 0.2          |

---

# 2️⃣ L2 Regularization

## What is L2 Regularization?

L2 regularization penalizes very large weights.

Used as:

```python
kernel_regularizer=regularizers.l2(0.001)
```

---

## Mathematical Idea

L2 adds penalty to the loss function:

[
Loss = OriginalLoss + \lambda \sum w^2
]

Where:

* ( \lambda ) = regularization strength
* ( w ) = model weights

---

## Why L2 Helps

Without L2:

* Weights may become extremely large
* Model becomes too complex
* Higher risk of overfitting

With L2:

* Keeps weights smaller
* Encourages simpler model
* Better generalization

---

# 3️⃣ Validation Split

Used:

```python
validation_split=0.2
```

Meaning:

* 80% data used for training
* 20% data used for validation

This helped monitor model performance on unseen data during training.

---

# 4️⃣ Batch Size Tuning

Initially, smaller batch size caused:

* Noisy gradients
* Unstable validation loss

After increasing batch size:

✅ Smoother training
✅ Stable convergence
✅ Better validation curves

---

# 📈 Training Analysis

## Final Observations

### Training Loss

* Consistently decreased

### Validation Loss

* Also decreased smoothly
* Stayed close to training loss

This indicates:

✅ Good generalization
✅ No severe overfitting
✅ Stable optimization

---

# 📊 Final Performance Metrics

## Classification Report

| Class | Precision | Recall | F1-Score |
| ----- | --------- | ------ | -------- |
| 0     | 0.98      | 0.98   | 0.98     |
| 1     | 0.92      | 0.92   | 0.92     |

---

## Overall Metrics

| Metric          | Score  |
| --------------- | ------ |
| Accuracy        | 96.19% |
| Macro Avg F1    | 0.95   |
| Weighted Avg F1 | 0.96   |

---

# 🔍 Key Learning Outcomes

Through this project, I learned:

* How Neural Networks overfit
* Importance of regularization
* Practical usage of Dropout
* Role of L2 Regularization
* Effect of batch size on training stability
* Validation monitoring techniques
* Model evaluation using Precision, Recall, and F1-score

---

# 🛠️ Technologies Used

* Python
* TensorFlow
* Keras
* NumPy
* Pandas
* Matplotlib
* Scikit-learn

---

# 🚀 Future Improvements

Possible future enhancements:

* EarlyStopping
* Learning Rate Scheduling
* Cross Validation
* Hyperparameter Tuning
* SMOTE for imbalance handling
* ROC-AUC analysis

---

# 📌 Conclusion

This project successfully demonstrates how overfitting in Deep Learning models can be controlled using:

✅ Dropout Regularization
✅ L2 Regularization
✅ Proper Validation Strategy
✅ Batch Size Optimization

The final model achieved strong performance while maintaining good generalization capability.

---

# 👨‍💻 Author

Gaurav Ghosh
CSE Undergraduate — NIT Silchar
