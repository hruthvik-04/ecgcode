#AI Based ECG Analysis

#About the Project
AI-Based ECG Analysis is a cutting-edge solution designed to automate and enhance the accuracy of electrocardiogram (ECG) interpretation using machine learning and deep learning. Cardiovascular diseases (CVDs) are a leading global cause of death, and early detection of heart abnormalities can save lives.
The system processes raw ECG signals, detects anomalies (e.g., arrhythmias, myocardial infarction), and generates actionable reports for healthcare providers—bridging the gap between cardiology expertise and underserved populations.
Key Features
1. ECG Signal Processing
•	Noise removal using Butterworth & Wavelet filters.
•	R-peak, QRS complex, and ST-segment detection (Pan-Tompkins algorithm).
•	Computes Heart Rate, QT/PR intervals.
2. AI-Powered Classification
•	Deep Learning Model: trained CNN to classify ECGs into:
o	Normal
o	Arrhythmia (Atrial Fibrillation, Ventricular Tachycardia, )
•	Trained on MIT-BIH and PTB-XL datasets.
3. Risk Assessment
•	Integrates Framingham Risk Score (10-year heart attack risk).
•	Computes GRACE Score (mortality risk post-heart attack).
•	Combines ECG findings with patient data (age, BP, cholesterol).
4. Visualization & Reporting
•	Interactive ECG waveform plots with anomaly highlights.
•	Automated PDF report generation for doctors/patients.
5. Web-Based Dashboard
•	Real-time ECG analysis via Flask.
•	Secure patient data storage (MySQL).

#Installation
Setting Up MySQL Community Server
Step 1: Download MySQL Community Server
1.	Visit the MySQL Community Downloads Page:
o	MySQL Community Downloads
2.	Download MySQL Community Server:
o	Download MySQL Community Server using MSI installer according to your operating system.
o	If prompted, you can skip the login/signup by clicking on "No thanks, just start my download".
Step 2: Install MySQL Community Server
1.	Run the Installer:
o	Once the download is complete, run the installer file.
2.	Choose Setup Type:
o	In the MySQL Installer window, select the Developer Default setup type.
o	Click Next and proceed with the complete installation. The installer will download and install the selected MySQL products.
Step 3: Configuration
1.	Server Configuration:
o	After the installation, the MySQL Installer will prompt you to configure the server.
o	Select Standalone MySQL Server. Click Next.
o	Choose the default port (3306) and ensure that it is open and available. Click Next.
Step 4: Authentication Method
1.	Set Authentication:
o	Use the default authentication method (recommended). Click Next.
o	Set the root password for your MySQL server. Remember this password as you will need it to connect.
o	Optionally, add additional MySQL user accounts. Click Next.
Step 5: Apply Configuration
1.	Apply Settings:
o	Review the configuration settings and click Execute to apply them.
o	Once the configuration is complete, click Finish.
Setting Up MySQL Workbench
Step 1: Download Workbench
1.	Visit the MySQL Workbench Download Page:
o	MySQL Workbench Downloads
2.	Download MySQL Workbench:
o	Download MySQL Workbench using MSI installer according to your operating system.
o	Click the Download button and follow the prompts to download the installer.
o	If prompted, you can skip the login/signup by clicking on "No thanks, just start my download".
Step 2: Install MySQL Workbench
1.	Run the Installer:
o	Run the downloaded installer.
o	Follow the installation prompts to complete the installation.
Step 3: Connect to MySQL Server using MySQL Workbench
1.	Launch MySQL Workbench:
o	Create a New Connection by clicking on the + button next to MySQL Connections.
Step 4: In the Setup New Connection Dialog
1.	Connection Settings:
o	Connection Name: Enter a name for the connection (in this case "localhost").
o	Connection Method: Standard (TCP/IP).
o	Port: 3306 (or the port you configured during installation).
o	Username: root.
o	Click OK.
Step 5: Launching the Connection
1.	Connect to Server:
o	Click on the new connection, enter the root password of your MySQL Server, and click OK.
o	If there is any Connection Warning, just click Continue Anyway.
o	Ensure MySQL server status is Running by navigating to Services app on your system.


