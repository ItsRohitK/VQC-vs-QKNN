# **Quantum Classifier Comparison: Active (VQC) vs. Lazy (QKNN) Learner**

This is a single-file, interactive web application designed to demonstrate the fundamental trade-offs between two different types of machine learning algorithms, using Quantum Classifiers as an example.

The project simulates and compares:

1. **Model 1: Variational Quantum Classifier (VQC)** \- An "Active Learner"  
2. **Model 2: Quantum K-Nearest Neighbors (QKNN)** \- A "Lazy Learner"

The entire application is self-contained in index.html.

## **📍 Core Concept: The "Active" vs. "Lazy" Trade-Off**

This project's main goal is to illustrate the crucial performance difference between "active" and "lazy" learning algorithms.

* **Active Learner (VQC):** This type of model goes through an intensive, up-front "training" phase to learn a compact mathematical function (a model) that represents the data.  
  * **TRAIN:** Slow and computationally expensive.  
  * **PREDICT:** Very fast, because it just needs to pass new data through its learned function.  
* **Lazy Learner (QKNN):** This type of model does *no* training. It simply stores the entire training dataset.  
  * **TRAIN:** Instant (0 ms).  
  * **PREDICT:** Very slow, because to classify a new point, it must compare that point to *every single point* in its stored training data.

This trade-off is a central concept in both classical and quantum machine learning.

## **🧮 The Simulated Algorithms**

Since running actual quantum circuits in a browser is not feasible, this project uses highly effective classical analogues to simulate the *behavior* and *performance trade-offs* of their quantum counterparts.

### **1\. Model 1: VQC (Simulated by an MLP)**

* **What it is:** A Variational Quantum Classifier (VQC), or Quantum Neural Network (QNN), is an "active" learner. It uses a hybrid quantum-classical loop to iteratively adjust the parameters (rotations) in its quantum circuit to minimize a cost function.  
* **How it's Simulated:** We use a **2-Layer Neural Network (MLP)**. This is a perfect analogue because it's a non-linear model that learns weights and biases through an iterative training process (backpropagation). You can watch this happen in the **Live Training Cost** graph.  
* **Hyperparameters:**  
  * Epochs: The number of training iterations.  
  * Learning Rate: How quickly the model updates its weights.

### **2\. Model 2: QKNN (Simulated by KNN)**

* **What it is:** A Quantum K-Nearest Neighbors (QKNN) algorithm is a "lazy" learner. To classify a new data point, it uses a quantum subroutine (like a "Swap Test") to calculate the "quantum distance" or overlap between the new point and every point in the training set. It then takes a majority vote from the k closest points.  
* **How it's Simulated:** We use a classical **K-Nearest Neighbors (KNN)** algorithm. This perfectly demonstrates the trade-off: it has 0 training time, but its prediction time scales directly with the size of the training set and test set.  
* **Hyperparameters:**  
  * Neighbors (K): The number of neighbors to use for the majority vote.

## **💻 How to Use**

1. **Save the File:** Download the index.html file provided.  
2. **Open in Browser:** Double-click the file to open it in any modern web browser (Chrome, Firefox, Safari, etc.).

### **Interacting with the App**

1. **Dataset Controls:**  
   * **Dataset Type:** Choose the shape of your data. Moons and Circles are non-linear and harder to classify, while Blobs is simple.  
   * **Total Samples:** Controls the *size* of the dataset. This is the most important slider\!  
   * **Dataset Noise:** Adds randomness to the data points.  
   * **Generate New Data:** Click this to create a new train/test split and update the main plot.  
2. **Run Each Model:**  
   * Adjust any hyperparameters (like Epochs for VQC or K for QKNN).  
   * Click the **"Train & Run..."** button for each model.  
   * Observe the results in the metrics boxes.

## **📊 What to Observe (The "Aha\!" Moment)**

The best way to see the core concept is to **test the scalability**:

1. Set **Total Samples** to 100\.  
2. Run both models. Note the Train Time and Predict Time for each. They should both be very fast.  
3. Now, set **Total Samples** to its maximum (500).  
4. Run both models again.  
5. You will see:  
   * **VQC:** Train Time will increase, but Predict Time will stay almost the same (it's still very fast).  
   * **QKNN:** Train Time will still be 0 ms, but the **Predict Time will explode\!** It will become much, much slower.

This is the **"active vs. lazy" trade-off** in action. You are trading *training time* for *prediction time*.