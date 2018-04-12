# Credit Card Fraud Demo

Cloudbreak Installation Directions:

Create cloudbreak cluster at demo-store-cb.field.hortonworks.com
  
  Instructions on creating cloudbreak credentials can be found here: https://hortonworks.app.box.com/file/285832790946
  
Create a cluster with the following specifications:

1. Blueprint: hdp-hdf-multi-node_v1.2 (most recent version)
2. All three nodes set to m3-xlarge-openstack
3. First node checked as Ambari Server
4. First node recipe set to: canonical-hdf-service install

OpenStack Installation Directions -- recommend to use Cloudbreak:

1. Create 3 node cluster with m3.xlarge sizing
2. Install Ambari 2.5.2 and HDP 2.6.2
3. Git clone this repo onto ambari node
4. Run hdp-hdf-post-install script 
5. Add Demo through Ambari Service


After cluster creation is finished, the Credit Card Fraud Demo can be added as an Ambari Service. The first time this is done, a Google Maps API key will be required. This can be found here: https://developers.google.com/maps/documentation/javascript/get-api-key 
After completion of the wizard the simulation will start and transactions will begin flowing into the UI. 

To maintain cluster integrity, ssh into the cluster after the demo and run the /stopSimulation.sh script found in /root/CreditCardTransactionMonitor. This will shut down the simulation and stop the transaction flow.

For additional analysis: Add Zeppelin Notebook as an Ambari Service. Import Note from URL: https://raw.githubusercontent.com/therson/Credit-Card-Fraud-Demo/master/Zeppelin/note.json. This note is the notebook to create the fraud prediction model used to predict whether an individual transaction is fradulent or not.
