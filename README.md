# Data Availability and reproducibility

Due to the large size of the **UrbanSound8K dataset**, the full set of audio files is **not included in this repository**. The dataset contains thousands of `.wav` files, which would significantly increase storage requirements and make the repository difficult to manage and share.

### Constraint

The initial stage of this project requires:

* Reading metadata (`UrbanSound8K.csv`)
* Randomly selecting one audio file from each class
* Loading and processing multiple `.wav` files
* Combining them into a single urban soundscape

Including all raw audio files in the repository created me a **storage burden** and reduced accessibility.

# How this was handled

To address this limitation while maintaining reproducibility:

### 1. Sample-based approach

* A **small subset of audio files** has been included in the repository.
* This allows users to understand and test the data pipeline without needing the full dataset.
* if the person who replicates this need, he or she can run the .qmd file from the beginning with the sample files chosen, also following the approach is possible.

### 2. Pre-generated combined soundscape

* The final combined audio file:

  ```text
  combined_urban_soundscape.wav
  ```

  is included in the repository.

* This file represents the **processed and merged urban soundscape** used in the visualization.


# if needed, where to start running the project - Easy way

Users who want to reproduce the visualization **do not need the original dataset**.

They can directly start from:

## Spectrogram generation step

```r
spec <- spectro(
  combined_wave,
  plot = FALSE,
  wl = 512,
  ovlp = 75
)
```

From this point onward, the pipeline:

* extracts **time, frequency, and energy**
* transforms the data into **city-building features**
* generates the **animated skyline**

