# PyExpressions

**Python String Expressions allowing runtime creation and definition of String Logic Expressions**

PyExpressions provides a streamlined, flexible framework for evaluating, manipulating, and executing string-based logic expressions natively at runtime in Python. It is designed for applications requiring dynamic evaluation of configurations, user-provided logic strings, query filtering, and rule engines.

---

## Features

- **Runtime Evaluation**: Create and safely parse logical string rules dynamically.
- **Custom Definitions**: Define and bind custom operators and functions directly in the parsing engine.
- **Security Oriented**: Isolated execution context, mitigating the risks inherently associated with `eval()`.
- **Fast and Lightweight**: Minimal overhead and low footprint, ensuring high-performance evaluations.

---

## Installation

PyExpressions requires **Python 3.13** or higher. Install the package via pip:

```bash
pip install -e .
```

---

## Quick Start

Below is a conceptual example of how PyExpressions can be used to parse and evaluate dynamic string logic.

```python
from pyexpressions import ExpressionContext

# 1. Initialize a context
ctx = ExpressionContext()

# 2. Define custom context variables or functions
ctx.set("minimum_value", 10)
ctx.set("is_valid", lambda x: x > 0)

# 3. Create a logic expression dynamically
expr_string = "value >= minimum_value and is_valid(value)"

# 4. Evaluate the expression with dynamic inputs
result1 = ctx.evaluate(expr_string, {"value": 15})
print(f"Result for 15: {result1}") # Output: True

result2 = ctx.evaluate(expr_string, {"value": 5})
print(f"Result for 5: {result2}")  # Output: False
```

---

## Advanced Usage

### Custom Operators

You can extend the engine's capability by adding custom operations suited to your data structures:

```python
ctx.add_operator("CONTAINS", lambda a, b: b in a)

expression = "'apple' CONTAINS item"
ctx.evaluate(expression, {"item": "app"}) # Output: True
```

### Complex Rule Sets

PyExpressions is perfect for reading config definitions or database driven rules at runtime and applying them across data pipelines to classify or filter data entries without touching the underlying Python codebase.

---

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the issues page or submit a Pull Request.

---

## License

This project is licensed under the Apache License. See the `LICENSE` file for more details.
