# TriClass-Lab-Logistic-Regression-Multi-Class-SVM-Benchmark
> **TriClass Lab** is a compact, end‑to‑end benchmark that pits three classic learners against one another on the MNIST digits:
>
> 1. **One‑vs‑All Logistic Regression** (baseline)
> 2. **Soft‑max Multi‑Class Logistic Regression** (extra‑credit variant)
> 3. **Support‑Vector Machines** – linear and RBF, with γ/C sweeps
>
> The repo walks from raw `mnist_all.mat` through feature selection, training, hyper‑parameter tuning, and final test evaluation—producing side‑by‑side accuracy tables and an “Accuracy vs C” plot in a single script.
> All code is pure NumPy / SciPy / scikit‑learn (no black‑box ML libraries), fully reproducible in under 10 minutes on a free Colab CPU.
