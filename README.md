                            

Configuration Extract Tool
--------------------------

		

                                                
**Introduction:**

Configuration Extract tool contains scripts that can be used to extract the configuration data related to a specific cell in Websphere Application Server Environment.

You can make use of these scripts and customize it as per your requirements.


----------


**Need for CE Tool  :**
 
Websphere Application Server acts as the runtime environment for hosting J2EE Applications. It connects with various other products like Websphere MQ, DB2,  etc which is required by the application in order to provide service. Hence a JVM contains huge number of configuration parameters that are related to the product which they connect to and parameters which are related to the JVM itself.

Hence a WAS environment containing more JVM's has more configuration parameters and properties. During migration it becomes important to compare the configuration settings of older and new environment and between QA and Prod in the latest environment. A WAS environment containing more JVM's will have thousands of configuration properties to be compared. This requires huge manual effort to achieve this.

In order to minimize the effort, the CE Tool was created which contains scripts to extract different configuration settings of JVM. This uses the wsadmin scripting tool functionality that is provided by
Websphere Application Server.


----------


The CE tool contains the following Scripts:

 - DS_Properties.jacl ( Used to extract the configuration details of all
   the Data Source contained in a cell )
 - DS_Properties_v4.jacl ( Used to extract the configuration details of
   all V4 Data Source contained in a cell )
 - JVM_CustomProperties.jacl ( Used to extract the custom properties
   details of all the JVM's in a cell )
 - JVM_CustomServicesProperties.jacl ( Used to extract the custom
   services properties details of all the JVM's in a cell )

----------


*Script Usage:*

The script is written in JACL and should be invoked through wsadmin tool in WAS. The script should be executed from the bin path of Deployment Manager.

Eg:
> <WAS_ROOT>/profiles/DMGR_profile/bin/wsadmin.sh -f 
> /path/to/script/DS_CustomProperties.jacl  > /path/to/outputfile.txt


----------


**Script Functional Details:**

The script uses the Admin Config Object of wsadmin tool to extract data. 

*DS_Properties.jacl* - This script extracts all the configuration details of the Data Sources's that are configured in a cell. It collects all the Data Source details irrespective of the scope that it is mapped to.
It extracts details such as Provider Type, JNDI Name, Connection Timeout, Max Connections, Min Connections etc. 

*DS_Properties.jacl* - This script is similar to the DS_Properties.jacl script except that it extracts information of the Data Source that are configured under WAS V4 Data Source

*JVM_CustomProperties.jacl* - This script extracts the General and Custom Properties details of all the JVM's in the cell. It extracts Details such as Initial Heap, Max Heap, Generic JVM arguments, etc .

*JVM_CustomServicesProperties.jacl* -  Similar to JVM_CustomProperties.jacl  this job extracts the details of Custom Services Properties of all the JVM's in the cell


**Versions Tested :**

Script is tested with WAS version 6.x, 7.x and 8.5

This script can be used in any environment directly without making any changes.


----------

**Comparison**

You can use the data generated using the script  to find out the differences in the configurations between various environments.

You can use any of the comparison tool's like beyond compare, diff now etc in order to find out the differences between the configurations by uploading the data generated using the scripts.









