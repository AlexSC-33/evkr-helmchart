# mychart — Documentation

Ce répertoire contient un chart Helm minimal scaffoldé pour votre application.

Emplacement: `/home/alex/evkr-helmchart/mychart`

Fichiers importants:

- `Chart.yaml` : métadonnées du chart (à compléter par vos soins).
- `values.yaml` : valeurs par défaut (remplissez `image.repository`, `image.tag`, `ingress.hosts`, ...).
- `.helmignore` : fichiers ignorés lors du packaging.
- `templates/` : templates Kubernetes (Deployment, Service, Ingress, helpers, NOTES).

Usage rapide (WSL ou PowerShell):

```powershell
# Vérifier le chart
helm lint ./mychart

# Générer manifests (local, sans cluster)
helm template myrelease ./mychart

# Installer dans un namespace de test
helm install myrelease ./mychart --namespace test --create-namespace

# Mettre à jour après modification
helm upgrade myrelease ./mychart --namespace test

# Désinstaller
helm uninstall myrelease --namespace test
```

Remplir `values.yaml` :

- `replicaCount` : nombre de replicas
- `image.repository` : image container (ex: `nginx` ou `myregistry/myapp`)
- `image.tag` : tag (ex: `1.2.3`)
- `service.type` : `ClusterIP` / `LoadBalancer` / `NodePort`
- `service.port` : port du service exposé
- `ingress.enabled` : `true` pour activer l'Ingress
- `ingress.hosts` : liste d'objets `{ host: "example.com", path: "/" }`

Après avoir rempli `values.yaml`, je peux adapter les templates et lancer `helm lint` pour vérifier les erreurs.

Si vous voulez, je peux aussi fournir un exemple concret de `values.yaml` pour une image donnée.
