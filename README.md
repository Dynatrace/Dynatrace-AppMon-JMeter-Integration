<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <title>JMeter Integration</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
    <meta http-equiv="X-UA-Compatible" content="IE=EmulateIE8" />
    <meta content="Scroll Wiki Publisher" name="generator"/>

    <link type="text/css" rel="stylesheet" href="css/blueprint/liquid.css" media="screen, projection"/>
    <link type="text/css" rel="stylesheet" href="css/blueprint/print.css" media="print"/>
    <!--[if lt IE 8]><link rel="stylesheet" href="css/blueprint/ie.css" type="text/css" media="screen, projection"/><![endif]-->

    <link type="text/css" rel="stylesheet" href="css/content-style.css" media="screen, projection, print"/>
    <link type="text/css" rel="stylesheet" href="css/screen.css" media="screen, projection"/>
    <link type="text/css" rel="stylesheet" href="css/print.css" media="print"/>
</head>
<body>
                <h1>JMeter Integration</h1>
    <div class="section-2"  id="5144984_JMeterIntegration-Overview"  >
        <h2>Overview</h2>
    <p>
            <img src="images_community/download/attachments/5144984/icon.png" alt="images_community/download/attachments/5144984/icon.png" class="confluence-embedded-image image-center" />
        This Converter tool updates existing JMeter scripts by adding the dynaTrace HTTP Headers to tag each request sent by JMeter. <a href="JMeter_Integration.html">This enables dynaTrace Integration with Load Testing Tools</a>    </p>
    </div>
    <div class="section-2"  id="5144984_JMeterIntegration-PluginDetails"  >
        <h2>Plugin Details</h2>
    <div class="tablewrap">
        <table>
<thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" ">    <tr>
            <td rowspan="1" colspan="1">
        <p>
Name    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<strong class=" ">JMeter Integration</strong>    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
Version    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
1.0    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
Author    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
Joe Hoffman (<a href="mailto:joe.hoffman@dynatrace.com">joe.hoffman@dynatrace.com</a>)    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
License    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<a href="attachments_5275722_2_dynaTraceBSD.txt">dynaTrace BSD</a>    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
Support    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<a href="https://community/display/DL/Support+Levels#SupportLevels-Community">Not Supported </a>    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
Download    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<a href="attachments_5275746_1_dynaTrace_JMeterSample_v1.0.zip">JMeter Script Modification </a><br/><a href="attachments_10223677_1_JMeterScriptConverter.zip">JMeter Script Converter </a>    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
        <p>
Tested with    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
JMeter 2.x; dynaTrace v2.x v3.x    </p>
            </td>
        </tr>
</tbody>        </table>
            </div>
    </div>
    <div class="section-2"  id="5144984_JMeterIntegration-Description"  >
        <h2>Description</h2>
    <p>
As you see in our <a href="https://community/display/DOCDT40/Integration+with+Web+Load+Testing+and+Monitoring+Tools">documentation on web load testing</a>, it is necessary to add a special HTTP header to web requests so they are correctly identified as synthetic requests and labelled appropriately by dynaTrace. In JMeter, this means that you'd have to add a HTTP Header Manager to every request sampler. In order to save you from this manual and potentially error-prone task, we provide two ways of automatically adding these headers to your JMeter scripts.    </p>
    <div class="section-3"  id="5144984_JMeterIntegration-JMeterTaggingBeanShellPreProcessor"  >
        <h3>JMeter Tagging BeanShell PreProcessor</h3>
    <p>
A BeanShell PreProcessor allows arbitrary code to be applied before a sampler is executed. This allows us to add the dynaTrace headers automatically, based on available context information such as the sampler name, thread group name, and thread group number.    </p>
    <p>
By adding the BeanShell PreProcessor to a thread group, dynaTrace headers are added to all requests executed by controllers in this group. This approach requires only slight changes compared to test scripts processed by the script converter, and also supports request samplers added later to the script without requiring additional effort.    </p>
    <p>
    </p>
    <div class="tablewrap">
        <table>
<thead class=" ">    <tr>
            <td rowspan="1" colspan="1">
        <p>
