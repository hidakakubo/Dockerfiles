FROM rocker/r-ver:4.3.2

# Install system dependencies for R packages
RUN apt-get update && apt-get install -y \
    libnetcdf-dev \
    libglpk40 \
    libglpk-dev \
    && rm -rf /var/lib/apt/lists/*

# Install Bioconductor and required R packages
RUN R -e "if (!require('BiocManager', quietly = TRUE)) install.packages('BiocManager'); \
          BiocManager::install(version = '3.18')"

# Install pacman and load required packages
RUN R -e "install.packages('pacman'); \
          library(pacman); \
          pacman::p_load('impute', 'pcaMethods', 'globaltest', 'GlobalAncova', \
                        'Rgraphviz', 'preprocessCore', 'genefilter', 'sva', 'limma', \
                        'KEGGgraph', 'siggenes', 'BiocParallel', 'multtest', 'RBGL', 'edgeR', 'fgsea')"

# Install specific Bioconductor packages
RUN R -e "BiocManager::install(c('mzR', 'MSnbase'))"

# Install devtools
RUN R -e "install.packages('devtools')"

# Install MetaboAnalystR from GitHub
RUN R -e "devtools::install_github('xia-lab/MetaboAnalystR', build = TRUE, build_vignettes = FALSE)"