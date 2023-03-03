Build an image using Docker:
``docker build -t jsong233/event-bus .``

Push the image to Docker Hub:
``docker push jsong233/event-bus``

Create a deployment:
``kubectl apply -f event-bus-depl.yaml``

Create a Cluster IP service:


