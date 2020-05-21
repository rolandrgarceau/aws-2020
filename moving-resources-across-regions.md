# Rancher Controller

We spent a good deal of time deconstructiong our build on AWS to move the controllers into us-east-1. This procedure shoiuld not have to be done ever again. Build out by adding to a new region and AZ's and then subtracting those we do not wish to have any longer.

## tl;dr:
Dont move resources, add another to a different region...

* elb needs rebuilt

* nlb layer 7 what does that take to rebuild too? Records adjustment? Alias Cnames?

* There exists one nlb in front of the Control plane. Control plane is 2 k3s. Not KRE. Remember our use case on-prem.

* Expand what both nodes mean.
  * Node label and taints

* run two of the top commands or htop for process deiscovery?

## Further notes

We are running ui outside domain. We could run rancher server in house. It is obvious the cluster and workers in colo should reside in DC. minimum in the colo exists one rack. Recommend to move outside of this because what happens when you have to scale? This is why we are running on AWS. For ISP monthly the nut and bolt here becomes the most expensive part...

## Convo notes on Rancher buildout

ISPs resale product. We need upstream to sell. Carrier neutral. Cogent is the first upstream, and why they are the used? They are cheap. 1000 for rack cost +400 for need and another provider. another 400 a month and haven't done anything. Need a stack of routers and switches, and also a way to get it out. Dark fiber, and have to rent it out. another 800 for that. Now we are at 2800. need to get on the roof. Now the building charges another 400 for top of roof center access fee. Then syslogs and all that. Do we run on prem or 2 node with RDS? All yamls need to stay agnostic. only customer using cloud 2 nodes and a hosted db to run the rancher server with. that db is the orchestrator. Then this shows why we keep it in the cloud. If it was on prem and it goes down... then talk expansion with another facility or another dc. we keep the clusters anywhere, rancher server ran outside on aws. have the dr strategy. makes sense to run pipeline on aws too. Pipeline sitting outside on prem too. Then a lightning strikes. all we have to do is replace the raspberry pis or whatever we are running routers/switching with and bring them up.

## Todo

move data store
move control plane instances
    ssh in and grab endpoints for db connections
redirect ALB to new vpc

rds in current. take snap. copy snap to region
go to new region. restore in.

Shut down to get ami image for 2 k3s.
copy to new region.

get the ssh key from .ssh/known_hosts

need to set rds endpoint
need to set password in new rds instance.

matt mattox is a rancher support person. in slack room.

rancher ser is separated from k3s control nodes.