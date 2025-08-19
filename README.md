#!/usr/bin/env python3
"""
Sui Single-Atom Approximation Numerical Verification

This script demonstrates a simple single-atom approximation for 
F(s) = exp(-i*t) along the imaginary axis.

Author: Your Name
License: MIT
"""

import numpy as np

# ----------------- 参数 -----------------
t = np.linspace(-5, 5, 101)       # 密集采样
t = t[t != -1]                     # 手动去掉奇点

# 目标函数 F(s)
F = np.exp(-1j*t)

# 单原子 Phi(s)
Phi = np.exp(-(1j*t - 1j)**2) * (1 + (1j*t - 1j)/(1j*t + 1j))

# 计算单原子系数 c1
c1 = np.vdot(F, Phi) / np.vdot(Phi, Phi)

# 输出结果
print("Single-atom coefficient c1:", c1)
# 误差示例
error = np.max(np.abs(F - c1*Phi))
print("Max pointwise error:", error)
---

### **3️⃣ LICENSE (MIT)**

```text
MIT License

Copyright (c) 2025 Your Name

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

[...standard MIT text continues...]
# Sui Single-Atom Approximation

This repository provides a minimal Python script to numerically verify
the Sui single-atom approximation for F(s) = exp(-i t) along the imaginary axis.

## Usage

Run the script with:

```bash
python sui_single_atom.py
