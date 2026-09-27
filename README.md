# ⚡ Station de Recharge Intelligente pour Véhicules Électriques (SRM-FM)

Bienvenue dans le dépôt du projet **Station de Recharge Intelligente pour Véhicules Électriques (IRVE)** raccordée au réseau électrique de la **Société Régionale Multiservices Fès-Meknès (SRM-FM)**.

Ce projet propose une modélisation, une simulation et une stratégie de gestion intelligente de l'énergie (*Energy Management System* - EMS) sous **MATLAB/Simulink** pour optimiser l'intégration des bornes de recharge sur le réseau de distribution électrique régional.

## 📋 Table des Matières

 1. [À Propos du Projet](#-à-propos-du-projet)

 2. [Fonctionnalités Principales](#-fonctionnalités-principales)

 3. [Architecture du Système](#-architecture-du-système)

 4. [Prérequis](#-prérequis)

 5. [Installation & Configuration](#-installation--configuration)

 6. [Structure du Dépôt](#-structure-du-dépôt)

 7. [Guide de Simulation](#-guide-de-simulation)

 8. [Résultats & Performances](#-résultats--performances)

 9. [Perspectives](#-perspectives)

10. [Auteurs & Remerciements](#-auteurs--remerciements)

## 💡 À Propos du Projet

L'intégration massive des véhicules électriques (VÉ) impose de nouveaux défis d'exploitation sur le réseau électrique de la **SRM-FM** (pics de puissance, chutes de tension, harmoniques).

Ce projet vise à concevoir une station de recharge intelligente capable d'interagir dynamiquement avec le réseau, d'intégrer des sources d'énergie renouvelable (solaire PV) et d'utiliser un système de stockage local (BESS) pour lisser les appels de charge.

### Objectifs Clés :

* **Gestion Dynamique de la Charge** : Régulation de la puissance délivrée selon l'état du réseau (Peak Shaving / Load Balancing).

* **Intégration d'Énergie Solaire (PV)** : Optimisation de l'autoconsommation via des algorithmes MPPT.

* **Gestion Bidirectionnelle (G2V / V2G)** : Contrôle des flux d'énergie entre le réseau, la batterie du véhicule et le stockage local.

* **Maintien de la Qualité de l'Énergie** : Atténuation des perturbations sur le nœud de raccordement du réseau SRM-FM.

## ✨ Fonctionnalités Principales

* 🔋 **Stratégie EMS Intelligente** : Algorithme de répartition de puissance basé sur le SOC (*State of Charge*) et le tarif horaire.

* ⚡ **Commande des Convertisseurs Power Electronics** : Hacheurs DC/DC et onduleurs/redresseurs bi-directionnels commandés en PWM.

* 🌐 **Modelisation du Réseau SRM-FM** : Prise en compte de l'impédance de ligne et du profil de charge BT/HTA.

* 📊 **Visualisation** et Monitoring : Traçage automatique des variables électriques (tensions, courants, SOC, puissances P/Q).

## 🏗️ Architecture du Système

```
               +----------------------------------+
               |     Réseau Électrique SRM-FM     |
               +----------------------------------+
                                | (Transfo HTA/BT)
                                v
                       +-----------------+
                       | Bus DC / Bus AC |
                       +-----------------+
                         /      |      \
                        /       |       \
                       v        v        v
         +---------------+  +-------+  +--------------------+
         | Système PV    |  |  BESS |  | Station VÉ         |
         | (Solaire MPPT)|  | (BAT) |  | (Convertisseur DC) |
         +---------------+  +-------+  +--------------------+

```

## 🛠️ Prérequis

Pour exécuter les modèles Simulink et les scripts associées :

* **MATLAB & Simulink** (Version R2021b ou plus récente recommandée)

* **Toolboxes Requises** :

  * *Simscape* / *Simscape Electrical* (Specialized Power Systems)

  * *Control System Toolbox*

  * *Signal Processing Toolbox*

  * *Stateflow* (optionnel, selon l'implémentation de la machine d'états)

## 🚀 Installation & Configuration

1. **Cloner le dépôt GitHub :**

   ```
   git clone https://github.com/Ghilmi/station-de-recharge-intelligente-pour-v-hicules-lectriques-connect-e-au-r-seau-de-la-SRM-FM.git
   cd station-de-recharge-intelligente-pour-v-hicules-lectriques-connect-e-au-r-seau-de-la-SRM-FM
   
   ```

2. **Lancer MATLAB** et définir le répertoire courant sur le dossier du projet.

3. **Charger les paramètres d'initialisation :** Dans la fenêtre de commande MATLAB, exécutez :

   ```
   run('init_params.m')
   
   ```

4. **Ouvrir le modèle principal Simulink :**

   ```
   open_system('station_recharge_srm_fm.slx')
   
   ```

## 📁 Structure du Dépôt

```
.
├── models/                     # Modèles Simulink (.slx)
│   ├── station_recharge_srm_fm.slx  # Modèle principal
│   └── components/             # Sous-systèmes (PV, VÉ, Réseau SRM-FM)
├── scripts/                    # Scripts MATLAB (.m)
│   ├── init_params.m           # Variables globales & paramètres
│   └── plot_results.m          # Traitement des résultats
├── data/                       # Données d'ensoleillement et profils de charge
├── docs/                       # Schémas d'architecture et documentation
├── LICENSE                     # Licence du projet
└── README.md                   # Fichier de présentation

```

## 📈 Guide de Simulation

1. Ouvrez le script `init_params.m` pour ajuster si besoin :

   * La capacité de la batterie VÉ (kWh) et le SOC initial.

   * L'irradiance solaire ($W/m^2$).

   * La limite de puissance maximale imposée par le contrat SRM-FM.

2. Lancez la simulation dans Simulink (`Ctrl + T` ou bouton **Run**).

3. Exécutez le script `plot_results.m` pour générer les courbes d'analyse.

## 🔮 Perspectives d'Évolution

* \[ \] Implémentation d'un algorithme de contrôle par logique floue (*Fuzzy Logic*)
