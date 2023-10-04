# Research: Galaxy Categorisation (Star Forming, Quiescent, Green Valley)
This is astrophysics research study using data from the COSMOS2020 catalog, to assess methodologies for galaxy categorisation in terms of their star formation capability. It was developed at the University of Lisbon, by Victor Sultanum and supervisor Cirino Pappalardo.

# Description
Galaxies can either be classified as "star forming", if they are relatively new and forming stars,
or "quiescent", if they are older and produce significantly less stars. In this research, we aim to
examine three different colour-colour galaxy categorisation approaches, and compare their ratios of
star forming to quiescent galaxies with those gathered via a full spectra energy distribution fitting,
in order to determine their efficiency in galaxy classification. This was attempted with data from
the latest release, as of writing, of the Cosmic Evolution Survey (COSMOS2020), in the 0 < z < 3
redshift range. The comparisons were done in the entire range at once, as well as separately in
six different redshift bins. Finally, the three criteria are examined with pseudo-confusion matrices,
excluding galaxies with a specific star formation rate between −11 to −10, which are the so-called
"green valley" galaxies in the midpoint of the two previous classifications. We found that, before
the removal of the green valley, the criteria did not yield very reliable results, yet upon the removal
two of them gave very satisfying results.

# The Code, and how to use it
The file 'lab.ipynb' can be accessed in a JupyterLab notebook.

It will be better understood by reading the accompanying paper, 'Astrophysics Star Formation Report.pdf'. Here I will give a **brief outline of what each section of the code does**. Both the paper and the following outline were written with an audience with knowledge in Physics/Astrophysics in mind.

## 1. Sample

### 1.1. Header
 This section of the code consists of importing the COSMOS2020 catalog along with all necessary packages.

### 1.2. Define Cells
  Here we filter the entire catalog, selecting for galaxies using LePhare type 0, setting the UVISTA magnitude upper limit to 22.4, and choosing the redshift range 0 < z < 3. This redshift range is then subdivided into 6 cells, 0 < z < 0.5, 0.5 < z < 1.0, 1.0 < z < 1.5, and so on.

### 1.3. Define SF, Q according to sSFR
  The code here classifies the galaxies as either Star Forming or Quiescent using the sSFR (specific star formation rate) criterion, for the entire redshift range as well as for each of the 6 bins.

### 1.4. Useful functions
  This section merely serves to write functions for confusion matrix, scatterplot and the specific Star Formation Rate analysis, according to our needs for this specific research. The sSFR analysis function can classify galaxies using different criteria and different redshift ranges, and also counts contaminants.

### 1.5. Galaxy Map
  Merely a map of all galaxies of interest after filtering for our purposes, with angle of declination on the x-axis and right ascension on the y-axis.

### 1.6. Redshift Distribution
  As the name implies, this shows the distribution of redshifts for all galaxies in the filtered sample.

## 2. Methods

### 2.1. UVJ
  Extract the fluxes for the U, V and J bands from EAZY. Then, compute the magnitudes. A histogram for both quantities is provided, for the galaxies in each redshift bin.

### 2.2. NUVrJ
  This time we directly extract the magnitudes from LePhare for the NUV, r and J bands. A histogram is provided for each z bin.

## 3. Results

### 3.1. Magnitudes (all bins)
  This section separates the U, V, J, NUV and r bands of the EM spectrum and makes a histogram for each.

### 3.2. Scatter plots + sSFR analysis
  For the UVJ and NUVrJ data extracted, a scatterplot showing the colour-colour diagrams of the sample is produced, as well as the classification lines that divide the sample between Star Forming and Quiescent galaxies, for three classification methods: "UVJ-1", "UVJ-2" and "NUVrJ". The proportion of Star Forming and Quiescent galaxies is then computed for each method using the sSFR analysis function defined earlier. This is done for the entire 0 < z < 3 range as well as separately for each bin.

### 3.3. sSFR Histogram
  This time, using the specific Star Formation Rate directly, we separate the galaxies in three categories: Star Forming, Quiescent and Green Valley (in between the first two). This fourth classification method was called "sSFR", and was the baseline, benchmark criterion for estimating the performance of the previous methods. Histograms are built for all redshift bins and compared to the classification methThods of the previous section.

## 4. Discussion

### 4.1. Remove green valley
  In this section we completely remove the green valley from the sample. Since the three methods UVJ-1, UVJ-2 and NUVrJ only separate into two classifications, it was necessary to remove the galaxies in the middle in order to better estimate the performance of each method more farily.

### 4.2. Evolution, with z, of the ratio of SF galaxies
  For each method, a line plot is drawn of the percentage of star forming and quiescent galaxies as a function of redshift. The resulting plot clearly shows that galaxies tend to be more star forming as redshift increases, since they appear younger.

### 4.3. Confusion Matrices
  The UVJ-1, UVJ-2 and NUVrJ methods are all compared to the sSFR method via a confusion matrix.
