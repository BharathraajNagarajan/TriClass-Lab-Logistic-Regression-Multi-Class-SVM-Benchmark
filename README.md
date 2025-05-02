# TriClass-Lab-Logistic-Regression-Multi-Class-SVM-Benchmark
> **TriClass Lab** is a compact, end‑to‑end benchmark that pits three classic learners against one another on the MNIST digits:
>
> 1. **One‑vs‑All Logistic Regression** (baseline)
> 2. **Soft‑max Multi‑Class Logistic Regression** (extra variant)
> 3. **Support‑Vector Machines** – linear and RBF, with γ/C sweeps
>
> The repo walks from raw `mnist_all.mat` through feature selection, training, hyper‑parameter tuning, and final test evaluation—producing side‑by‑side accuracy tables and an “Accuracy vs C” plot in a single script.
> All code is pure NumPy / SciPy / scikit‑learn (no black‑box ML libraries), fully reproducible in under 10 minutes on a free Colab CPU.




### Key Insights from the Project

1. **Linear separability is good—but not perfect**
   A linear‑kernel SVM already scores \~94 % on MNIST, confirming that digits are *largely* separable in raw‑pixel space, yet non‑linear models still help.

2. **γ drives locality in RBF SVMs**
   Choosing γ = 1 makes the kernel radius tiny, so the model memorises the training set (100 % train, 17 % test) → textbook over‑fitting.

3. **Data‑adaptive γ (‘scale’) restores generalisation**
   scikit‑learn’s default γ≈0.003 (derived from feature variance) smooths the decision boundary and lifts test accuracy to \~98 %.

4. **Multi‑class logistic regression outperforms one‑vs‑all**
   Training a single weight matrix for all ten digits (multi‑class LR) improves test accuracy by ≈0.6 % over ten independent one‑vs‑all classifiers because classes share information.

5. **Training‑vs‑test gaps reveal model health**
   One‑vs‑all LR: gap ≈1.2 % • Multi‑class LR: gap ≈0.9 % • Tuned RBF SVM: gap ≈0.1 % —smaller gaps indicate better generalisation.

6. **C has diminishing returns once γ is right**
   For RBF with default γ, validation accuracy plateaus at C≈10; pushing C to 100 only bloats the number of support vectors.

7. **Multi‑class LR trains \~10× faster than full RBF SVM**
   It optimises just (D+1)×10 weights with conjugate‑gradient—no kernel matrix—finishing in minutes on CPU.

8. **Feature scaling is mandatory**
   Pixels normalised to \[0, 1] give meaningful distance measures; skipping scaling breaks default γ heuristics and fuels over‑fit.

9. **Unified preprocessing ensures fair comparisons**
   One `preprocess()` function feeds every model, so performance differences arise from algorithms—not data handling quirks.

10. **Lean enough for free Colab**
    The entire workflow (50 k training samples, all models) completes in under 10 minutes on a standard 2‑core Colab session, making it easy to reproduce anywhere.
