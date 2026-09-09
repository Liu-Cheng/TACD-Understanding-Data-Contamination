# Understanding Data Contamination in Verilog-Generation LLMs

LaTeX source for the paper **Understanding Data Contamination in Verilog-Generation LLMs**, maintained through GitHub and Overleaf. The manuscript uses the IEEEtran journal template.

## Paper overview

The paper studies inconsistencies among existing contamination detectors for Verilog-generation LLMs and develops a CatBoost ensemble that combines their signals. Experiments evaluate detection effectiveness on DeepSeek-Coder-v1.5 variants, generalization across additional RTL-generation models, and estimated contamination in Verilog benchmarks.

This repository contains the manuscript, bibliography, and figures. It does not currently include detector implementations, experiment scripts, or the evaluation datasets.

## Repository structure

| File or directory | Contents |
| --- | --- |
| `top.tex` | Main document, title, authors, abstract, and section includes |
| `intro.tex` | Introduction |
| `related.tex` | Related work |
| `detection.tex` | Motivational study and boosting-based detector |
| `evaluation.tex` | Experimental setup, results, benchmark analysis, and ablations |
| `future.tex` | Future-work paragraphs included at the end of the combined conclusion section |
| `conclusion.tex` | Combined Conclusion and Future Work section; conclusion followed by `future.tex` |
| `cite.bib` | Bibliography |
| `figures/` | Figure assets used in the manuscript |
| `photo/` | Additional image assets |
| `rebuttal.tex` | Separate rebuttal source; not included by `top.tex` |
| `IEEEtran.cls` | Bundled IEEEtran document class |
| `README.txt`, `changelog.txt` | Original IEEEtran template documentation |

## Compile locally

Use a LaTeX distribution such as MiKTeX or TeX Live with **pdfLaTeX** and **BibTeX**. Install the packages requested by the manuscript and the `IEEEtran.bst` bibliography style through your distribution if needed.

From the repository root, create `output/pdf`, then run:

```sh
pdflatex -interaction=nonstopmode -halt-on-error -output-directory=output/pdf top.tex
bibtex output/pdf/top
pdflatex -interaction=nonstopmode -halt-on-error -output-directory=output/pdf top.tex
pdflatex -interaction=nonstopmode -halt-on-error -output-directory=output/pdf top.tex
```

On PowerShell, create the output directory with:

```powershell
New-Item -ItemType Directory -Force output/pdf
```

The compiled paper is written to `output/pdf/top.pdf`. Run the commands from the repository root so that LaTeX can resolve section files, figures, and `cite.bib`. If the executables are not on `PATH`, invoke them using their full installation paths.

Generated PDFs, auxiliary files, logs, and review images under `output/` are local build artifacts and are not part of the manuscript source to synchronize.

## Overleaf workflow

1. Import this GitHub repository into Overleaf, or pull the latest changes in the existing linked project.
2. Set the main document to `top.tex` and the compiler to **pdfLaTeX**.
3. Recompile after pulling changes to refresh the PDF.
4. Synchronize Overleaf edits back to GitHub before editing the same files locally; fetch and reconcile remote changes before pushing local edits.

## Items awaiting verification

- Section V-A describes the ensemble threshold-selection procedure, but its final numerical threshold, search range, and step size still require confirmation from experiment records. The baseline threshold policy for these experiments also needs confirmation.
- Some baseline results in Table III are blank in the current manuscript.

These items should be checked against the experiment records before the manuscript is finalized.
