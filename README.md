# Dimensionality Reduction and City Ranking Using Principal Component Analysis

## Overview

This project applies Principal Component Analysis (PCA) to assess the performance of 329 U.S. cities using a set of socioeconomic and quality of life attributes. Because the attributes are correlated, PCA provides a way to summarize them in an interpretable, low dimensional form.

The analysis has three objectives:

1. To reduce the dimensionality of the dataset while retaining as much of the original variability as possible.
2. To identify latent structures and relationships among the city attributes.
3. To draw meaningful conclusions about relative city performance, including a ranking of cities based on overall performance.

## Dataset

The dataset contains 329 U.S. cities, each described by nine attributes. According to the notes in the workbook, a higher score is better for every attribute. The attributes and the measures they summarize are as follows:

1. **Climate and Terrain:** very hot and very cold months, seasonal temperature variation, heating degree days and cooling degree days, freezing days, zero degree days, and ninety degree days.
2. **Housing:** utility bills, property taxes, and mortgage payments.
3. **Health Care and Environment:** per capita physicians, teaching hospitals, medical schools, cardiac rehabilitation centers, comprehensive cancer treatment centers, hospices, an insurance and hospitalization costs index, fluoridation of drinking water, and air pollution.
4. **Crime:** violent crime rate and property crime rate.
5. **Transportation:** daily commute, public transportation, Interstate highways, air service, and passenger rail service.
6. **Education:** pupil to teacher ratio in the public K through 12 system, an effort index in K through 12, and academic options in higher education.
7. **The Arts:** museums, fine arts and public radio stations, public television stations, universities offering a degree or degrees in the arts, symphony orchestras, theatres, opera companies, dance companies, and public libraries.
8. **Recreation:** good restaurants, public golf courses, certified lanes for tenpin bowling, movie theatres, zoos, aquariums, family theme parks, sanctioned automobile race tracks, pari mutuel betting attractions, major league and minor league professional sports teams, NCAA Division I football and basketball teams, miles of ocean or Great Lakes coastline, inland water, national forests, national parks or national wildlife refuges, and Consolidated Metropolitan Statistical Area access.
9. **Economics:** average household income adjusted for taxes and living costs, income growth, and job growth.

The city identifiers, Place ID and Place Name, were excluded from the PCA computations and were retained only for labelling and interpreting the results.

## Methodology

### Choice of the Correlation Matrix

The attributes are measured on different scales. For this reason, the analysis was conducted on the correlation matrix rather than the covariance matrix. Using the correlation matrix effectively standardizes the variables before PCA, so that no attribute dominates the components simply because of its scale.

### Correlation Structure

The correlation matrix was examined before the PCA was performed, with a threshold of 0.3 used to highlight notable correlations. It shows multiple moderate to strong correlations, indicating that the attributes are not independent and that city performance across different dimensions is interconnected.

The main positive correlations are as follows:

1. Health Care and Environment with The Arts (0.866).
2. Health Care and Environment with Education (0.490).
3. Transportation with The Arts (0.465).
4. Transportation with Education (0.336).

These relationships suggest that cities with strong health and environmental conditions also tend to perform well in cultural and educational dimensions, and that infrastructure plays a role in supporting broader quality of life outcomes.

The main negative correlations are as follows:

1. Housing with Health Care and Environment (-0.453).
2. Housing with The Arts (-0.449).
3. Crime with Health Care and Environment (-0.305).

These negative relationships indicate trade-offs among certain dimensions of city performance, where strength in one area may be associated with weakness in another for some cities.

Economics and Climate and Terrain show relatively weak correlations with most of the other attributes, which suggests that they capture more independent aspects of city characteristics. Taken together, the combination of positively correlated clusters and meaningful negative relationships provides a strong justification for PCA, since a smaller number of latent components can summarize the variability in the original attributes.

### Carrying Out the PCA

PCA was performed in Minitab on the correlation matrix of the nine attributes. Minitab produced the eigenvalues, the eigenvectors, and the principal component scores for all 329 cities. These outputs were then transferred to Microsoft Excel, where the correlations between the original variables and the principal components (the loadings), the squared loadings, and the cumulative explained variance in each variable were computed. Excel was also used to produce the scree plot, the loading plot, and the score plot.

### Number of Components to Retain

