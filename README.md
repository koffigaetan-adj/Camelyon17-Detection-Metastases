# 🔬 Détection Automatisée de Métastases (Camelyon17)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](REMPLACE_CECI_PAR_L_URL_DE_TON_FICHIER_GITHUB)
[![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)](https://pytorch.org/)

## 📝 Description du Projet
Ce projet s'inscrit dans le cadre du défi **Camelyon17**. L'objectif est de développer une solution de Deep Learning capable d'assister les pathologistes dans la détection de micro-métastases de cancer du sein sur des images histologiques (Whole Slide Images).

L'analyse manuelle de ces biopsies est longue et fastidieuse. Notre solution propose une approche automatisée pour **trier les patients** (Screening) avec une priorité absolue : **la sécurité du diagnostic** (ne rater aucun malade).

## 🚀 Installation & Utilisation

### 💾 Téléchargement Direct (Dataset + Code)
Pour récupérer l'intégralité du projet, y compris le **Dataset complet déjà structuré** (plus simple pour une installation locale), vous pouvez accéder directement au dossier Google Drive :
👉 **[Accéder au Drive du Projet (Dataset inclus)](https://drive.google.com/drive/folders/1mxWaFfSpgqQXBgxatOzF11XOU5GzaHh1?usp=drive_link)**

---

### Option 1 : Google Colab (Recommandé & Rapide)
L'environnement est pré-configuré pour le Cloud.
1.  Cliquez sur le badge **"Open in Colab"** en haut de page.
2.  Le script de démarrage téléchargera les données nécessaires.
3.  Exécutez les cellules séquentiellement.

### Option 2 : Exécution en Local
Vous pouvez lancer ce notebook sur votre propre machine (Jupyter Lab / VS Code).

**Pré-requis :**
* Python 3.8+
* Bibliothèques : `torch`, `torchvision`, `pandas`, `numpy`, `plotly`, `opencv-python`.

**⚠️ Modifications pour le Local :**
Le code étant optimisé pour le Cloud, pensez à **nettoyer** les instructions spécifiques à Google avant de lancer :
1.  **Supprimez** les lignes de connexion au Drive (`from google.colab import drive`...).
2.  **Adaptez les chemins (Paths)** vers votre dossier local.

## ⚙️ Méthodologie Technique

L'approche repose sur un pipeline de classification d'images supervisé :

* **Architecture :** **ResNet18** (Transfer Learning via ImageNet).
* **Traitement :** Découpage des images géantes (WSI) en **Patchs** (Tiling).
* **Agrégation :** Stratégie de décision "Patient-Level" basée sur la moyenne des probabilités tumorales.
* **Optimisation :** Entraînement avec l'optimiseur Adam et gestion du déséquilibre des classes (Undersampling).

## 📊 Résultats Clés

Le modèle a été conçu comme un **outil de screening haute sensibilité**.

| Métrique | Résultat | Interprétation |
| :--- | :--- | :--- |
| **Accuracy (Patch)** | **93.4%** | Excellente distinction Tumeur/Sain au niveau cellulaire. |
| **Sensibilité (Patient)** | **100%** | **0 Faux Négatif.** Tous les patients malades ont été détectés. |
| **Spécificité (Patient)** | 66.7% | Quelques fausses alertes (Faux Positifs) par sécurité. |

## ⚠️ Limitations & Perspectives
* **Domain Shift :** Une sensibilité accrue a été observée sur certains centres hospitaliers (scanners plus saturés), générant des faux positifs.
* **Amélioration future :** Implémentation de techniques de *Stain Normalization* pour harmoniser les couleurs entre les hôpitaux.

---
*Projet réalisé dans le cadre académique Janvier  2026.*
