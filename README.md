#JMapper Framework [![Build Status](https://travis-ci.org/jmapper-framework/jmapper-core.svg?branch=master)](https://travis-ci.org/jmapper-framework/jmapper-core)

> Version 1.6.0.1 Released! You can check the [release notes](https://github.com/jmapper-framework/jmapper-core/wiki/Release-Notes) for more information.


#####Fast as hand-written code with zero compromise.
#####Write the configuration using what you prefer: Annotation, XML or API.
Most relevant features:

  * [One to Many](https://github.com/jmapper-framework/jmapper-core/wiki/One-To-Many) and [Many to One](https://github.com/jmapper-framework/jmapper-core/wiki/Many-To-One) relationship
  * [dynamic conversions](https://github.com/jmapper-framework/jmapper-core/wiki/Conversion-examples), whose body adapts to every relationship
  * [inherited configurations](https://github.com/jmapper-framework/jmapper-core/wiki/Inheritance-examples), you can split the configuration along the hierarchy
  * and more..
   
  
**especially its use is intuitive**

##Configuration
Below it is shown the same configuration in the three types allowed
#####Annotation
```java
class Destination{                      class Source{
    @JMap
    private String id;                      private String id;
    @JMap("sourceField")                    
    private String destinationField;        private String sourceField;
    private String other;                   private String other;

    // getters and setters...               // getters and setters...
}                                       }
```
#####XML
```xml
<jmapper>
  <class name="it.jmapper.bean.Destination">
    <attribute name="id">
      <value name="id"/>
    </attribute>
    <attribute name="destinationField">
      <value name="sourceField">
    </attribute>
  </class>
</jmapper>
```
#####API
```java
JMapperAPI jmapperAPI = new JMapperAPI()
    .add(mappedClass(Destination.class)
             .add(attribute("id")
                     .value("id"))
             .add(attribute("destinationField")
                     .value("sourceField")));
```

##Creation
```java
JMapper<Destination, Source> mapper;
```
#####Annotation
```java
mapper = new JMapper<>(Destination.class, Source.class);
```
#####XML
```java
mapper = new JMapper<>(Destination.class, Source.class, xml);
```
#####API
```java
mapper = new JMapper<>(Destination.class, Source.class, jmapperAPI);
```
##Usage
```java
Source source = new Source("id", "sourceField", "other");
Destination destination = mapper.getDestination(source);
```
##Result
```java
destination ["id", "sourceField", null]
```
*With JMapper we have all the advantages of dynamic mapping with the performance of static code, with 0 memory consumption.*<br>
**Required java 5+**<br><br>
**issues status**
<br>[![Stories in Progress](https://badge.waffle.io/jmapper-framework/jmapper-core.png?label=In Progress&title=In Progress)](https://waffle.io/jmapper-framework/jmapper-core)<br><br>
**Dependency information**
<br>[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.googlecode.jmapper-framework/jmapper-core/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.googlecode.jmapper-framework/jmapper-core) [![Dependency Status] (https://www.versioneye.com/user/projects/5539172d1d2989cb78000002/badge.svg?style=flat)](https://www.versioneye.com/user/projects/5539172d1d2989cb78000002)<br>

**For a complete guide**<br>[wiki](https://github.com/jmapper-framework/jmapper-core/wiki) pages<br><br>
**Do you like the project? think it has good potential?**<br>
Let us know any malfunctions, new features and more through the [JMapper Framework group](https://groups.google.com/forum/#!forum/jmapper-framework).<br><br>

**Do you want to contribute to the development of JMapper?**<br> 
There are many features to be implemented, such as:
- Eclipse plugin
- Integration with Hibernate, Apache Camel and other frameworks
- and more..

contact us (jmapper.framework@gmail.com) for more information.<br><br>
**Do you want to do a friendly chat?**<br>
[![Join the chat at https://gitter.im/jmapper-framework/jmapper-core](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/jmapper-framework/jmapper-core?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)<br><br>

**Follow us on twitter**<br>
<a href="https://twitter.com/jmapper_av"><img src="http://www.teachthought.com/wp-content/uploads/2012/10/twitter-logo-break.png" width="120" height="120" /></a>

