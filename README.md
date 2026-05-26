# Pandas Magic Course

A 1-week self-study course for making pandas examples in machine-learning and deep-learning textbooks feel less like magic.

The course focuses on **basic pandas proficiency for ML workflows**: reading tutorial-style code, understanding hidden pandas behavior, cleaning real datasets, doing exploratory data analysis, and using `matplotlib` / `seaborn` to make each transformation visible.

## Who this is for

This course is for learners who already have some Python exposure and are starting to see pandas in ML/deep-learning books, notebooks, or tutorials, but feel surprised by features such as:

- `DataFrame` vs `Series`
- `loc` vs `iloc`
- label-based vs position-based indexing
- boolean masks
- automatic index alignment
- chained operations
- missing-value cleanup
- categorical encoding
- `groupby` and aggregation
- joins, concat, pivot/melt reshaping
- feature/target preparation for ML

## Learning goals

By the end of the week, you should be able to:

1. Read pandas-heavy ML tutorial snippets and explain what each line does.
2. Predict the resulting object type, shape, columns, and index after common operations.
3. Clean common ML tabular-data problems: missing values, dtypes, categoricals, duplicates, and simple outliers.
4. Use EDA plots to understand distributions, relationships, and before/after effects of transformations.
5. Prepare `X` feature matrices and `y` target vectors for a model-ready workflow.
6. Recognize common pandas operations used in tutorials even when you cannot yet recall every API detail.

## Course format

- **Duration:** 7 days
- **Time:** 60–90 minutes per day
- **Style:** read → annotate → rebuild → visualize
- **Primary lesson format:** Jupyter notebooks, not standalone pure Python `.py` lesson files
- **Assessment:** final mini-project notebook

Each day follows this pattern:

1. Read a short textbook/tutorial-style pandas snippet.
2. Annotate each line:
   - What object type is produced?
   - Which rows/columns are affected?
   - What happens to the index?
   - Why is this operation useful in an ML workflow?
3. Rebuild the same idea on a course dataset.
4. Verify the result with a small table, plot, or before/after comparison.

## Main datasets

The course uses three canonical, reality-based datasets:

