kitchensink-jsp: Example Using Multiple Jakarta EE 6 Technologies with a JSP (JavaServer Pages) Front End
======================================================================================================

<a href="https://codeready-openshift-workspaces.apps.cluster-5ac3.5ac3.sandbox1017.opentlc.com/f?url=https://github.com/audomsak/kitchensink-example"><img src="https://audomsak.tinytake.com/media/1007453?filename=1620599609704_10-05-2564-05-33-28.png&sub_type=thumbnail_preview&type=attachment&width=452&height=52" width="250" height="30" /></a>

Author: Elvadas Nono

What is it?
-----------

jboss-as-kitchensink-jsp is a deployable Maven 3 project to help you
get your foot in the door developing with Jakarta EE 6 on JBoss AS 7 or JBoss Enterprise Application Platform 6. This 
project is setup to allow you to create a compliant Jakarta EE 6 application 
using *JSP 2.0* *EL 2.0* *JSTL 1.2* *CDI 1.0*, *EJB 3.1*, *JPA 2.0* and Bean Validation 1.0. 

This project rebuilds the presentation tier of the kitchensink quickstart app
 using JSP and JSTL instead of JSF features.

It is another  app based on JSP that reused all other components from the
Member Registration template.
It reused the persistence unit and some sample persistence and transaction code to help 
you get your feet wet with database access in enterprise Java. 

System requirements
-------------------

All you need to build this project is Java 6.0 (Java SDK 1.6) or better, Maven
3.0 or better.

The application this project produces is designed to be run on a JBoss AS 7 or JBoss Enterprise Application Platform 6. 
The following instructions target JBoss AS 7, but they also apply to JBoss Enterprise Application Platform 6.
 
With the prerequisites out of the way, you're ready to build and deploy.

Deploying the application
-------------------------
 
First you need to start JBoss AS 7 (or JBoss Enterprise Application Platform 6). To do this, run
  
    $JBOSS_HOME/bin/standalone.sh
  
or if you are using windows
 
    $JBOSS_HOME/bin/standalone.bat

To deploy the application, you first need to produce the archive to deploy using
the following Maven goal:

    mvn package

You can now deploy the artifact to JBoss AS by executing the following command:

    mvn jboss-as:deploy

This will deploy `target/jboss-as-kitchensink-jsp.war`.
 
The application will be running at the following URL <http://localhost:8080/jboss-as-kitchensink-jsp/>.

To undeploy from JBoss AS, run this command:

    mvn jboss-as:undeploy

You can also start JBoss AS 7 and deploy the project using Eclipse. See the JBoss AS 7
<a href="https://docs.jboss.org/author/display/AS71/Getting+Started+Developing+Applications+Guide" title="Getting Started Developing Applications Guide">Getting Started Developing Applications Guide</a> 
for more information.
 
Running the Arquillian tests
============================

By default, tests are configured to be skipped. The reason is that the sample
test is an Arquillian test, which requires the use of a container. You can
activate this test by selecting one of the container configuration provided 
for JBoss AS 7 (remote).

To run the test in JBoss AS 7, first start a JBoss AS 7 instance. Then, run the
test goal with the following profile activated:

    mvn clean test -Parq-jbossas-remote

Importing the project into an IDE
=================================

If you created the project using the Maven archetype wizard in your IDE
(Eclipse, NetBeans or IntelliJ IDEA), then there is nothing to do. You should
already have an IDE project.

Detailed instructions for using Eclipse with JBoss AS 7 are provided in the 
JBoss AS 7 <a href="https://docs.jboss.org/author/display/AS71/Getting+Started+Developing+Applications+Guide" title="Getting Started Developing Applications Guide">Getting Started Developing Applications Guide</a>.

If you created the project from the commandline using archetype:generate, then
you need to import the project into your IDE. If you are using NetBeans 6.8 or
IntelliJ IDEA 9, then all you have to do is open the project as an existing
project. Both of these IDEs recognize Maven projects natively.

Downloading the sources and Javadocs
====================================

If you want to be able to debug into the source code or look at the Javadocs
of any library in the project, you can run either of the following two
commands to pull them into your local repository. The IDE should then detect
them.

    mvn dependency:sources
    mvn dependency:resolve -Dclassifier=javadoc
