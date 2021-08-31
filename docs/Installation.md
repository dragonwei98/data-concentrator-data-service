# Installation

- [Installation](#installation)
    - [Configuration Device Energy1&2](#configure-device1-device2)
        - [Configure Databus](#configure-databus)
        - [Configure S7 Connector](#configure-s7connector)
        - [Configure IE Cloud Connector Local Lake](#configure-cloud-connector)
    - [Configuration Central Device](#configure-central-device)
        - [IE MQTT Connector](#mqtt-connector)
        - [Configure IE-Flow Creator](#ie-flow-creator)
        - [Data Service Custom Adapter](#dataservice-custom-adapter)
        - [Performance Insight](#performance-insight-dashboard)
   
## Configuration Device Energy 1 and Energy 2 

- Configuration of the 2 edge devices for data transfer to the central edge device

### Configure Databus

- Launch the IE Databus Configurator and add your related credentials/topics:
`"ie/#"`
![ie_databus_user](docs/graphics/IE_Databus_User.png)
![ie_databus](docs/graphics/IE_Databus.png)

### Configure S7 Connector

![Create PLC Connection](docs/graphics/add_data_source.png)

- Launch the S7 Connector and configure the PLC connection 
- Start and Deploy your S7 Connector configuration

### Configure Cloud Connector Local Lake 

- Configure starting from the left side "Bus Adaptor" to the right the "Cloud Connector Clients"
- To deploy the configuration, initially click on your route and connect your topics from the bus adaptor with your cloud topics 
- Then click on deploy. 
- Note: You must create one topic for the data and one topic for the metadata. 

Add a topic in the Bus Adaptor(docs/graphics/cc_step_1.png)


Switch to the Standard tab and put your Configuration from the databus(docs/graphics/cc_step_2.png)


Close the option and prove under "Edit configuration" the following settings(docs/graphics/cc_step_3.png)

- Same steps for the metadata topic

Create for the data a Route(docs/graphics/cc_route_step1.png)

Create for the metadata a Route(docs/graphics/cc_route_step2.png)

 Add a Cloud Connector Clients by using Local lake as Type(docs/graphics/cc_add_cloud_step_1.png)

- For receiving data on our central edge device we use the MQTT Connector, which is accessible via port 9883

Add the external databus(docs/graphics/cc_add_cloud_step_2.png)

Adjust the Publish Topic(docs/graphics/cc_add_cloud_step_3.png)

- Same steps for the metadata topic

Overview of the Cloud Connector configuration(docs/graphics/cc_general_overview_1.png)

## Configuration Central Device 


### Configure Databus



### Configure IE MQTT Connector



### Import and Configure IE Flow Creator



### Setup Data Service



### Setup Performance Insight 