| Dataset | Why it is used |
| --- | --- |
| [Palmer Penguins](https://github.com/allisonhorst/palmerpenguins) | Friendly EDA, selecting/filtering, `Series` vs `DataFrame`, `groupby`, visual comparisons |
| [Titanic](https://www.kaggle.com/c/titanic) | Missing values, categoricals, masks, feature engineering, feature/target prep, common ML tutorial idioms |
| [California Housing](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_california_housing.html) | Numeric ML-style features, target vectors, distributions, correlations, outlier inspection, regression-style preprocessing |

Tiny synthetic examples are allowed only as microscope demos for behavior that is hard to see clearly in a real dataset, such as index alignment, `loc` vs `iloc`, assignment semantics, or join behavior.

## 7-day syllabus

### Day 1 — DataFrame and Series mental model

**Dataset:** Palmer Penguins

**Core ideas:**

- Loading data
- `.head()`, `.info()`, `.describe()`, `.shape`, `.columns`, `.dtypes`
- `DataFrame` vs `Series`
- selecting one column vs many columns
- first plot checks with seaborn

**Visual checks:**

- histogram/distribution of numeric columns
- scatter plot of flipper length vs body mass
- count plot by species

### Day 2 — Selecting rows/columns without fear

**Dataset:** Palmer Penguins + tiny indexing microscope examples

**Core ideas:**

- `loc` vs `iloc`
- label vs position
- boolean masks
- combining conditions with `&`, `|`, `~`
- assignment with `.loc`
- index alignment surprises

**Visual checks:**

- before/after row counts after filtering
- filtered scatter plots by species/island/sex
- side-by-side summary tables before and after a mask

### Day 3 — EDA and `groupby`: split, apply, combine

**Dataset:** Palmer Penguins

**Core ideas:**

- `groupby`
- `.agg()`
- grouped counts and means
- multi-column grouping
- `reset_index()`
- when grouped output changes shape

**Visual checks:**

- bar plots of group means
- box plots by category
- grouped summary tables next to charts

### Day 4 — Titanic cleaning: missing values, dtypes, categoricals

**Dataset:** Titanic

**Core ideas:**

- missing-value inspection with `.isna()` / `.isna().sum()`
- dropping vs imputing
- creating missingness indicators
- dtype cleanup
- category inspection with `.value_counts()`
- categorical encoding with `get_dummies` or simple maps

**Visual checks:**

- missingness bar chart
- survival rate by sex/class/embarked
- age distribution before/after imputation

### Day 5 — ML textbook idioms: feature/target preparation

**Dataset:** Titanic

**Core ideas:**

- selecting feature columns
- separating `X` and `y`
- excluding leakage columns
- chained method calls at a readable level
- train/test split context
- reading common tutorial snippets line by line

**Visual checks:**

- feature table before/after encoding
- class balance plot
- survival-rate grouped plots

### Day 6 — California Housing: numeric EDA and model-ready data

**Dataset:** California Housing

**Core ideas:**

- creating a pandas `DataFrame` from scikit-learn data
- numeric feature inspection
- correlation matrix
- outlier inspection
- simple feature transformations
- thinking in terms of `X` and `y` for regression

**Visual checks:**

- histograms for numeric features
- correlation heatmap
- scatter plots of median income vs target

### Day 7 — Joins, concat, reshape, and final mini-project

**Datasets:** Titanic or California Housing; small derived lookup tables

**Core ideas:**

- `merge` / joins
- `concat`
- `pivot`, `pivot_table`, `melt`
- using reshape for plotting and summaries
- final mini-project completion

**Visual checks:**

- before/after row and column counts for joins/concat
- long-form vs wide-form plot examples
- mini-project EDA and cleaning plots

## Final mini-project

Choose either Titanic or California Housing and produce a notebook that:

1. Loads and inspects the dataset.
2. Explains the initial shape, columns, dtypes, and missing values.
3. Performs at least three meaningful pandas transformations.
4. Includes before/after evidence for cleaning or feature changes.
5. Includes at least four EDA plots.
6. Prepares `X` and `y` for an ML-style workflow.
7. Explains each transformation in plain language, including:
   - object type produced
   - shape changes
   - column changes
   - index behavior
   - why the operation was used

## Recommended environment

This starter course repo is a minimal [`uv`](https://docs.astral.sh/uv/) project. It intentionally starts with dependency metadata only; notebooks and lesson code should be added by the course-building issues rather than preemptively generated.

When lesson materials are added, they should be delivered as Jupyter notebooks. Avoid standalone pure Python `.py` lesson files unless a future issue explicitly calls for a small supporting utility.

Install dependencies and start Jupyter:

```bash
uv sync
uv run jupyter notebook
```

If you need to add a package later:

```bash
uv add package-name
```

## Well-known references used by the course

Official pandas references:

- [pandas getting started tutorials](https://pandas.pydata.org/docs/getting_started/)
- [How do I select a subset of a DataFrame?](https://pandas.pydata.org/docs/getting_started/intro_tutorials/03_subset_data.html)
- [Indexing and selecting data](https://pandas.pydata.org/docs/user_guide/indexing.html)
- [Group by: split-apply-combine](https://pandas.pydata.org/docs/user_guide/groupby.html)
- [Merge, join, concatenate and compare](https://pandas.pydata.org/docs/user_guide/merging.html)
- [Reshaping and pivot tables](https://pandas.pydata.org/docs/user_guide/reshaping.html)
- [Working with missing data](https://pandas.pydata.org/docs/user_guide/missing_data.html)
- [Visualization](https://pandas.pydata.org/docs/user_guide/visualization.html)

Dataset and tutorial references:

- [Palmer Penguins project](https://github.com/allisonhorst/palmerpenguins)
- [Quarto Palmer Penguins example](https://quarto.org/docs/authoring/penguins.html)
- [Kaggle Titanic competition](https://www.kaggle.com/c/titanic)
- [pandas Titanic CSV](https://raw.githubusercontent.com/pandas-dev/pandas/main/doc/data/titanic.csv)
- [pandas Titanic tutorial](https://pandas.pydata.org/docs/getting_started/intro_tutorials/02_read_write.html)
- [scikit-learn California Housing dataset](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_california_housing.html)
- [scikit-learn train/test split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)
- [seaborn example gallery](https://seaborn.pydata.org/examples/index.html)

## Build roadmap

The GitHub issues in this repository break the course into independently grabbable notebook/content slices. Each issue includes acceptance criteria and well-known references for the lesson.

- [#1 Bootstrap course repo and notebook environment](https://github.com/majorgilles/pandas-magic-course/issues/1)
- [#2 Day 1: DataFrame/Series mental model with Palmer Penguins](https://github.com/majorgilles/pandas-magic-course/issues/2)
- [#3 Day 2: loc, iloc, masks, assignment, and index surprises](https://github.com/majorgilles/pandas-magic-course/issues/3)
- [#4 Day 3: EDA and groupby with Palmer Penguins](https://github.com/majorgilles/pandas-magic-course/issues/4)
- [#5 Day 4: Titanic cleaning — missing values, dtypes, and categoricals](https://github.com/majorgilles/pandas-magic-course/issues/5)
- [#6 Day 5: Feature/target prep and ML-textbook pandas idioms](https://github.com/majorgilles/pandas-magic-course/issues/6)
- [#7 Day 6: California Housing numeric EDA and ML-ready features](https://github.com/majorgilles/pandas-magic-course/issues/7)
- [#8 Day 6/7: Joins, concat, reshape, and before/after visual checks](https://github.com/majorgilles/pandas-magic-course/issues/8)
- [#9 Day 7: Final mini-project notebook and rubric](https://github.com/majorgilles/pandas-magic-course/issues/9)
- [#10 Create resource appendix of well-known pandas/ML tutorials](https://github.com/majorgilles/pandas-magic-course/issues/10)