Three criteria were used to decide how many principal components to retain:

1. **Kaiser's rule:** only the first three components have eigenvalues greater than one.
2. **Scree plot:** the scree plot shows a clear elbow after the third component, so components beyond this point add little explanatory power.
3. **Cumulative variance:** the first three components together explain more than sixty percent of the total variance, which is sufficient for analyses of socioeconomic and quality of life data.

On the basis of these criteria, a reduced model retaining the first three principal components was selected. This model balances dimensionality reduction with interpretability.

## Results

### Eigenvalues and Variance Explained

The eigenvalues, the percentage of variance explained, and the cumulative percentage of variance explained for all nine components are as follows:

1. PC1: eigenvalue 3.4083, 37.9 percent of the variance, 37.9 percent cumulative.
2. PC2: eigenvalue 1.2140, 13.5 percent of the variance, 51.4 percent cumulative.
3. PC3: eigenvalue 1.1415, 12.7 percent of the variance, 64.0 percent cumulative.
4. PC4: eigenvalue 0.9209, 10.2 percent of the variance, 74.3 percent cumulative.
5. PC5: eigenvalue 0.7533, 8.4 percent of the variance, 82.6 percent cumulative.
6. PC6: eigenvalue 0.6306, 7.0 percent of the variance, 89.7 percent cumulative.
7. PC7: eigenvalue 0.4930, 5.5 percent of the variance, 95.1 percent cumulative.
8. PC8: eigenvalue 0.3180, 3.5 percent of the variance, 98.7 percent cumulative.
9. PC9: eigenvalue 0.1204, 1.3 percent of the variance, 100.0 percent cumulative.

The three retained components together explain about 64.0 percent of the total variability in the original data. This represents a substantial reduction in dimensionality while preserving most of the information in the original attributes.

### Interpretation of the Retained Components

The interpretation is based on the correlations between the original variables and the principal components, and focuses on variables with absolute loadings of at least 0.5.

**Principal Component 1 (37.9 percent of the variance).** PC1 has strong positive loadings on The Arts (0.855), Health Care and Environment (0.850), Transportation (0.648), Recreation (0.605), and Education (0.508), and strong negative loadings on Housing (-0.658) and Crime (-0.519). The size and consistency of these loadings indicate that PC1 measures overall city performance and quality of life. Cities with high PC1 scores tend to do well in health care, cultural amenities, infrastructure, education, and recreational opportunities. At the same time, they tend to have less crime and better housing conditions. Cities with low PC1 scores tend to do poorly in these areas. PC1 can therefore be treated as a general index of city performance and is well suited to ranking cities.

**Principal Component 2 (13.5 percent of the variance).** PC2 has a positive loading on Education (0.533) and a negative loading on Economics (-0.519), with Recreation (-0.424) also contributing in the negative direction. PC2 therefore captures a trade-off between educational achievement on one side and economic and recreational strength on the other. Cities with high PC2 scores place relatively more weight on education, while cities with low PC2 scores tend to have stronger economies and more recreational opportunities but comparatively weaker educational outcomes.

**Principal Component 3 (12.7 percent of the variance).** PC3 has substantial positive loadings on Climate and Terrain (0.737) and Economics (0.649), which contribute far more to this component than any other attribute. PC3 is therefore a climate and economic advantage dimension. Cities with high PC3 scores tend to have favorable weather and terrain together with stronger economies, while cities with low PC3 scores lack these advantages. This component captures an aspect of urban performance that is separate from the general quality of life dimension represented by PC1.

The squared loadings support these interpretations. PC1 explains 72.2 percent of the variance in Health Care and Environment and 73.1 percent of the variance in The Arts, while PC3 explains 54.3 percent of the variance in Climate and Terrain and 42.1 percent of the variance in Economics.

### Loading Plot and Score Plot

A loading plot of the attributes on PC1 and PC2 confirms the numerical interpretation. Education, The Arts, Transportation, and Health Care and Environment are grouped closely on the positive side of the PC1 axis, while Housing and Crime lie on the negative side. Along the PC2 axis, Education lies on the positive side, while Economics and Recreation lie on the negative side, which visually confirms the trade-off captured by PC2.

