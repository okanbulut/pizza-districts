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

## Learning interactions
- Drag exactly three shop/centroid markers.
- Houses are assigned to their nearest shop and colored by delivery zone.
- Live metrics show total Euclidean delivery distance, average trip, and the k-means sum-of-squared-errors (SSE) objective.
- Run one assignment/update iteration or run a multi-start auto-optimization.
- Explore three city layouts and discuss sensitivity to initialization and local minima.

## Teaching note
Classical k-means minimizes the **sum of squared Euclidean distances** to centroids. The game also reports the sum of raw delivery distances to connect the mathematical objective to the scenario, but those two objectives are not identical. The benchmark is a heuristic best-of-multiple-starts estimate, not a proof of the global optimum.
