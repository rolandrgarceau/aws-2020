Dont move rousrces, add another to a different region...

elb needs rebuilt

nlb layer 7 what does that take

one nlb in front of 
Control plane. control plane is 2 k3s.

Expand what both nodes mean.

Node label and taints

run two of the top commands we have not good docs on 

running ui outside domain. we could run rancher server in house. obvious the cluster and workers in colo in DC. minimum in the colo exists one rack. Recommend to move outside of this because what happens when you have to scale? This is why we are running on AWS. For ISP monthly nut, most expensive part...

ISPs resale product. need upstream to sell. Carrie neutral. Cogent is the first upstream, and why they are the used they are cheap. 1000 for rack 400. need another provider. another 400 a month and havent don e anything. Need a stack of routers and switches, and also a way to get it out. dark fiber, and have to rent it out. another 800 for that. Now we are at 2800. need to get on the roof. now the building charges another 400 for top of roof center. then syslogs and all that. Do we run on prem or 2 node with rds. all yamls agnostic. only customer using cloud 2 nodes and a hosted db to run the rancher server with. that db is the orchestrator. then this shows why we keep it in the cloud. if it was on prem and it goes down... then talk expansion with another facility another dc. we keep the clusters anywhere, rancher server ran outside on aws. have the dr strategy. makes sense to run pipeline on aws too. Pipeline sitting outside on prem too. Then a lightning strikes. all we have to do is replace the raspberry pis and bring them up.

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