A score plot of the cities on PC1 and PC2 shows wide horizontal dispersion, indicating substantial differences in overall performance rather than a single common profile. Cities such as San Diego, CA; Detroit, MI; Denver, CO; and Boston, MA lie on the far right side of the plot, indicating strong overall performance across the combined quality of life and socioeconomic characteristics measured by PC1. Cities such as Dallas, TX; New York, NY; and Newark, NJ lie on the left side of the plot, indicating weaker overall performance on this composite measure.

Vertical separation shows that cities with similar overall performance can have quite different strengths in education, economics, and recreation. Cities such as Chicago, IL and Denver, CO, which lie higher on the PC2 axis, are more closely aligned with a focus on education, while Miami-Hialeah, FL and San Diego, CA, which lie lower on the PC2 axis, are more closely aligned with economic and recreational traits. Philadelphia, PA; Atlanta, GA; and Baltimore, MD lie near the center of the plot. San Diego, CA stands out with a very high PC1 score and a strongly negative PC2 score, and Chicago, IL has a high PC2 score relative to most other cities.

### Ranking of Cities

Cities were ranked by their PC1 scores. PC1 was chosen as the ranking criterion because it explains the largest share of the total variance (37.9 percent) and has favorable loadings on key quality of life attributes, namely Health Care and Environment, Education, Transportation, Recreation, and The Arts.

## Key Findings

1. Large, economically diverse cities occupy the top of the PC1 ranking. The cities with the highest PC1 scores are New York, NY; San Francisco, CA; Los Angeles, Long Beach, CA; Chicago, IL; Boston, MA; Washington, DC-MD-VA; and Philadelphia, PA-NJ. These cities perform well across many interconnected dimensions and have high composite scores because of strong infrastructure, access to education and health care, cultural facilities, and job opportunities.
2. New York, NY has the highest PC1 score and is an extreme positive case, since it excels in many areas at once rather than in a single area.
3. San Francisco and Boston also score highly because of strong schools, innovation driven economies, and good quality of life indices, even though they may face problems such as housing affordability.
4. Cities in the middle of the PC1 distribution tend to have balanced but less pronounced strengths.
5. Cities with negative PC1 scores, at the bottom of the ranking, show poorer overall circumstances. These are usually smaller metropolitan areas or regions with fundamental problems in areas such as access to health care, economic diversification, or public infrastructure.
6. Ordering cities by the first principal component reveals clear and meaningful differences in overall city performance. The results demonstrate that PCA is effective in reducing dimensionality, uncovering latent structure, and supporting data driven comparisons among metropolitan areas.

## Limitations

The PC1 based ranking should not be treated as a final judgement about livability or about how well a policy works. It is a relative, multivariate comparison that reflects the cumulative effect of correlated variables rather than separate performance measurements for each attribute.

## Repository Contents

1. **PCA_Project_2025_TEMPLATE.xlsx:** the Excel workbook containing the data and the analysis. It has seven worksheets:
    1. CITY_DATA: the raw scores of the 329 cities on the nine attributes, with Place ID and Place Name, together with notes describing what each attribute measures.
    2. MINITAB OUTPUT: the eigenvalues and eigenvectors produced by Minitab.
    3. MINITAB OUTPUT Scores: the scores of every city on all nine principal components.
    4. Loading Analysis: the eigenvalues, the percentage and cumulative percentage of variance explained, the eigenvectors, the correlations between the original variables and the principal components, the squared loadings, and the cumulative explained variance in each variable.
    5. SCREE PLOT: the eigenvalues and the scree plot used in the component retention decision.
    6. LOADING PLOT: the loadings of each attribute on PC1 and PC2 and the corresponding loading plot.
    7. SCORE PLOT: the PC1 and PC2 scores of the cities and the corresponding score plot.
2. **PRIDE_MUDONDO_PCA_PROJECT_WRITEUP.pdf:** the written report, covering the introduction, the data description and correlation structure, the PCA and reduced model, the interpretation of the retained components, the loading plot, the score plot, and the city ranking and conclusions.
3. **README.md:** this file.
4. **.gitignore:** a list of temporary and system files, such as Excel lock files, that are excluded from version control.

## Tools Used

1. **Minitab:** used to carry out the Principal Component Analysis.
2. **Microsoft Excel:** used for additional computations, visualizations, and organizing the results.

## Author

Pride Mudondo