&nbsp;    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<a href="JMeter_Integration.html">File</a>    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<a href="JMeter_Integration.html">Modified</a>    </p>
            </td>
        </tr>
</thead><tfoot class=" "></tfoot><tbody class=" ">    <tr>
            <td rowspan="1" colspan="1">
                </td>
                <td rowspan="1" colspan="1">
        <p>
File                    <a href="https://community/download/attachments/5144984/dynaTrace%20Tagging.jmx?api=v2">dynaTrace Tagging.jmx</a>dynaTrace Tagging Preprocessor    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
Nov 17, 2010by<a href="    /community/display/~michael.kopp@compuware.com ">Michael Kopp</a>    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
                </td>
                <td rowspan="1" colspan="2">
        <p>
    </p>
    <p>
Labels    </p>
<ul class="label-list has-pen "><li class="no-labels-message ">    <p>
No labels    </p>
</li><li class="labels-edit-container ">    <p>
<a href="JMeter_Integration.html">Edit Labels</a>    </p>
</li></ul>    <p>
    </p>
            </td>
        </tr>
</tbody>        </table>
            </div>
<ul class=" "><li class="drop-zone-text hidden ">    <p>
Drag and drop to upload or browse for files    </p>
            <img src="images_community/images/icons/wait.gif" alt="images_community/images/icons/wait.gif" class="plugin_attachments_dropzone_uploadwaiticon" />
        </li></ul>    <p>
Upload fileFile description    </p>
    </div>
    <div class="section-3"  id="5144984_JMeterIntegration-JMeterScriptConverter"  >
        <h3>JMeter Script Converter</h3>
    <p>
The JMeter Script converts existing JMeter script to dynaTrace header aware scripts by automatically adding these headers. For installation follow the instructions below.    </p>
    <p>
<strong class=" ">Automatic Script Conversion</strong>    </p>
    <p>
The script convert will create transaction names based on URLs. The timer name is created by extracting the &quot;document&quot; part of the URL. For <a href="http://localhost:9090/frontend/menu.do">http://localhost:9090/frontend/menu.do</a> the timer <i class=" ">menu</i> will be created. Use the following command to convert a JMeter script.    </p>
    <div class="confbox programlisting">
                <div class="content">
        <pre><code>JMeterConvert -source &lt;sourceFilePath&gt; -target &lt;targetFilePath&gt;</code></pre>
        </div>
    </div>
    <p>
<strong class=" ">Using Mapping Files</strong>    </p>
    <p>
In case you want to use customer timer names or if you want to reuse timers, it is recommended to create a mapping file using the following command.    </p>
    <div class="confbox programlisting">
                <div class="content">
        <pre><code>JMeterConvert -genMapping -mapping &lt;mappingFilePath&gt;</code></pre>
        </div>
    </div>
    <p>
The mapping file is used to translate URLs to timer names. Below is an example mapping file of the GoSpace demo application. The format for mappings is <i class=" ">&lt;URL&gt;:&lt;Timer Name&gt;</i>. The use of mapping files is also very useful if you want to convert muliple scripts and automate the conversion task.    </p>
    <div class="confbox programlisting">
                <div class="content">
        <pre><code>/frontend/:Start Page
/frontend/main.jsp:Main Page
/frontend/userlogin.do:User Login
/frontend/query.do:Query Page
/frontend/list.do:List Result
/frontend/sale.do:Sale
/frontend/menu.do:Menu Option</code></pre>
        </div>
    </div>
    <p>
In order to use the mapping file for the conversion use the command below.    </p>
    <div class="confbox programlisting">
                <div class="content">
        <pre><code>JMeterConvert -source &lt;sourceFilePath&gt; -target &lt;targetFilePath&gt; -mapping &lt;mappingFilePath&gt;</code></pre>
        </div>
    </div>
    <p>
<strong class=" ">Contribution</strong>    </p>
    <p>
Please post a comment in case of bug reports, enhancements or questions.    </p>
    </div>
    <div class="section-3"  id="5144984_JMeterIntegration-JMeterScriptModification"  >
        <h3>JMeter Script Modification</h3>
    <p>
This sample describes how to setup transactions within JMeter so that the Transaction name shows up within the dynaTrace Diagnostics Client under the Tagged Web Requests view.    </p>
    <p>
