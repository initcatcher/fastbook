# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the official repository for "Deep Learning for Coders with fastai and PyTorch" book by Jeremy Howard and Sylvain Gugger. The repository contains Jupyter notebooks that serve as both educational materials and the source for the published book.

## Commands

### Package Management (uv)

```bash
# Install dependencies
uv sync

# Add a new dependency
uv add <package-name>

# Add a dev dependency
uv add --dev <package-name>

# Run commands in the virtual environment
uv run python <script.py>
uv run jupyter notebook
```

### Running Notebooks

```bash
# Start Jupyter notebook server
uv run jupyter notebook

# Run a specific notebook from command line
uv run jupyter nbconvert --execute <notebook.ipynb>
```

### Notebook Cleaning

The `tools/clean.py` script processes notebooks to create "clean" versions (output to `clean/` directory):
```bash
uv run python tools/clean.py
```

This removes cell outputs and strips special tags (id, caption, alt, width, hide_input, hide_output) while preserving header cells and cells marked with `# clean`.

## Architecture

### Repository Structure

- Root `.ipynb` files: Full book chapters (01-20) with outputs and annotations
- `clean/`: Cleaned notebook versions without outputs (for teaching/exercises)
- `utils.py`: Shared utilities imported by notebooks - includes:
  - Display configuration (matplotlib, pandas, numpy settings)
  - `search_images_bing()` / `search_images_ddg()`: Image search functions for data collection
  - `gv()`: GraphViz diagram helper
  - `draw_tree()`: Decision tree visualization using sklearn
  - `cluster_columns()`: Correlation clustering visualization
  - `plot_function()`: Simple function plotting helper

### Key Dependencies

- **fastai**: High-level deep learning library (the main subject)
- **nbdev**: Notebook development tools for cleaning and processing
- **graphviz**: Visualization of decision trees and diagrams
- **azure-cognitiveservices-search-imagesearch**: Bing image search for dataset creation

### Notebook Conventions

- Chapters are numbered 01-20 (e.g., `01_intro.ipynb`)
- Appendices prefixed with `app_` (e.g., `app_jupyter.ipynb`)
- Cells with `# hide_input` or `# hide_output` are processed specially for book publishing
- `# clean` tag marks cells to preserve in cleaned versions
