# Utilisation et structure des templates

Ce document décrit les templates créés dans `mychart/templates` et comment les adapter à vos besoins.

Templates fournis:

- `_helpers.tpl` : fonctions d'aide pour générer les noms et labels (`mychart.name`, `mychart.fullname`, `mychart.labels`).
- `deployment.yaml` : Deployment basique utilisant les valeurs de `values.yaml` (`replicaCount`, `image`, `env`, `resources`).
- `service.yaml` : Service exposant le `targetPort` égal à `service.port`.
- `ingress.yaml` : Ingress conditionnel activé par `ingress.enabled`. Configure `hosts`, `annotations`, `tls` et `ingressClassName` depuis `values.yaml`.
- `NOTES.txt` : instructions post-installation.

Points d'attention et exemples :

- Variables d'environnement : dans `values.yaml` mettez `env` comme map :

```yaml
env:
  - name: ENV_VAR
    value: "value"
```

- Ingress `hosts` : exemple dans `values.yaml` :

```yaml
ingress:
  enabled: true
  hosts:
    - host: example.com
      path: /
      pathType: Prefix
  tls:
    - hosts:
        - example.com
      secretName: example-tls
```

- Resources, affinity, tolerations : remplissez les maps `resources`, `nodeSelector`, `tolerations`, `affinity` dans `values.yaml` selon vos contraintes.

Validation locale :

```bash
# Template pour voir le YAML rendu
helm template myrelease ./mychart

# Vérifier les bonnes pratiques et erreurs
helm lint ./mychart
```

Souhaitez-vous que je :
- fournisse un `values.yaml` exemple complet pour une image précise, ou
- adapte les templates à des champs supplémentaires (liveness/readiness, extra volumes, initContainers, etc.) ?