When load scripts are executed from a load generator tool such as JMeter or Silk Performer, it is very helpful to define from within the Load generator tool specific transactions by name and be able to correlate those transaction names to what is being seen from within the dynaTrace Diagnostics Client GUI. This integration is automatic for the Silk Performer tool and can easily be done for load script tools such as JMeter. This Technology Sample describes how to do this for JMeter and provides a sample JMeter load script to be used against the dynaTrace sample application GoSpace.    </p>
    <p>
The attached zip file contains a descriptive document on how to perform this integration as well as a JMeter script for exercising the GoSpace application which demonstrates the Tagged Web Request technology. The JMeter script assumes you already have JMeter downloaded and installed. From within JMeter, select File -&gt; Open, and select the attached script file.    </p>
    </div>
    </div>
    <div class="section-2"  id="5144984_JMeterIntegration-Install"  >
        <h2>Install</h2>
    <div class="confbox panel">
    <ol class=" "><li class=" ">    <p>
Save the attached file.    </p>
</li><li class=" ">    <p>
Unzip the file.    </p>
</li><li class=" ">    <p>
<strong class=" ">For the Script MOdification Guide</strong> Follow the instructions in the 'HowTo Setup JMeter Integration.pdf' document<br/><strong class=" ">For the Script Converter</strong> Run the JMeterConvert script. For usage see description above.    </p>
</li></ol>    </div>
    <p>
    </p>
    <div class="tablewrap">
        <table>
<thead class=" ">    <tr>
            <td rowspan="1" colspan="1">
        <p>
&nbsp;    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<a href="JMeter_Integration.html">File</a>    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
<a href="JMeter_Integration.html">Modified</a>    </p>
            </td>
        </tr>
</thead><tfoot class=" "></tfoot><tbody class=" ">    <tr>
            <td rowspan="1" colspan="1">
                </td>
                <td rowspan="1" colspan="1">
        <p>
ZIP Archive                    <a href="https://community/download/attachments/5144984/JMeterScriptConverter.zip?api=v2">JMeterScriptConverter.zip</a>    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
Feb 13, 2009by<a href="    /community/display/~alois.reitbauer@compuware.com ">Alois Reitbauer</a>    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
                </td>
                <td rowspan="1" colspan="2">
        <p>
    </p>
    <p>
Labels    </p>
<ul class="label-list has-pen "><li class="no-labels-message ">    <p>
No labels    </p>
</li><li class="labels-edit-container ">    <p>
<a href="JMeter_Integration.html">Edit Labels</a>    </p>
</li></ul>    <p>
    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
                </td>
                <td rowspan="1" colspan="1">
        <p>
ZIP Archive                    <a href="https://community/download/attachments/5144984/dynaTrace_JMeterSample_v1.0.zip?api=v2">dynaTrace_JMeterSample_v1.0.zip</a>    </p>
            </td>
                <td rowspan="1" colspan="1">
        <p>
Jun 21, 2008by<a href="    /community/display/~ted.feyler@compuware.com ">Ted Feyler</a>    </p>
            </td>
        </tr>
    <tr>
            <td rowspan="1" colspan="1">
                </td>
                <td rowspan="1" colspan="2">
        <p>
    </p>
    <p>
Labels    </p>
<ul class="label-list has-pen "><li class="no-labels-message ">    <p>
No labels    </p>
</li><li class="labels-edit-container ">    <p>
<a href="JMeter_Integration.html">Edit Labels</a>    </p>
</li></ul>    <p>
    </p>
            </td>
        </tr>
</tbody>        </table>
            </div>
<ul class=" "><li class="drop-zone-text hidden ">    <p>
Drag and drop to upload or browse for files    </p>
            <img src="images_community/images/icons/wait.gif" alt="images_community/images/icons/wait.gif" class="plugin_attachments_dropzone_uploadwaiticon" />
        </li></ul>    <p>
Upload fileFile description<a href="https://community/pages/downloadallattachments.action?pageId=5144984">Download All</a>    </p>
    </div>
            </div>
        </div>
        <div class="footer">
        </div>
    </div>
</body>
</html>
