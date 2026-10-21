# Pizza Districts — The K-Means Challenge

A self-contained, responsive browser game for teaching k-means clustering to graduate students.

## Run locally
Open `docs/index.html` in a modern browser. No build step, dependencies, API keys, or server required.

## Deploy to GitHub Pages
1. Push the repository to GitHub (the game lives at `docs/index.html`).
2. Open **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**, choose `main` and `/docs`, then save.
4. Wait for the Pages deployment workflow to finish; GitHub will show the site URL in Settings → Pages.

## How a round works
1. **Choose k.** Before placing anything, students inspect the map and answer: *How many pizza stores do you think are needed to serve these neighborhoods well?* (1–8).
2. **Place stores.** Click the map to drop that many stores, then drag them as needed.
3. **Optimize.** Run one k-means iteration at a time or run to convergence from the current layout.
4. **Submit.** Each city allows 3 submissions. The best submission counts.

Live metrics: total delivery distance, SSE (the k-means objective), attempts used, and round score.

## Characters
All characters are drawn in the page's own SVG (no image files) and can be hidden with the **Characters** button above the map. Movement is skipped for players who prefer reduced motion.

- **Pat Grid, city planner:** briefs the player before each city, hinting at its twist (fuzzy edges, uneven sizes, outliers, bridges) without revealing the intended k. The **Brief** button reopens it.
- **Chefs:** one beside each store. They wave while a k-means step runs and cheer when a round succeeds.
- **Delivery drivers:** after each step, a driver rides from each store to every house in its zone at the same speed, so long trips visibly take longer.
- **Grumpy residents:** houses more than twice the typical delivery distance of the reference layout frown. The legend shows how many there are and what share of SSE they cause, which illustrates why squared distance punishes far-away houses.
- **Rosa Crust, food critic:** presents the final report with a star rating and a short review based on chosen k, SSE gaps, and attempts.

## Scoring and benchmark
Minimizing SSE alone always favors more clusters (one store per house gives SSE = 0), so each map has a hidden **intended k** equal to the number of neighborhoods it was generated from. The benchmark SSE for any k is the best of 60 k-means++ runs with a fixed seed per city and k, so it is identical on every page load.

- **Model choice (50 pts):** 50 for the intended k, 20 if off by one, 0 otherwise.
- **Optimization (50 pts):** 50 when your SSE equals the benchmark SSE for the k you chose, falling linearly to 0 at a 50% gap.
- **Attempt penalty:** attempt 2 earns 85% and attempt 3 earns 70% of those points.

Choosing the intended k with an SSE within 5% of the benchmark ends the round with a celebration (customers run to their stores). After all five cities, a final report shows chosen k, reference k, your SSE, benchmark SSE, SSE gap, attempts, points per round, and total score (out of 500).

## Cities
1. **Starterville** (k = 3): 24 houses in three clearly separated neighborhoods.
2. **Riverside** (k = 4): four neighborhoods with softer borders.
3. **Metrovale** (k = 2): two broad districts plus distant outlier houses.
4. **Harbor District** (k = 5): neighborhoods of very different sizes.
5. **Night Shift** (k = 6): many neighborhoods, bridge houses, and an outlier.

## Teaching note
Classical k-means minimizes the **sum of squared Euclidean distances** to centroids. The game also reports the sum of raw delivery distances to connect the mathematical objective to the scenario, but those two objectives are not identical. The benchmark uses multiple seeded starts as a heuristic; it does not prove the global optimum. The intended k is a design choice for each map; formal criteria such as the elbow method or silhouette score can be discussed as alternatives and may disagree with each other.
