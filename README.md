# Genetic Algorithm-Based Feature Selection for Network Intrusion Detection

## Overview

This project applies a **Genetic Algorithm (GA)** to perform feature selection for network intrusion detection across multiple benchmark datasets. The goal is to identify compact, high-performing feature subsets that maximize classifier F1 performance while minimizing feature count — evaluated across multiple classifiers and datasets.

This was completed as part of **IDAI-720 Research** at Rochester Institute of Technology (RIT).

---

## Repository Structure

```
├── ga_project_fin.ipynb             # Final experiment notebook
├── GA_Research_RIT_Final.pptx       # Final project presentation
│
├── datasets/
│   ├── nsl_kdd/
│   │       KDDTrain+.txt            # NSL-KDD training set
│   │       KDDTest+.txt             # NSL-KDD test set
│   └── unsw_nb15/
│           UNSW_NB15_training-set.csv
│           UNSW_NB15_testing-set.csv
│
├── ga_checkpoints/
│   │   ga_log_seed42.csv            # GA training log (seed 42)
│   │   nsl_kdd_preprocessor.pkl     # Fitted preprocessor — NSL-KDD
│   │   unsw_nb15_preprocessor.pkl   # Fitted preprocessor — UNSW-NB15
│   └── ga_checkpoint_gen*.pkl       # Per-generation GA checkpoints
│
├── ga_results/
│   │   e1_results.csv               # Experiment 1: baseline F1 by classifier
│   │   e2_results.csv               # Experiment 2: F1 heatmap across features
│   │   e3_results.csv               # Experiment 3: GA convergence run
│   │   e4_results.csv               # Experiment 4: cross-dataset heatmap
│   │   e5_results.csv               # Experiment 5: GA vs baseline F1
│   │   e6_feature_frequency.csv     # Experiment 6: feature selection frequency
│   │   e6_per_seed.csv              # Experiment 6: per-seed breakdown
│   │   e6_stability.csv             # Experiment 6: Jaccard stability analysis
│   │   e7_transfer.csv              # Experiment 7: cross-dataset transfer
│   │   final_combined_results.csv   # All experiments combined
│   └── stats_results.csv            # Statistical significance results
│
└── ga_figures/
        e1_f1_by_classifier.png
        e2_f1_heatmap.png
        e2_feature_counts.png
        e3_f1_by_classifier.png
        e3_ga_convergence.png
        e4_f1_heatmap.png
        e5_f1_by_classifier.png
        e5_ga_convergence.png
        e6_boxplot_f1.png
        e6_feature_frequency.png
        e6_jaccard_heatmap.png
        e7_delta_m_bar.png
        e7_within_vs_cross.png
        final_boxplot_ga.png
        final_delta_m.png
        final_heatmap_nsl.png
        final_heatmap_unsw.png
        stats_ga_vs_baselines.png
```

---

## Datasets

| Dataset | Description |
|---|---|
| **NSL-KDD** | Improved KDD Cup 1999 dataset for network intrusion detection |
| **UNSW-NB15** | Modern network intrusion dataset with 9 attack categories |

> Note: The CICIDS2017 dataset was considered but not included in final experiments.

---

## Experiments

| Experiment | Description |
|---|---|
| E1 | Baseline F1 scores by classifier (all features) |
| E2 | F1 heatmap across feature subsets and classifiers |
| E3 | GA convergence behavior over generations |
| E4 | Cross-dataset F1 heatmap |
| E5 | GA-selected features vs. full feature baseline |
| E6 | Feature selection stability — frequency, Jaccard similarity across seeds |
| E7 | Cross-dataset transfer performance (within vs. cross-domain) |
| Final | Combined statistical analysis vs. baselines |

---

## Methodology

- **Algorithm:** Genetic Algorithm with tournament selection, uniform crossover, and bit-flip mutation
- **Fitness Function:** Weighted F1 score on validation set
- **Classifiers Evaluated:** Multiple (see results CSVs)
- **Reproducibility:** Fixed seed (`seed=42`) with per-generation checkpoints saved
- **Stability Analysis:** Jaccard similarity across multiple random seeds (E6)
- **Transfer Analysis:** Features selected on one dataset evaluated on another (E7)

---

## Getting Started

### Requirements

```bash
pip install numpy pandas scikit-learn matplotlib seaborn jupyter
```

### Running the Notebook

```bash
jupyter notebook ga_project_fin.ipynb
```

Checkpoints are saved every 10 generations to `ga_checkpoints/`. To resume from a checkpoint, load the relevant `.pkl` file at the top of the notebook.

---

## Key Results

- GA-selected feature subsets achieve competitive F1 scores with significantly fewer features than the full feature set
- Stable feature subsets identified across multiple seeds (E6 Jaccard analysis)
- Cross-dataset transfer results reported in E7 (`e7_transfer.csv`)
- Full statistical comparison against baselines in `stats_results.csv`

---

## Authors

- Rochester Institute of Technology — IDAI-720 Research Project

---

## Acknowledgements

- [NSL-KDD Dataset](https://www.unb.ca/cic/datasets/nsl.html) — University of New Brunswick
- [UNSW-NB15 Dataset](https://research.unsw.edu.au/projects/unsw-nb15-dataset) — UNSW Canberra
