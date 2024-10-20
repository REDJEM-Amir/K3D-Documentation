# K3D-Documentation

### Dimensionnement selon les charges (Pods) :

| Nombre de Pods   | Nombre de Nœuds Serveurs (Control Plane)   | Nombre de Nœuds Agents   | Commandes de Lancement (Serveurs et Agents) |
|:-----------------|:-------------------------------------------|:-------------------------|:--------------------------------------------|
| 50 Pods          | 1 serveur                                  | 1 à 2 nœuds agents       | `k3d cluster create mycluster --servers 1 --agents 2 --k3s-arg "--kube-apiserver-arg=enable-admission-plugins=ResourceQuota@server:0" --agents-memory 1g --servers-memory 1g` |
| 250 Pods         | 3 serveurs                                 | 3 à 5 nœuds agents       | `k3d cluster create mycluster --servers 3 --agents 5 --k3s-arg "--kube-apiserver-arg=enable-admission-plugins=ResourceQuota@server:0" --agents-memory 2g --servers-memory 2g` |
| 500 Pods         | 3 serveurs                                 | 5 à 10 nœuds agents      | `k3d cluster create mycluster --servers 3 --agents 10 --k3s-arg "--kube-apiserver-arg=enable-admission-plugins=ResourceQuota@server:0" --agents-memory 4g --servers-memory 4g` |
| 1000+ Pods       | 3 à 5 serveurs                             | 10+ nœuds agents         | `k3d cluster create mycluster --servers 5 --agents 10 --k3s-arg "--kube-apiserver-arg=enable-admission-plugins=ResourceQuota@server:0" --agents-memory 4g --servers-memory 4g` |

### Explication

- **Serveurs** : Les nœuds serveurs (control plane) gèrent les composants principaux de Kubernetes (API server, scheduler, controller manager, etc.).
- **Agents** : Les nœuds agents sont responsables de l'exécution des pods et de la gestion des workloads.
- **Limites CPU et Mémoire** : Les valeurs optimales sont définies pour limiter l'impact sur la machine hôte tout en offrant suffisamment de ressources pour les charges de travail.

### Commandes k3d

| Commande                                      | Description                                      |
|:-------------------------------|:-------------------------------------------------|
| `k3d cluster start mycluster`  | Démarre le cluster `mycluster` s'il a été arrêté |
| `k3d cluster stop mycluster`   | Arrête le cluster `mycluster`.                   |
| `k3d cluster delete mycluster` | Supprime le cluster `mycluster`.                 |

### Commandes info

| Commande                              | Description                                    |
|:--------------------------------------|:-----------------------------------------------|
| `kubectl get svc --namespace default` | Affiche les services dans le namespace default |
| `kubectl get nodes`                   | Affiche la liste des nœuds du cluster          |
| `kubectl get pods`                    | Affiche la liste des pods                      |
| `kubectl logs <name-pod>`             | Affiche les logs du pod spécifié               |
| `kubectl describe pod <name-pod>`     | Donne des détails complets sur le pod spécifié |

### Commandes delete

| Commande                                                | Description                                                                     |
|:--------------------------------------------------------|:--------------------------------------------------------------------------------|
| `kubectl delete svc <name-service> --namespace default` | Supprime le service spécifié dans le namespace default                          |
| `kubectl delete deployment <name-deployment>`           | Supprime le déploiement spécifié                                                |
| `kubectl delete secret <name-secret> --ignore-not-found`| Supprime le secret spécifié, en ignorant l'erreur si le secret n'est pas trouvé |
| `kubectl delete pod <name-pod>`                         | Supprime le pod spécifié                                                        |

