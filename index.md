# Predicting Search Content Decay: A Machine Learning Approach to SEO Refresh Prioritization

## Abstract
Content decay silently drains organic search traffic. This research investigates whether trailing search metrics can accurately predict future traffic drops. By training a Random Forest classifier on anonymized search data, the model successfully identified high-value URLs at risk of decay. This resulted in a prioritized action playbook that allows content teams to deploy targeted updates over manual guesswork.

## Introduction / Problem Statement
In enterprise SEO, monitoring thousands of URLs manually is impossible. Content teams need a decision-support system to prioritize their limited human hours. This project builds an opportunity scoring model that acts as an automated radar, surfacing high-value pages showing mathematical signs of decay so they can be refreshed.

## Data
The analysis was conducted using the FlyRank ML Internship dataset. The data consists of anonymized Google Search Console metrics (e.g., `impressions_90d`, `clicks_90d`, `avg_position`, and `ctr`). 
*   **Exclusions:** All client identifiers, domains, exact URLs, and raw exports were strictly excluded to ensure public safety and compliance.

## Methodology
*   **Target Label:** The target was defined mathematically as a directional trend ('decay' vs 'stable') based on trailing visibility metrics. 
*   **Features & Assumptions:** Assumes historical visibility momentum is an indicator of future performance. Features included temporal snapshots of content performance.
*   **Baseline:** The model was benchmarked against a standard rule-based baseline (e.g., triggering a review if a page fell below position 10).
*   **Validation Design:** To prevent data leakage, the model was validated using a strict Grouped Split by `client_id`. This ensured the model was tested on completely unseen clients. 

## Results
*   The Random Forest model outperformed the naive baseline in identifying nuanced decay patterns.
*   **Charts:** *(Note: Add the `action_distribution.png` chart you exported in Week 7 here)*.

## Limitations & Honest Framing
This model serves strictly as a **directional, decision-support tool**.
*   **The Lag Effect:** Relying on trailing 90-day metrics means it is inherently slow to react to sudden Google algorithm updates.
*   **Business Blindspots:** The model measures search opportunity, not business profit.
*   **Human Review Required:** The model does not prove causal refresh impact. Human editors must review the SERP landscape to ensure user intent has not shifted.

## Ranked Recommendations
The output is a cost-value action queue, sorted by historical impressions:
*   **FULL_REFRESH:** Assigned to URLs that drove massive traffic but have slipped off Page 1.
*   **REWRITE_METADATA:** Assigned to URLs maintaining Page 1 rankings but failing to capture clicks (low CTR).

## Reproducibility
All code, EDA, and modeling pipelines can be found in the `work/` directory of this repository, which holds every assignment notebook.

## Acknowledgments & Data Credit
Built on the FlyRank ML Internship dataset. Visit [https://flyrank.ai](https://flyrank.ai) for more information.