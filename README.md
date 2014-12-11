# JMeter Integration

## Overview

![images_community/download/attachments/5144984/icon.png](images_community/download/attachments/5144984/icon.png) This Converter tool updates existing JMeter scripts by adding the dynaTrace HTTP
Headers to tag each request sent by JMeter. [This enables dynaTrace Integration with Load Testing Tools](JMeter_Integration.html)

## Plugin Details


| Name | JMeter Integration
| :--- | :---
| Author | Joe Hoffman ([joe.hoffman@dynatrace.com](mailto:joe.hoffman@dynatrace.com))
| Supported dynaTrace Version | >= 5.5
| Supported JMeter Version | Tested with JMeter 2.x
| License | [dynaTrace BSD](dynaTraceBSD.txt)
| Support | [Not Supported ](https://community.compuwareapm.com/community/display/DL/Support+Levels#SupportLevels-Community)
| Release history | Version 1.0
| Download | [JMeter Script Modification ](dynaTrace_JMeterSample_v1.0.zip)  
| | [JMeter Script Converter ](JMeterScriptConverter.zip)

## Description

As you see in our [documentation on web load testing](https://community.compuwareapm.com/community/display/DOCDT40/Integration+with+Web+Load+Testing+and+Monitoring+Tools), it is necessary to add a special HTTP header to web
requests so they are correctly identified as synthetic requests and labelled appropriately by dynaTrace. In JMeter, this means that you'd have to add a HTTP Header Manager to every request sampler. In
order to save you from this manual and potentially error-prone task, we provide two ways of automatically adding these headers to your JMeter scripts.

### JMeter Tagging BeanShell PreProcessor

A BeanShell PreProcessor allows arbitrary code to be applied before a sampler is executed. This allows us to add the dynaTrace headers automatically, based on available context information such as the
sampler name, thread group name, and thread group number.

By adding the BeanShell PreProcessor to a thread group, dynaTrace headers are added to all requests executed by controllers in this group. This approach requires only slight changes compared to test
scripts processed by the script converter, and also supports request samplers added later to the script without requiring additional effort.

[dynaTrace Tagging Preprocessor](dynaTraceTagging.jmx)


### JMeter Script Converter

The JMeter Script converts existing JMeter script to dynaTrace header aware scripts by automatically adding these headers. For installation follow the instructions below.

**Automatic Script Conversion**

The script convert will create transaction names based on URLs. The timer name is created by extracting the "document" part of the URL. For <http://localhost:9090/frontend/menu.do> the timer _menu_
will be created. Use the following command to convert a JMeter script.

    
    
    JMeterConvert -source <sourceFilePath> -target <targetFilePath>

**Using Mapping Files**

In case you want to use customer timer names or if you want to reuse timers, it is recommended to create a mapping file using the following command.

    
    
    JMeterConvert -genMapping -mapping <mappingFilePath>

The mapping file is used to translate URLs to timer names. Below is an example mapping file of the GoSpace demo application. The format for mappings is _<URL>:<Timer Name>_. The use of mapping files
is also very useful if you want to convert muliple scripts and automate the conversion task.

    
    
    /frontend/:Start Page
    /frontend/main.jsp:Main Page
    /frontend/userlogin.do:User Login
    /frontend/query.do:Query Page
    /frontend/list.do:List Result
    /frontend/sale.do:Sale
    /frontend/menu.do:Menu Option

In order to use the mapping file for the conversion use the command below.

    
    
    JMeterConvert -source <sourceFilePath> -target <targetFilePath> -mapping <mappingFilePath>

**Contribution**

Please post a comment in case of bug reports, enhancements or questions.

### JMeter Script Modification

This sample describes how to setup transactions within JMeter so that the Transaction name shows up within the dynaTrace Diagnostics Client under the Tagged Web Requests view.

When load scripts are executed from a load generator tool such as JMeter or Silk Performer, it is very helpful to define from within the Load generator tool specific transactions by name and be able
to correlate those transaction names to what is being seen from within the dynaTrace Diagnostics Client GUI. This integration is automatic for the Silk Performer tool and can easily be done for load
script tools such as JMeter. This Technology Sample describes how to do this for JMeter and provides a sample JMeter load script to be used against the dynaTrace sample application GoSpace.

The attached zip file contains a descriptive document on how to perform this integration as well as a JMeter script for exercising the GoSpace application which demonstrates the Tagged Web Request
technology. The JMeter script assumes you already have JMeter downloaded and installed. From within JMeter, select File -> Open, and select the attached script file.

## Install

  1. Save [JMeterScriptConverter](JMeterScriptConverter.zip) 

  2. Unzip the file. 

  3. **For the Script MOdification Guide** Follow the instructions in the 'HowTo Setup JMeter Integration.pdf' document  
**For the Script Converter** Run the JMeterConvert script. For usage see description above. 





