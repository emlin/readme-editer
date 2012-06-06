# Aurora_big_data: Serengeti's Web service and CLI
-----------
Serengeti helps you to deploy Hadoop clusters on vSphere fast and easy. It's a management service, which makes user start with Hadoop very easy.
This repo holds Serengeti Web Service and CLI.

## Getting Started
To jump into using Serengeti, follow our Installation Instructions. 

## Serengeti Web Service
-----------
Serengeti Web Service providers RESTful API for VC resources managment, hadoop cluster spec management. And also work as a proxy to invoke Serengeti provision engine and return fine-grained process execution status to caller.

### Web service archetecture
-----------
Web service archetecture:
![Web service archetecture (doc/ws-architecture.png)](https://github.com/llhe/readme-editer/raw/master/doc/ws-architecture.png "web service archetecture")

### Web service APIs
-----------
<table>
<tr><td>Method</td><td>URL Template</td><td>Request</td><td>Response</td><td>Description</td></tr>
<tr><td>GET</td><td>/hello</td><td>void</td><td>void</td><td></td></tr>
<tr><td>GET</td><td>/tasks</td><td>void</td><td>List of TaskRead</td><td>List all tasks</td></tr>
<tr><td>GET</td><td>/task/{taskId}</td><td>taskId</td><td>TaskRead</td><td>Get task by task id</td></tr>
<tr><td>POST</td><td>/clusters</td><td>ClusterCreate</td><td>Redirect to /task/{taskId}</td><td>Create cluster</td></tr>
<tr><td>GET</td><td>/clusters</td><td>void</td><td>List of ClusterRead</td><td>List all clusters</td></tr>
<tr><td>GET</td><td>/cluster/{clusterName}</td><td>clusterName</td><td>ClusterRead</td><td>Get cluster by name</td></tr>
<tr><td>PUT</td><td>/cluster/{clusterName}</td><td>clusterName; state=start/stop/resume</td><td>Redirect to /task/{taskId}</td><td>Operate a cluster: start; stop or resume a failed creation</td></tr>
<tr><td>PUT</td><td>/cluster/{clusterName}/nodegroup/{groupName}</td><td>clusterName; groupName; instanceNum</td><td>Redirect to /task/{taskId}</td><td>Resize cluster with a new instance number</td></tr>
<tr><td>DELETE</td><td>/cluster/{clusterName}</td><td>clusterName</td><td>Redirect to /task/{taskId}</td><td>Delete a cluster by name</td></tr>
<tr><td>POST</td><td>/resourcepools</td><td>ResourcePoolAdd</td><td>void</td><td>Add a resource pool</td></tr>
<tr><td>GET</td><td>/resourcepools</td><td>void</td><td>List of ResourcePoolRead</td><td>List all resource pools</td></tr>
<tr><td>GET</td><td>/resourcepool/{rpName}</td><td>rpName</td><td>ResourcePoolRead</td><td>Get resource pool by name</td></tr>
<tr><td>DELETE</td><td>/resourcepool/{rpName}</td><td>rpName</td><td>void</td><td>Delete a resource pool by name</td></tr>
<tr><td>POST</td><td>/datastores</td><td>DatastoreAdd</td><td>void</td><td>Add a datastore</td></tr>
<tr><td>GET</td><td>/datastores</td><td>void</td><td>List of DatastoreRead</td><td>List all datastores</td></tr>
<tr><td>GET</td><td>/datastore/{dsName}</td><td>dsName</td><td>DatastoreRead</td><td>Get datastore by name</td></tr>
<tr><td>DELETE</td><td>/datastore/{dsName}</td><td>dsName</td><td>void</td><td>Delete a datastore by name</td></tr>
<tr><td>POST</td><td>/networks</td><td>NetworkAdd</td><td>void</td><td>Add a network</td></tr>
<tr><td>GET</td><td>/networks</td><td>details=true/false</td><td>List of NetworkRead</td><td>List all networks</td></tr>
<tr><td>GET</td><td>/network/{networkName}</td><td>networkName; details=true/false</td><td>NetworkRead</td><td>Get a network by name</td></tr>
<tr><td>DELETE</td><td>/network/{networkName}</td><td>networkName</td><td>void</td><td>Delete a network by name</td></tr>
<tr><td>GET</td><td>/distros</td><td>void</td><td>List of DistroRead</td><td>List all distros</td></tr>
<tr><td>GET</td><td>/distro/{distroName}</td><td>distroName</td><td>DistroRead</td><td>Get a distro by name</td></tr>
</table>

