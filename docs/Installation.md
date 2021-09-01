# Configuration

- [Installation](#installation)
    - [Configure PLC project](#configure-plc-project)
    - [Configuration Device Energy 1 & 2](#configuration-device-energy-1-and-energy-2)
    - [Configuration Central Device](#configuration-central-device)
        - [IE MQTT Connector](#mqtt-connector)
        - [Configure IE-Flow Creator](#ie-flow-creator)
        - [Data Service Custom Adapter](#dataservice-custom-adapter)
        - [Performance Insight](#performance-insight-dashboard)
   
## Configure PLC project

1) Open TIA portal and open the project containing the filling application
2) Download the PLC program to the PLC and set the PLC into RUN
3) Open the HMI to control the filling application   
   
## Configuration Device Energy 1 and Energy 2 

To read data from the PLC and provide the data, we will use S7 Connector to establish connection with the PLC via OPC UA.
The S7 Connector sends the data to the Databus, where the Data Service app can collect what is needed for the notification rules.
In order to build this infrastructure, these apps must be configured properly:

- IE Databus
- S7 Connector
- Cloud Connector

**IE Databus**

- Launch the IE Databus Configurator and add your related credentials/topics:
`"ie/#"`

![ie_databus_user](graphics/IE_Databus_User.png)

![ie_databus](graphics/IE_Databus.png)

**S7 Connector**

![Create PLC Connection](graphics/add_data_source.png)

- Launch the S7 Connector and configure the PLC connection 
- Start and Deploy your S7 Connector configuration

**Cloud Connector Local Lake**

- Configure starting from the left side "Bus Adaptor" to the right the "Cloud Connector Clients"
- To deploy the configuration, initially click on your route and connect your topics from the bus adaptor with your cloud topics 
- Then click on deploy. 
- Note: You must create one topic for the data and one topic for the metadata. 

1:
ie/d/j/simatic/v1/s7c1/dp/r/EnergyMeter/default
ie/m/j/simatic/v1/s7c1/dp/r/EnergyMeter/
Add a topic in the Bus Adaptor 

![cc_step_1](graphics/cc_step_1.png)

2:
Close the option and prove under "Edit configuration" the following settings: 

![cc_step_2](graphics/cc_step_1.png)


3: 
Bus Adaptor Configuration

![cc_step_3](graphics/cc_step_3.png)

- Same procedure for the metadata topic

4:
Create for the data a Route

![cc_route_step1](graphics/cc_route_step1.png)

5:
Create for the metadata a Route

![cc_route_step2](graphics/cc_route_step2.png)

Add a Cloud Connector Clients by using Local lake as Type
 
6: 
Client Connection Local Lake

![cc_add_cloud_step_1](graphics/cc_add_cloud_step_1.png)

- For receiving data on our central edge device we use the MQTT Connector, which is accessible via port 9883

7: 
Add external databus from Central Device

![cc_add_cloud_step_2](graphics/cc_add_cloud_step_2.png)

Adjust the Publish Topic

8: Create Publish Topic

![cc_add_cloud_step_3_adv](graphics/cc_add_cloud_step_3_adv.png)

- Same steps for the metadata topic

9:
Overview of the Cloud Connector configuration

![cc_general_overview_1](graphics/cc_general_overview_1.png)

## Configuration Central Device 

The following applications must be installed and configured on the central edge device

- IE Databus
- IE MQTT Connector
- IE Flow Creator
- Data Service
- Performance Insight

**Configure Databus**

Add your user credentials and publish topic


![IE_Databus](graphics/IE_Databus.png)

**Configure IE MQTT Connector**

In the Databus Configurator switch to "IE MQTT" Connector and enable the external databus by clicking unsecure

![databus_external_step_2](graphics/databus_external_step_2.png)

**IE Flow Creator**

Purpose of the Flow: The incoming data from the two Edge devices must be converted into the appropriate format so that the data service is able to process the data. 

Open the IE Flow Creator App from the IED Web UI and import the [convertdata.json](src/convertdata.json)

![ie_flow_step_1](graphics/ie_flow_step_1.png)


**Data Service**

- We get data from 2 different devices. In the data service we create a custom adapter for each device. 
- Important here is to create the appropriate metadata topic.
- The connection status changes automatically to green if its correctly configured. 

Create your custom Adapter for Edge Device Energy 1

![data_service_Step1](graphics/data_service_Step1.png)

Create your custom Adapter for Edge Device Energy 2

![data_service_Step2](graphics/data_service_step_2.png)

Save the connection and return to the main page

![data_service_Step3](graphics/data_service_step_3.png)

Check the datatransfer with preview data

![data_service_Step4](graphics/data_service_step4.png)


**Performance Insight**

The same Asset structure is visible in Performance Insight
Finish the example by creating your Dashboard

![performance_insight_step1](graphics/performance_insight_step1.png)



