Pastoralist Conflict Prevention System — Turkana County
Overview

The Pastoralist Conflict Prevention System is a machine learning–based early warning platform designed to detect environmental conditions that may contribute to resource-driven conflicts among pastoralist communities in Turkana County, Kenya. In arid and semi-arid regions such as Turkana, pastoralist livelihoods depend heavily on access to water and grazing land. During periods of drought or environmental stress, competition over these scarce resources often intensifies, increasing the likelihood of inter-community conflict.

This project addresses that challenge by integrating satellite remote sensing data, machine learning techniques, and geospatial visualization tools to detect environmental scarcity hotspots. By analysing long-term patterns in rainfall and vegetation conditions, the system identifies areas where environmental stress may increase the risk of conflict. The results are presented through an interactive dashboard that allows users to visualize high-risk areas spatially. The system is intended to support decision-makers, humanitarian organizations, and peacebuilding institutions by providing early warnings that enable proactive interventions before resource competition escalates into violence.

Project Objectives

The primary objective of this project is to develop a data-driven system capable of monitoring environmental conditions that influence pastoralist livelihoods in Turkana County. Specifically, the system seeks to identify environmental scarcity hotspots by analysing satellite-derived rainfall and vegetation datasets. Through the use of machine learning techniques, the project aims to detect patterns associated with resource stress and translate them into actionable insights. Another important objective is to provide a visual interface that allows non-technical stakeholders to interpret the model outputs easily. Ultimately, the system contributes to conflict prevention efforts by enabling early identification of areas where resource scarcity could increase the likelihood of pastoralist conflict.

System Architecture

The system follows a structured pipeline that moves from environmental data collection to predictive modelling and finally to visualization through a dashboard interface. The first stage involves collecting and preparing satellite-derived environmental data that describe rainfall patterns and vegetation conditions across Turkana County. The second stage involves training a machine learning model using these datasets in order to identify patterns associated with environmental scarcity. The final stage translates the model predictions into a visual interface using an interactive dashboard. This architecture ensures that raw environmental observations can be transformed into interpretable insights that support real-world decision making.

Data Collection

Environmental data used in this project were obtained from satellite remote sensing sources and processed to create a structured dataset suitable for machine learning analysis. The study area was first divided into a spatial monitoring framework using a five-kilometre grid covering the entire Turkana County boundary. Each grid cell represents a monitoring location, and the centroid of each cell was used as a point where environmental variables could be extracted. This spatial framework produced 2,519 monitoring points distributed across the county.

Rainfall data were obtained from the Climate Hazards Group InfraRed Precipitation with Station data (CHIRPS) daily dataset. The daily rainfall records were aggregated into sixteen-day cumulative rainfall composites to align with the temporal resolution of vegetation data. The aggregation process covered the period from 2015 to 2025 and produced 252 rainfall raster files stored in GeoTIFF format.

Vegetation conditions were measured using the MODIS Normalized Difference Vegetation Index (NDVI) dataset, specifically the MOD13Q1 product with a spatial resolution of 250 meters. NDVI values were extracted for each of the 2,519 monitoring points over the ten-year study period. Because the MODIS dataset stores NDVI values as scaled integers, a scaling factor of 0.0001 was applied to convert them into their standard decimal format. The extracted values were exported as a structured CSV dataset, which formed the vegetation component of the machine learning training data.

All datasets generated during the data collection process were stored in a centralized directory to ensure consistent access during model development and analysis.

Machine Learning Model

The system uses a Random Forest Classifier to identify environmental scarcity hotspots. Random Forest is an ensemble learning method that constructs multiple decision trees and combines their predictions to produce a final classification. This algorithm was selected because it performs well with environmental datasets that contain nonlinear relationships and complex interactions between variables.

The model was trained using four environmental features derived from the rainfall and vegetation datasets. These features include the mean NDVI, NDVI standard deviation, mean rainfall, and rainfall standard deviation. Together, these variables capture both the overall environmental conditions and the variability of those conditions across time. Mean values represent long-term resource availability, while standard deviation measures indicate environmental instability that may stress pastoralist livelihoods.

A key challenge during model training was the presence of class imbalance. Scarcity hotspots represent only a small fraction of the dataset, accounting for approximately five percent of all observations. To address this imbalance, the Synthetic Minority Over-sampling Technique (SMOTE) was applied to generate additional training examples for the minority class. In addition, balanced class weights were used during model training to ensure that the model assigns greater importance to correctly identifying scarcity hotspots.

The trained model achieved strong performance, with an overall accuracy of 93 percent. The recall score for hotspot detection reached 76 percent, indicating that the system successfully identifies more than three-quarters of genuine scarcity events. While the precision score of 44 percent indicates the presence of some false positives, this level of sensitivity is acceptable for early warning systems where the cost of missing a true hotspot is higher than the cost of investigating a false alert.

Dashboard Visualization

To make the model predictions accessible to users, an interactive dashboard was developed using the Streamlit framework. The dashboard was implemented and deployed through Visual Studio Code, allowing the application to run as a local web-based interface. Streamlit enables rapid development of data applications directly in Python and provides built-in support for interactive components and map visualizations.

The dashboard presents a geospatial heatmap that highlights areas within Turkana County where the model predicts environmental scarcity hotspots. Each grid cell on the map corresponds to a five-kilometre monitoring location used during the modelling process. Users can interact with the dashboard through controls that allow them to adjust the alert probability threshold. By modifying this threshold, users can choose between displaying only the most critical hotspots or expanding the map to include moderate-risk areas. This flexibility allows the dashboard to adapt to different operational contexts depending on the available response capacity.

Through this visualization interface, the system translates machine learning outputs into an intuitive early warning map that supports rapid situational awareness and informed decision making.

Technologies Used

The development of the system relied on several technologies commonly used in geospatial data science and machine learning. Python served as the primary programming language for data processing and model development. Google Earth Engine was used for satellite data access and geospatial processing. Machine learning operations were implemented using the scikit-learn library, while the imbalanced-learn library was used to apply SMOTE for handling class imbalance. The interactive dashboard was developed using the Streamlit framework and deployed through the Visual Studio Code development environment.
