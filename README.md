# K3D-Documentation

### Dimensionnement selon les charges (Pods) :

| Nombre de Pods   | Nombre de Nœuds Serveurs (Control Plane)   | Nombre de Nœuds Agents   |
|:-----------------|:-------------------------------------------|:-------------------------|
| 50 Pods          | 1 serveur                                  | 1 à 2 nœuds agents       |
| 250 Pods         | 3 serveurs                                 | 3 à 5 nœuds agents       |
| 500 Pods         | 3 serveurs                                 | 5 à 10 nœuds agents      |
| 1000+ Pods       | 3 à 5 serveurs                             | 10+ nœuds agents         |

### commandes essentielles

| Commande                                      | Description                                                                                       |
|:----------------------------------------------|:--------------------------------------------------------------------------------------------------|
| `k3d cluster create mycluster`                | Crée un cluster Kubernetes nommé `mycluster` avec 1 serveur et 1 nœud agent.                       |
| `k3d cluster create mycluster --servers 3`    | Crée un cluster avec 3 nœuds serveurs pour la haute disponibilité.                                 |
| `k3d cluster create mycluster --agents 3`     | Crée un cluster avec 1 serveur et 3 nœuds agents pour exécuter les applications.                   |
| `k3d cluster delete mycluster`                | Supprime le cluster `mycluster`.                                                                   |
| `kubectl get nodes`                           | Affiche la liste des nœuds dans le cluster.                                                        |
| `k3d cluster stop mycluster`                  | Arrête le cluster `mycluster`.                                                                     |
| `k3d cluster start mycluster`                 | Démarre le cluster `mycluster` s'il a été arrêté.                                                  |
| `k3d node create mynode --role agent`         | Ajoute un nouveau nœud agent nommé `mynode` au cluster existant.                                   |
| `k3d node delete mynode`                      | Supprime le nœud nommé `mynode` du cluster.                                                        |
| `kubectl expose deployment myapp --port=80`   | Expose un service Kubernetes pour l'application `myapp` sur le port 80.                            |
| `kubectl apply -f mydeployment.yaml`          | Applique une configuration Kubernetes à partir d'un fichier YAML.                                  |
| `k3d cluster create mycluster --servers 1 \`  | Crée un cluster avec des limitations de ressources (500m CPU et 1Gi de RAM) pour les composants.    |
| `  --k3s-server-arg "--kubelet-arg=--kube-reserved=cpu=500m,memory=1Gi"` |
