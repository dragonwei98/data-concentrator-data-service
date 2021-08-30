# Installation

- [Installation](#installation)
    - [Configuration Device Energy 1 & 2]
        - [Configure Databus](#configure-databus)
        - [Configure S7 Connector](#configure-s7connector)
        - [Configure IE Cloud Connector Local Lake](#configure-cloud-connector)
    - [Configuration Central Device]
        - [IE MQTT Connector]
        - [Configure IE-Flow Creator](#ie-flow-creator)
        - [Data Service Custom Adapter]
        - [Performance Insight]
   
## Configuration Device Energy 1 and Energy 2 

Configuration of the 2 edge devices for data transfer to the central edge device

### Configure Databus

In your IEM open the Databus and launch the configurator.

Add a user with this topic:
`"ie/#"`

![ie_databus_user](docs/graphics/IE_Databus.PNG)

![ie_databus](docs/graphics/IE_Databus.PNG)

Deploy the configuration.

### Configure S7 Connector

![Create PLC Connection](docs/graphics/add_data_source.PNG)

Launch the S7 Connector and configure the PLC connection 

Start and Deploy your S7 Connector. 

### Configure Cloud Connector Local Lake 

Add a topic in the Bus Adaptor(docs/graphics/configuration_bus_adaptor.PNG)

Afterwards create a Route in the middle. 

Add Cloud Connector Client by using Local Lake as an option. 

![Cloud_Conenctor_Local_Lake](docs/graphics/general_config_cloudconnector.PNG). 

Two topics must be specified: One for the data points and the other for the metadata(docs/graphics/general_config_cloudconnector.PNG)

Deploy process: Select the route, then the topic from the bus adaptor and at least the topic from the cloud connector. Then press Deploy.   


## Configuration Central Device 


### Configure Databus

### Configure IE MQTT Connector

### Import and Configure IE Flow Creator

### Setup Data Service

### Setup Performance Insight 

