# soap-ws

## A lightweight and easy-to-use Java library to handle SOAP on a purely XML level.

### Intro
Welcome to soap-ws! This is a lightweight and easy-to-use Java library to handle SOAP message generation and SOAP message transmission on a purely XML level. With the usage of this library
within few lines of code you can easily import your WSDL and generate SOAP messages directly in an XML format. 
Then you can use the SoapClient to transmit this message over HTTP(s) to a web-service endpoint. 
Finally, you can run SoapServer to receive SOAP messages and and respond to them. 
And all of that requires no classes or stubs generation - everything happens directly in an XML format.


### Why should you use soap-ws?
Read this carefully and check if you know what we are talking about.

* Have you ever had problems with the versioning of web-service endpoints? Have you ever had to address the problem how to deal with many versions of the same classes generated from two versions of the same WSDL in one code base? Did you try to prefix the classes, change the package, or do any other mambo-jambo tricks that are clearly against the best-practices of software design?
* Have you every tried to chain and orchestrate a few web-service invocations applying some XSLT transformation to the consecutive responses forwarding them to the next endpoint? Have you ever seen how cumbersome it is using Java generated ws clients/servers?
* Have you ever had to re-generate the ws-stubs, recompile and redeploy you application because of a tiny change in the WSDL?
* Have you every been confused why you generate all these domain and stub classes to invoke one simple web-service operation and to get a plain response that could be processed with XSTL one-liner?
* Have you ever had to had to send a simple XML message to a SOAP server in a fire and forget mode?
* Have you ever had to expose a mock SOAP endpoint that would respond to the request sending a sample response -let's say in an unit test?
* Have you ever had to download a hierarchical WSDL file with hierarchical XSD schemas and store it on your local hard drive with all the import and includes fixed properly so that you can reuse it locally?
* Have you ever…

Yes, that's what soap-ws can do for you. But it can do much more, just dive in and check the plethora of stuff that we have implemented.

### SOAP specifications - what is supported
* supports WSDL 1.1
* supports SOAP 1.1 and 1.2
* supports all four WS flavors: rpc-encoded, rpc-literal, document-literal and document-encoded
* supports SSL

### Main features

soap-builder:

* soap message generation in the XML format on the basis of imported WSDL 
* fetch and store of a hierarchical WSDL with hierarchical XSD included in it

soap-server:

* endpoint exposition - communication and message handling purely in the XML format
* auto-responder - respond to a soap request with a sample content - in an unit-test
* HTTP and HTTPS support
* extensive operation matcher - match a request to a BindingOperation from the WSDL

soap-client:

* communication and message handling purely in the XML format
* basic authentication and SSL support
* proxy with basic authenticationsupport
* proper SOAPAction support in both SOAP versions

### License
The project is open-source and distributed under the Apache license, Version 2.0.
One module (soap-builder) is distributed under the LGPL 2.1 license (see the Note).
You can confidently use soap-ws in your commercial project.



## User Guide

### Quickstart

#### Add soap-ws to your maven project
In order to use soap-ws in your project you have to declare soap-ws in the dependencies section of your pom.xml. You can add soap-builder, soap-client, soap-server or all of them, dependening on the fact which components you want to use.
```xml
<dependencies>
        <dependency>
            <groupId>com.centeractive</groupId>
            <artifactId>soap-builder</artifactId>
            <version>1.0.1-SNAPSHOT</version>
        </dependency>
        <dependency>
            <groupId>com.centeractive</groupId>
            <artifactId>soap-client</artifactId>
            <version>1.0.1-SNAPSHOT</version>
        </dependency>
        <dependency>
            <groupId>com.centeractive</groupId>
            <artifactId>soap-server</artifactId>
            <version>1.0.1-SNAPSHOT</version>
        </dependency>
</dependencies>
```
soap-ws is not yet located in the central maven repo, thus you also have to add an additional repository to your config.
```xml
<repositories>
        <repository>
            <id>centeractive</id>
            <url>TODO</url>
        </repository>
</repositories>
```

#### soap-builder

#### soap-client
You can create an instance of a soap-client using the fluent builder. If you want to use a plain HTTP connection without tweaking any advance option you are good to go with the following snippet:
```java
SoapClient client = SoapClient.builder()
	.endpointUrl("http://example.com/endpoint")
	.build();
client.post(soapAction, message);
```

#### soap-server



### Maven repo
TODO

### Project modules
* soap-builder - responsible for the generation of SOAP XML messages.
* soap-client - responsible for the communication with a SOAP endpoint.
* soap-server - responsible for exposing SOAP endpoints and handling the requests.
* soap-examples - contains a few example how to use soap-ws.
* soap-test - contains integration tests - tests soap-client and soap-server in many tricky ways.


## Last but not least

### Who's behind it?
Tom Bujok [tom.bujok@centeractive.com, tom.bujok@reficio.org]

centeractive ag

www.centeractive.com

### Note
This project contains classes extracted from the soapUI code base by centeractive ag
in October 2011. They are located in the soap-builder module. Every extracted class is
annotated with an comment to fulfill he requirements of the LGPL 2.1 license under
which soapUI is released. That is also the reason why soap-builder module is also
released under LGPL 2.1 license. All other soap-ws modules are released under Apache
v.2 license. The main reason behind class the extraction was to separate the code that
is responsible for the generation of the SOAP messages from the rest of the soapUI's
code that is tightly coupled with other modules, such as soapUI's graphical user
interface, etc. The goal was to create an open-source java project whose main
responsibility is to handle SOAP message generation and SOAP transmission purely on
an XML level.

centeractive ag would like to express strong appreciation to SmartBear Software and
to the whole team of soapUI's developers for creating soapUI and for releasing its
source code under a free and open-source licence. centeractive ag extracted and
modifies some parts of the soapUI's code in good faith, making every effort not
to impair any existing functionality and to supplement it according to our
requirements, applying best practices of software design.