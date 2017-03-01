# Tallying Cognoma Contributions

[`contrib.ipynb`](contrib.ipynb) tallies the contributions for all [Cognoma repositories](https://github.com/cognoma) using the GitHub API.
The number of contributions per user by repository is displayed in the contribution heatmap:

![Contribution Heatmap](contribution-heatmap.png "Intensity shows the number of contributions") 

The raw data for this visualization is stored in [`contribution-by-repo.tsv`](contribution-by-repo.tsv).
The total number of contributions per user is stored in [`contributor-summary.tsv`](contributor-summary.tsv).

To update contribution information, run the following from this directory:

```sh
jupyter nbconvert --inplace --execute --ExecutePreprocessor.timeout=-1 contrib.ipynb
jupyter nbconvert --to=script contrib.ipynb
```
