==================
StarlingX SDO Demo
==================

------------
Introduction
------------

This is a demo to show on StarlingX infrastructure, how to run Rendezvous server for performing secure device onboarding.

For more information on SDO, please refer `SDO <https://www.intel.in/content/www/in/en/internet-of-things/secure-device-onboard.html>`_ 

The demo scenario is tested based on the following versions:

#.  **StarlingX**: STX 4.0 Version
#.  **SDO sdk**: [Pre-built/binaries version 1.7.0.91]( )

-------------------
Setup StarlingX Env
-------------------

#. Follow `StarlingX Documents <https://docs.starlingx.io/>`_ to setup the simplex.

#. Run Rendezvous server on Starlingx
   
   Copy the RV service from the `gitlab <https://gitlab.devtools.intel.com/starlingx/demos/-/tree/sdo/sdo-in-stx>`_ to the home 
   directory of the controller. 
  
#. Follow below commands to deploy the Rendezvous service on the simplex  
   
   ::
    
     cd ~/demos/sdo-in-stx/SDOonPrem/dockerfile/ 
     ./DO.sh build #builds the RV service  
     ./DO.sh run  #Helm commands are automated to create a new deploy  

#. Following is the sample output for the kubectl get po,svc  

   ::

     controller-0:~/demos$ kubectl get po,svc   
     NAME                             READY   STATUS    RESTARTS   AGE
     pod/redis-697fb49877-nbtqk       1/1     Running   0          20h  
     pod/rv.deploy-75686f7f99-zhzrv   1/1     Running   0          20h  
     NAME                   TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                         AGE  
     service/kubernetes     ClusterIP   10.96.0.1        <none>        443/TCP                         3d17h  
     service/redis          NodePort    10.104.198.241   <none>        6379:30008/TCP                  20h  
     service/rvdeploy-int   NodePort    10.96.248.186    <none>        8000:31450/TCP,8001:30007/TCP   20h  

#. Check the status of the rendezvous service on the controller by using below command. For example for the pod listed above,
   the command is:  

   ::

      kubectl logs -f pod/rv.deploy-75686f7f99-zhzrv  
   
   
     