Creating Database and Tables
Step 1: Create a New SQL Tab for Executing Queries
1.	Open SQL Tab:
o	Click on File > New Query Tab.
Step 2: Create the Schema
1.	Enter and Execute Query:
o	Enter the following query to create the database:
CREATE DATABASE hospital_ecg_db;
o	Press Ctrl+Enter to execute it.
Step 3: Select the New Schema
1.	Select Schema:
o	Double click on the new schema " hospital_ecg_db " which is visible on the Navigator section (left-hand side).
Step 4: Create Staff Table
1.	Enter and Execute Query:
                o	Enter the following query to create the staff table:
                CREATE TABLE `staff` (
                  		    `Staff_ID` varchar(80) NOT NULL,
                 		    `Password` varchar(80) NOT NULL,
                 		    `StaffName` varchar(80) DEFAULT NULL,
                  		    PRIMARY KEY (`Staff_ID`)
                 ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
o	Insert values into the created table:
INSERT INTO `staff` VALUES ('1AH21CS043','$2b$12$pVtihF8xr8znJqCByaSOVuJ.m7fw..iiEzD2GnbUTDvPvBW2ZUmfK','Hruthvik');

Step 5: Create Doctor Table
1.	Enter and Execute Query:
                    o	Enter the following query to create the doctor table:
                    CREATE TABLE `doctor` (
                      		    `Doctor_ID` varchar(255) NOT NULL,
                     		    `Username` varchar(255) NOT NULL,
                      		    `Password` varchar(255) NOT NULL,
                     		     PRIMARY KEY (`Doctor_ID`),
                      		    UNIQUE KEY `Username` (`Username`)
                    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci; 
o	Insert values to the created table 
INSERT INTO `doctor` VALUES 
('DR-001-2024','hruthvi','$2b$12$EixZaYVK1fsbw1ZfbX3OXePaWxn96p36WQoeG6Lruj3vjPGgaYlJW'),('DR-002-2024','HRUTHVIK','$2b$12$Ei7rVxrjAW32IJujwDtPQuUs21e26iIcQqhNHqx46UlTNOG5E2ffW'),('DR-004-2024','hruthv','1234556789'),('DR-009-2024','Hruthik','$2b$12$9YzlKL6HEYwXJ0QMX3zP7.HYc3iEa938jzUqvyf/v3FfMSQu8fnxm'),('DR-012-2024','dr_john','$2b$12$ovLiN8.a9Na.a.NtVyDr5OVvMAnWMJjOQvL6igH6H5vKxIT6cxcgC');

Step 6: Create patient_profile Table
1.	Enter and Execute Query:
                    o	Enter the following query to create the patient_profile table:
                    CREATE TABLE `patient_profile` (
                     		   `Patient_ID` varchar(20) NOT NULL,
                      		   `Patient_Name` varchar(45) NOT NULL,
                     		   `Age` int NOT NULL,
                      		   `Gender` varchar(45) NOT NULL,
                      		   `Address` varchar(60) NOT NULL,
                      		   `Email_ID` varchar(45) NOT NULL,
                      		   `Personal_Contact` bigint NOT NULL,
                      		   `Emergency_Contact` bigint NOT NULL,
                      		   `Doctor_ID` varchar(255) DEFAULT NULL,
                      		   `Created_At` datetime NOT NULL,
                      		   `Staff_Username` varchar(80) NOT NULL,
                      		   PRIMARY KEY (`Patient_ID`),
                     		   UNIQUE KEY `Patient_ID_UNIQUE` (`Patient_ID`),
                      		   KEY `fk_patient_doctor` (`Doctor_ID`),
                      CONSTRAINT `fk_patient_doctor` FOREIGN KEY (`Doctor_ID`) REFERENCES `doctor` (`Doctor_ID`)
                    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;


Step 7: Create input Table
1.	Enter and Execute Query:
o	Enter the following query to create the input table:
                    CREATE TABLE `input` (
                      		  `Record_ID` int NOT NULL AUTO_INCREMENT,
                      		  `Patient_ID` varchar(20) DEFAULT NULL,
                      		  `Smoker` tinyint NOT NULL,
                      		  `Diabetic` tinyint NOT NULL,
                      		  `Cholesterol` float NOT NULL,
                      		  `HDL` int NOT NULL,
                      		  `Blood_Pressure` float NOT NULL,
                      		  `Other_Issues` varchar(200) NOT NULL DEFAULT '',
                      		  `Generated_AT` varchar(45) NOT NULL DEFAULT 'Timestamp(Now)',
                     		 `Doctor_ID` varchar(20) DEFAULT NULL,
                     		 PRIMARY KEY (`Record_ID`),
                     		 UNIQUE KEY `Record_ID_UNIQUE` (`Record_ID`),
                     		 KEY `_idx` (`Patient_ID`)
                    ) ENGINE=InnoDB AUTO_INCREMENT=690 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
Step 8: Create ecg_reports Table
1.	Enter and Execute Query:
                            CREATE TABLE `ecg_reports` (
                              `report_id` varchar(50) NOT NULL,
                              `patient_id` varchar(20) NOT NULL,
                              `doctor_id` varchar(20) DEFAULT NULL,
                              `report_date` datetime NOT NULL,
                              `record_num` varchar(20) DEFAULT NULL,
                              `predicted_class` varchar(50) NOT NULL,
                              `confidence` float NOT NULL DEFAULT '0',
                              `heart_rate` float NOT NULL DEFAULT '0',
                              `qt_interval` float NOT NULL DEFAULT '0',
                              `pr_interval` float NOT NULL DEFAULT '0',
                              `framingham_risk` float NOT NULL DEFAULT '0',
                              `grace_score` float NOT NULL DEFAULT '0',
                              `systolic_bp` float NOT NULL DEFAULT '0',
                              `cholesterol` float NOT NULL DEFAULT '0',
                              `hdl` float NOT NULL DEFAULT '0',
                              `smoker` tinyint(1) NOT NULL DEFAULT '0',
                              `diabetes` tinyint(1) NOT NULL DEFAULT '0',
                              `all_beats_count` int NOT NULL DEFAULT '0',
                              `class_probabilities` json DEFAULT NULL,
                              `ecg_image_path` varchar(255) DEFAULT NULL,
                              `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
                              `updated_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
                              PRIMARY KEY (`report_id`),
                              KEY `idx_patient` (`patient_id`),
                              KEY `idx_doctor` (`doctor_id`),
                              KEY `idx_report_date` (`report_date`),
                              CONSTRAINT `ecg_reports_ibfk_1` FOREIGN KEY (`patient_id`) REFERENCES `patient_profile` (`Patient_ID`),
                              CONSTRAINT `ecg_reports_ibfk_2` FOREIGN KEY (`doctor_id`) REFERENCES `doctor` (`Doctor_ID`)
                            ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
