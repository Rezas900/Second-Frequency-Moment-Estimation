

# Second Frequency Moment ($F\_2$) Estimation

An implementation and evaluation of the space-efficient algorithm for approximating the second frequency moment ($F\_2$) from the paper "The Space Complexity of Approximating the Frequency Moments" by Alon, Matias, and Szegedy.1996


## Overview

The second frequency moment, $F\_2 = \\sum (m)\_i^2$ (where $m\_i$ is the count of item *i*), is a key statistic for measuring data skew in large streams. Calculating it exactly is often infeasible as it requires memory linear in the number of unique items ($\\Omega(n)$)[cite: 19].

This project implements the paper's randomized algorithm which estimates $F\_2$ in logarithmic space.
The core idea is to use 4-wise independent random vectors to produce an unbiased estimator whose value is very close to the true $F\_2$ with high probability.

## Experiment & Results

The algorithm's accuracy was tested using three different types of random vectors: **pairwise independent**, **4-wise independent**, and **fully random**. For each method, the estimation was run 20 times on five different datasets, and the results were averaged.

The experimental results confirm the paper's theoretical findings: **4-wise independent vectors yield the most accurate estimations.**

The following table shows a sample result from the `zipf.1.5.txt` dataset:

| Method | Estimated $F\_2$ | Actual $F\_2$ | Relative Error |
| :--- |:-----------------| :--- |:---------------|
| **4-wise Independent** | `1.77e+10`       | `1.89e+10` | **\~6.35%**    |
| Fully Random | `1.45+e10`       | `1.89e+10` | **\~23.2%**    |
| Pairwise Independent | `4.15+e10`       | `1.89e+10` | `---------`    |

## How to Run

### Prerequisites

  * Python 3.8+
  * NumPy

### Installation

```bash
git clone [URL-TO-YOUR-REPOSITORY]
cd [REPOSITORY-NAME]
pip install -r requirements.txt
```

### Execution

Run the algorithm using the following command structure:



  * `--dataset_path`: Path to the input data file.
  * `--method`: The type of random vector to use (`pairwise`, `4wise`, `fully_random`).

## Conclusion

This project successfully demonstrates the practical effectiveness of the AMS algorithm, validating that 4-wise independence is a sufficient and efficient property for accurate, space-constrained $F\_2$ estimation.

## Reference

  * Alon, N., Matias, Y., & Szegedy, M. (1999). The space complexity of approximating the frequency moments. *Journal of Computer and System Sciences*, 58(1), 137-147.