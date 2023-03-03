Build an image using Docker:
``docker build -t jsong233/event-bus .``

Push the image to Docker Hub:
``docker push jsong233/event-bus``

Create a deployment:
``kubectl apply -f event-bus-depl.yaml``

Create a Cluster IP service:
in event-bus-depl.yaml

To communicate between different pods (each of which has an associated Cluster IP Service), the service inside the pod makes a request to 
``http://name-of-the-cluster-ip-service:port-number``

Update image used by a deployment:
build the image, push the image to the docker hub, run the command:
``kubectl rollout restart deployment [depl_name]``

Wire it up with the React app: 
React App running in browser -> Load Balancer (getting traffic into the cluster) -> Ingress Controller (a set of routing rules) -> Cluster IP Services -> different Pods

Install **ingress-nginx**:
``https://kubernetes.github.io/ingress-nginx/deploy/#quick-start``


Build Ingress Controller by ingress-srv.yaml


For development purposes, we need to trick our local machine into connecting to localhost whenever we go to posts.com. To do so, modify the Host File on our local machine by adding a line at the bottom:
``127.0.0.1 posts.com``


Use ``skaffold.yaml`` to watch all the yaml files in ``/infra/k8s/``.
Whenever there are changes in those files, skaffold will auto reapply the config files for our kubernetes cluster.

Start up skaffold:
``skaffold dev``