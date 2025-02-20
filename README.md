# PgHero Helm Chart
## Deployment

1. Create Kubernetes secret for PGHERO

```bash
kubectl create secret generic pghero \
  --from-literal=database_url='postgres://user:password@hostname:5432/dbname' \
  --from-literal=username='admin' \
  --from-literal=password='StrongPassword123'
```

2. Add custom Helm Chart repository

```bash
helm repo add custom-pghero https://cyberglamdring.github.io/pghero-helmchart/ && helm repo update 
```

3. Fill in values.yaml if necessary. If `secretName` exists, then below `database`, `pgheroUser` and `pgheroUser` fields are not valid

4. Install PGHERO helm chart

```bash
helm install pghero -f pghero-helmchart-values.yaml custom-pghero/pghero 
```
## Configuration

The following table lists the configurable parameters of the PgHero chart and their default values

| Parameter | Description | Default |
|:---|:---|:---|
| `secretName` | PgHero secret name. If `secretName` exists, then below database and credential fields are not valid | `pghero` |
| `database.user` | DataBase username | `""` |
| `database.password` | DataBase password | `""` |
| `database.url` | DataBase URL | `""` |
| `database.port` | DataBase port | `5432` |
| `database.dbName` | DataBase name | `""` |
| `pgheroUser` | Login user name | `""` |
| `pgheroPassword` | Login user password | `""` |

## Removal

To remove PGHERO use following command: 

```bash
helm unistall pghero
```

---
Sources: https://github.com/ankane/pghero
