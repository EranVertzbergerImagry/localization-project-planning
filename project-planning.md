# Localization Algorithm Development Project Plan

## General Description

This project focuses on developing an improved localization algorithm. The goal is to enhance the current localization system which relies on IMU and odometry measurements but suffers from drift issues. By integrating and optimizing multiple sensor inputs, including visual odometry, and establishing RTK measurements as ground truth, we aim to achieve a more accurate and reliable localization system.

The project will involve extracting the existing localization module from the vehicle control system into a standalone repository with a clean API, enhancing the IMU & odometry-based localization to reduce drift significantly, and solving scale issues in the visual odometry algorithm. Additionally, the project includes configuring the RTK system properly for ground truth measurements and collecting comprehensive data for analysis and validation.

## Objectives

### Objective A: Comprehensive Data Collection & Verification System
- **Description:** Establish a comprehensive data collection system with verified ground truth and algorithms to assess performance
- **Success Metrics:**
  - Successfully configured RTK system with verified coordinate system alignment
  - Collected at least 10 hours of driving data with accurate ground truth
  - Implemented automated data quality verification process
  - Compiled relevant public datasets for additional testing

### Objective B: Standalone Localization Repository with API
- **Description:** Create IMU & odometry-based localization in a new repository with an API to the central algorithm (AI-driver)
- **Success Metrics:**
  - Completed extraction of localization module from vehicle control
  - Implemented clean API for the AI-driver to access localization data
  - Successfully transitioned vehicle control to use the new localization API
  - Comprehensive documentation and testing of the new repository

### Objective C: Enhanced IMU & Odometry Localization
- **Description:** Reduce IMU & odometry-based localization drift to achieve submeter accuracy for up to 1 minute
- **Success Metrics:**
  - Localization error less than 1 meter after 1 minute of operation
  - Reduced gyro bias effects through improved algorithms
  - Comprehensive testing across various driving conditions
  - Statistical validation of performance improvements

### Objective D: Visual Odometry Scale Correction
- **Description:** Solve the scale problem in the Visual Odometry algorithm
- **Success Metrics:**
  - Identified and implemented solution for scale correction
  - Visual odometry output matches ground truth measurements within 5% scale error
  - Successful online operation of visual odometry module
  - Integration with main localization system

## Task Planning

### Tasks for Objective A: Comprehensive Data Collection & Verification System

#### Current State and Challenges
- RTK system installed but not properly configured
- Coordinate system convention (ENU<->NED) compliance not verified
- Lever arm not measured
- Data saving with OS clock and GPS clock not verified
- Insufficient data collected for analysis
- Need to search for online public datasets for vehicles incorporating IMU, cameras, car speed, and ground truth
- Implementation of localization performance calculations exists but lacks direction of driving metric calculation

#### Task Breakdown

##### RTK System Configuration
- **Task A1:** Verify RTK system coordinate convention (ENU/NED) compliance (2 days)
- **Task A2:** Measure and document lever arm offsets (1 day)
- **Task A3:** Configure data synchronization between OS clock and GPS clock (2 days)
- **Task A4:** Create configuration documentation for RTK setup (1 day)

##### Data Collection
- **Task A5:** Design comprehensive data collection test scenarios (2 days)
- **Task A6:** Develop data collection protocol with quality checks (1 day)
- **Task A7:** Execute data collection for urban scenarios (3 days)
- **Task A8:** Execute data collection for highway scenarios (2 days)
- **Task A9:** Process and organize collected data (2 days)

##### Reference Datasets
- **Task A10:** Research and identify public autonomous vehicle datasets (3 days)
- **Task A11:** Evaluate dataset compatibility with our requirements (2 days)
- **Task A12:** Develop tools for converting external datasets to our format (3 days)
- **Task A13:** Create documentation for using external datasets (1 day)

##### Performance Metrics
- **Task A14:** Implement direction of driving metric calculation (2 days)
- **Task A15:** Enhance existing performance evaluation system (2 days)
- **Task A16:** Create automated data quality validation tools (3 days)
- **Task A17:** Create test scenarios for localization performance assessment (2 days)

### Tasks for Objective B: Standalone Localization Repository with API

#### Current State and Challenges
- Localization module currently nested in vehicle control module
- Not isolated as a standalone component with clean API
- Need to establish connections with AI-driver and visual odometry module

#### Task Breakdown
[Tasks to be detailed]

### Tasks for Objective C: Enhanced IMU & Odometry Localization

#### Current State and Challenges
- Experiences drift due to gyro bias
- Calculates orientation using AHRS module which fuses gyroscopes and accelerometers
- Heading is fused with speed and steering measurements using kinematic model equations

#### Task Breakdown

##### Motion State Detection
- **Task C1:** Research static/dynamic detection algorithms for IMU data (2 days)
- **Task C2:** Implement static/dynamic state detection algorithm (3 days)
- **Task C3:** Test and tune static/dynamic detection on collected datasets (2 days)

##### Bias Estimation and Compensation
- **Task C4:** Design gyro bias estimation algorithm based on static periods (3 days)
- **Task C5:** Implement bias estimation and compensation in AHRS module (3 days)
- **Task C6:** Validate bias estimation accuracy with ground truth data (2 days)

##### Visual Odometry Integration
- **Task C7:** Extend API to accept VO pose updates (2 days)
- **Task C8:** Implement VO pose processing and transformation (3 days)
- **Task C9:** Develop VO heading update mechanism (2 days)
- **Task C10:** Implement heading bias estimation using VO data (3 days)

##### Testing and Validation
- **Task C11:** Run enhanced localization on test datasets (3 days)
- **Task C12:** Compare performance with original localization algorithm (2 days)
- **Task C13:** Analyze and quantify drift reduction improvements (2 days)

##### Documentation
- **Task C14:** Document algorithm enhancements and implementation details (2 days)

### Tasks for Objective D: Visual Odometry Scale Correction

#### Current State and Challenges
- Scale problem likely due to lack of loop closure in the scenario
- Issues when running online (pose appears incorrect)
- Direction of driving seems correct when operating offline, but not fully tested
- Deployed in CPP project

#### Task Breakdown
[Tasks to be detailed]