# Constrained Nonlinear Optimization — Reproducible Python Study

A compact numerical analysis project illustrating constrained convex optimization, analytical derivatives, independent numerical cross-checks, and first-order Karush–Kuhn–Tucker (KKT) diagnostics.

**Project status:** A portfolio demonstration designed for you to run, understand, modify, and validate. Do not describe it as previously completed original research unless that is accurate. This project is not affiliated with AfterQuery or Turing.

## Mathematical model

Minimize

\[
f(x,y)=\tfrac12[(x-0.8)^2 + 2(y-0.2)^2]+0.1(x^4+y^4)
\]

subject to

\[
x+y=1,\qquad 0\leq x\leq1,\qquad 0\leq y\leq1.
\]

The Hessian is diagonal with entries \(1+1.2x^2\) and \(2+1.2y^2\), so the objective is strictly convex. The feasible set is convex and nonempty. Thus the solution is unique. The optimizer uses SLSQP with an analytic objective gradient, and reports feasibility and stationarity residuals.

## Install and run

```bash
python -m venv .venv
# Linux/macOS: source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1
pip install -r requirements.txt
python -m examples.run_example
python -m pytest -q
```

## Validation

The tests assess analytical gradients against centered finite differences at multiple points, verify positive-definiteness of the Hessian, check feasibility and KKT stationarity from several initial conditions, and independently verify the minimum via reduction to one dimension and SciPy's bounded scalar minimization.

## Suggested coding task extension

Implement the constrained optimizer from the stated mathematical model, output the estimated minimizer and objective value, then provide a unit-test suite covering optimality conditions, constraint violations, derivative correctness and solver consistency across initial conditions. A further extension could compare SLSQP with a Newton method applied to the reduced one-dimensional problem, providing an independent algorithm rather than only an independent interface to SciPy.

## Responsible portfolio use

Run the implementation, understand the model, and make your own documented enhancements. If the project is published, identify your own contributions accurately. Do not publish confidential employer or client task material.
