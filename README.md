# Azure CLI - Cheat Sheet des 20% des Commandes les Plus Importantes

## Introduction

Azure CLI est un outil puissant pour gérer les ressources sur Microsoft Azure directement depuis le terminal. Cependant, face à la grande quantité de commandes disponibles, il peut être difficile de savoir par où commencer.

Ce **cheat sheet** vous présente les **20% des commandes les plus importantes** que vous utiliserez régulièrement pour déployer, gérer et sécuriser vos ressources Azure. Ce guide est conçu pour les développeurs, administrateurs systèmes, ou toute personne travaillant sur Azure, afin de gagner du temps et d'améliorer l'efficacité dans l'utilisation quotidienne de la ligne de command

---

## 📊 Gestion des Ressources

- **Créer un groupe de ressources** :

```bash
az group create --name MyResourceGroup --location francecentral
```

- **Lister les groupes de ressources :**

```bash
az group list --output table
```

- **Supprimer un groupe de ressources** :

```bash
az group delete --name MyResourceGroup --yes --no-wait
```

## 💻 Machines Virtuelles (VM)

- **Créer une VM** :

```bash
az vm create --resource-group MyResourceGroup --name MyVM --image UbuntuLTS --admin-username azureuser --generate-ssh-keys
```

- **Démarrer une VM** :

```bash
az vm start --resource-group MyResourceGroup --name MyVM
```

- **Arrêter une VM** :

```bash
az vm stop --resource-group MyResourceGroup --name MyVM
```

- **Supprimer une VM**:

```bash
az vm delete --resource-group MyResourceGroup --name MyVM --yes --no-wait
```

## 📦 Azure Container Registry (ACR)

- **Se connecter à un Azure Container Registry :**

```bash
az acr login --name MyRegistry
```

- **Créer un ACR** :

```bash
az acr create --resource-group MyResourceGroup --name MyRegistry --sku Basic
```

- **Lister les référentiels dans un ACR :**

```bash
az acr repository list --name MyRegistry --output table
```

## 🌐 Applications Web

- **Créer une application web** :

```bash
az webapp create --resource-group MyResourceGroup --plan MyAppServicePlan --name MyWebApp --runtime "NODE|14-lts"
```

- **Déployer une application web avec Git** :

```bash
az webapp deployment source config --name MyWebApp --resource-group MyResourceGroup --git-url https://github.com/myrepo.git
```

- **Lister les applications web** :

```bash
az webapp list --resource-group MyResourceGroup --output table
```

## 🌍 Réseau et Sécurité

- **Créer un réseau virtuel (VNet)** :

```bash
az network vnet create --name MyVNet --resource-group MyResourceGroup --subnet-name MySubnet
```

- **Créer un groupe de sécurité réseau (NSG) :**

```bash
az network nsg create --resource-group MyResourceGroup --name MyNSG
```

- Ajouter une règle au groupe de sécurité réseau :

```bash
az network nsg rule add --resource-group MyResourceGroup --nsg-name MyNSG --name MyRule --protocol tcp --priority 1000 --destination-port-range 80 --access allow
```

## 💾 Stockage

- **Créer un compte de stockage :**

```bash
az storage account create --name mystorageaccount --resource-group MyResourceGroup --sku Standard_LRS --kind StorageV2 --location francecentral
```

- **Créer un conteneur de stockage :**

```bash
az storage container create --name mycontainer --account-name mystorageaccount
```

- **Télécharger un fichier dans un conteneur** :

```bash
az storage blob upload --container-name mycontainer --file myfile.txt --name myfile.txt --account-name mystorageaccount
```

## 🔑 Authentification et Comptes

- **Se connecter à Azure** :

```bash
az login
```

- **Lister les abonnements :**

```bash
az account list --output table
```

- **Changer d'abonnement** :

```bash
az account set --subscription "My Subscription Name"
```
