# mautic-kubernetes

The goal of this project is to be able to run Mautic on Kubernetes in a way that is easy to configure and manage.
## Step 1: Adapt the files

Make sure you change `placeholder` namespace occurences and `mautic.example.co` to match your deployment url and desired namespace

## Step 2: Set up MySQL Creds

Change the db secret credentials 
 * __DB_URL__
 * __DB_USERNAME__
 * __DB_PASSWORD__
 * __Database name is set by default to `mautic`__

Then use the `mysql.secret.yaml` file to store the cerds in the Kubernetes secret engine:

`kubectl apply -f mysql.secret.yaml`

## Step 3: Set up Mautic

First use the `mautic.deployment.yaml` file to deploy the manifest:

`kubectl apply -f mautic.deployment.yaml`

Then, expose the service on Port 80:

`kubectl apply -f mautic.service.yaml`

Finally, link your service to the desired domain name through the `mautic.ingress.yaml`

`kubectl apply -f mautic.ingress.yaml`

## Step 4: View your site!

After waiting a few minutes to create the containers and set up the IP forwarding rules, go to the desired subdomain name and you will see the installation screen.