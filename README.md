[![Build Status](https://travis-ci.org/OriginQ/QPanda-SDK.svg?branch=master)](https://travis-ci.org/OriginQ/QPanda-SDK)
## QPanda 2.0


![图片: ](https://images-cdn.shimo.im/BtuP6aVe0oo2jRlZ/image.png)

Qpanda 2.0 is a quantum software development kit used to deal with quantum circuits and experiments on various quantum computers.

There are three processes in QPanda: **initialization**, **compilation** and **running**.

**Initialization**:

The initialization allows users to design different quantum circuits to deal with the corresponding problems.

**Compilation**:

Compilation allows users to rewrite them to run on different backends (such as simulators, quantum chips, quantum chips of different companies, etc.).

**Running**:

that is, the process of collecting results(classical information), depending on the design of the problem to do the corresponding operation.

## The Design Ideas of QPanda


The design of **QPanda** is forward-looking, considering that quantum computing will flourish and be widely applied in the future. So QPanda did the following consideration when it was designed:

1.  Full series compatibility.

2.  Standard architecture.

3.  Standardized quantum machine model.

## The Project Includes：

![图片: ](https://images-cdn.shimo.im/j71VAaimgHkKWXEW/image.png)

-   **QPanda SDK**：

C++ is used as the host language to compiling quantum programs in QPanda 2.0 SDK. It enables users to connect and execute quantum programs conveniently.

-   **QRunes**：

Qrunes is a set of quantum computing instructions developed by the Origin quantum team.

-   **QRunes(QASM) Generator**：

Qrunes Generator is a C + + library that supports generating Qrunes directives in function calls.

-   **[QPanda Documentation](./QPanda-2.0.Documentation/README.md)**：

 Instructions for QPanda software. It includes algorithm summary, corresponding quantum circuits, corresponding QPanda code, etc., aiming at guiding users to use QPanda correctly and quickly.

 ## License
 Apache License 2.0
