# Code2Flow Visualizer - Usage Guide

## Installation

Install the package from PyPI:

```bash
pip install code2flow-visualizer
```

## Quick Start

### 1. Basic Decorator Usage

```python
from code2flow import visualize

@visualize
def factorial(n):
    if n <= 1:
        return 1
    return n * factorial(n - 1)

# Run the function - this will generate a visualization
result = factorial(5)
print(f"Result: {result}")
```

### 2. Manual Flow Tracking

```python
from code2flow import CodeFlow

def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr

# Create a flow tracker
flow = CodeFlow()
flow.trace(bubble_sort, [64, 34, 25, 12, 22, 11, 90])

# Export the visualization
flow.export_image("bubble_sort_flow.png")
flow.export_mermaid("bubble_sort_flow.md")
```

### 3. Jupyter Notebook Integration

```python
from code2flow import FlowVisualizer

def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# In Jupyter notebook
visualizer = FlowVisualizer()
visualizer.track_function(fibonacci, 6)
visualizer.display()  # Shows interactive widget
```

## Package Import

Note: Even though you install `code2flow-visualizer`, you import it as `code2flow`:

```python
import code2flow
# or
from code2flow import visualize, CodeFlow, FlowVisualizer
```

## Export Formats

The library supports multiple export formats:

- **PNG/SVG images**: For documentation and presentations
- **Mermaid.js**: For GitHub markdown and documentation sites
- **Graphviz DOT**: For advanced customization
- **Interactive HTML**: For web-based viewing

## Configuration

You can customize the visualization:

```python
from code2flow import CodeFlow

flow = CodeFlow(
    theme="dark",
    show_variables=True,
    max_depth=10,
    highlight_changes=True
)
```

## Troubleshooting

If you encounter any issues:

1. Make sure you have Python 3.8 or higher
2. Try updating the package: `pip install --upgrade code2flow-visualizer`
3. Check the [GitHub issues](https://github.com/Aryan0854/code2flow-visualizer/issues) for known problems
4. Report new bugs on the GitHub repository

## More Examples

Check the `examples/` directory in the GitHub repository for more comprehensive examples.
