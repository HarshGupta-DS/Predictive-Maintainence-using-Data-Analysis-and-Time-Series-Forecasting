# Predictive-Maintainence-using-Data Analysis-&-Time-Series-Forecasting

<img src="https://docs.microsoft.com/en-us/azure/architecture/industries/manufacturing/images/predictive-maintenance-solution/model.png" width="1000"/>

## Introduction
Unscheduled equipment downtime can be detrimental for any business. It is critical to keep field equipment running to maximise utilisation and minimise costly, unscheduled downtime and health, safety and environmental risks. The goal of a predictive maintenance strategy is to extend the useful service life of equipment and prevent failures. Anomaly detection is a common approach, because it identifies when a device is behaving differently than expected. Anomaly detection solutions are often more accurate than simple rule-based failure-detection methods and they are useful in the prevention of expensive failures and outages.

Predictive maintenance aims to predict whether a machine will fail and needs to be repaired given data produced by various sensors placed in the machine while it is running. There are multiple commonly used sensors, such as temperature, voltage, and pressure sensor. The readings produced by these sensors are then sent to a database and then used in further analysis to determine several important requirements to guarantee the machine's performance, such as Mean Time Before Failure (MTBF) and Mean Time To Repair (MTTR). In terms of time-series forecasting, one possible approach is to predict the value of a certain sensor several hours in advance. The predicted values can then be compared with a predetermined threshold based on domain knowledge or be fed into another machine learning algorithm to determine the probability of the machine breaking down. Predictive Maintenance avoids the drawbacks of Preventive Maintenance (under utilization of a part's life) and Reactive Maintenance (unscheduled downtime). Based on the health of an equipment in the past, future point of failure can be predicted in Predictive Maintenance. Thus, replacement of parts can be scheduled just before the actual failure.

## Dataset
The Use-Case is obtained from Microsoft Azure Sensor Data <a href="https://azure.microsoft.com/en-in/use-cases/predictive-maintenance/" target="_blank">Use-Case Predictive Maintenance</a>, Whereas the data set is obtained from <a href="https://www.kaggle.com/datasets/arnabbiswas1/microsoft-azure-predictive-maintenance" target="_blank">Kaggle</a> which contains five .csv files describing different events (error, failure, and maintenance) and the sensor data for each machine.

## Approach
In this repository, a simple deep learning model based on LSTM will be used to predict the value of the chosen feature (e.g. readings from pressure sensor). Further, a failure event from the record will be chosen to check whether the model can correctly predict the chosen sensor readings in the event of failure.

## Context
This an example data source which can be used for Predictive Maintenance Model Building. It consists of the following data:

Machine conditions and usage: The operating conditions of a machine e.g. data collected from sensors.
Failure history: The failure history of a machine or component within the machine.
Maintenance history: The repair history of a machine, e.g. error codes, previous maintenance activities or component replacements.
Machine features: The features of a machine, e.g. engine size, make and model, location.

## Details
Telemetry Time Series Data (PdM_telemetry.csv): It consists of hourly average of voltage, rotation, pressure, vibration collected from 100 machines for the year 2015.

Error (PdM_errors.csv): These are errors encountered by the machines while in operating condition. Since, these errors don't shut down the machines, these are not considered as failures. The error date and times are rounded to the closest hour since the telemetry data is collected at an hourly rate.

Maintenance (PdM_maint.csv): If a component of a machine is replaced, that is captured as a record in this table. Components are replaced under two situations: 1. During the regular scheduled visit, the technician replaced it (Proactive Maintenance) 2. A component breaks down and then the technician does an unscheduled maintenance to replace the component (Reactive Maintenance). This is considered as a failure and corresponding data is captured under Failures. Maintenance data has both 2014 and 2015 records. This data is rounded to the closest hour since the telemetry data is collected at an hourly rate.

Failures (PdM_failures.csv): Each record represents replacement of a component due to failure. This data is a subset of Maintenance data. This data is rounded to the closest hour since the telemetry data is collected at an hourly rate.

Metadata of Machines (PdM_Machines.csv): Model type & age of the Machines.
