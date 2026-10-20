# Pizza Districts — The K-Means Challenge

A self-contained, responsive browser game for teaching k-means clustering to graduate students.

## Run locally
Open `index.html` in a modern browser. No build step, dependencies, API keys, or server required.

## Deploy to GitHub Pages
1. Create a GitHub repository (for example, `pizza-districts`).
2. Upload `index.html` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**, choose `main` and `/(root)`, then save.
5. Wait for the Pages deployment workflow to finish; GitHub will show the site URL in Settings → Pages.

## Game features
- Custom storefront graphics for the three draggable pizza-shop centroids, plus an updated map legend.
- Guided prompt encourages students to place shops manually before running k-means.
- Exactly three shops in every round; houses are assigned to their nearest shop.
- Live metrics for total Euclidean delivery distance, average trip, and the k-means sum-of-squared-errors (SSE) objective.
- Run one assignment/update iteration or use a multi-start auto-optimization. The game explicitly notes that one iteration—and convergence—does not guarantee the global optimum.
- Five progressively harder cities:
  1. **Starterville:** 24 houses in three clearly separated neighborhoods.
  2. **Riverside:** overlapping neighborhoods and more ambiguous assignments.
  3. **Metrovale:** overlap and distant outliers.
  4. **Harbor District:** uneven cluster sizes and bridge houses.
  5. **Night Shift:** ambiguous structure, bridge houses, and outliers to motivate comparison across initializations.

## Teaching note
Classical k-means minimizes the **sum of squared Euclidean distances** to centroids. The game also reports the sum of raw delivery distances to connect the mathematical objective to the scenario, but those two objectives are not identical. The benchmark and auto-optimization use multiple starts as a heuristic; neither proves the global optimum.
