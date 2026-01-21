# 💶 Calculateur d'Intérêts de Retard — Eurovia / VINCI

![Version](https://img.shields.io/badge/version-2.0.0-blue)
![Python](https://img.shields.io/badge/python-3.10+-green)
![Streamlit](https://img.shields.io/badge/streamlit-1.28+-red)
![License](https://img.shields.io/badge/license-proprietary-gray)

Application professionnelle pour le calcul des intérêts moratoires et pénalités de retard dans le secteur BTP.

---

## 📋 Fonctionnalités

### Modes de calcul

| Mode | Base légale | Taux | Actualisation |
|------|-------------|------|---------------|
| **Client Privé** | L.441-10 C.Com | BCE + 10 pts | Semestrielle (1er janv. / 1er juil.) |
| **Client Public** | R.2192-31 CCP | BCE + 8 pts | Annuelle (1er janvier) |
| **Manuel** | Clause contractuelle | Taux fixe | Aucune |

### Caractéristiques

- ✅ Téléchargement automatique des taux BCE (API BCE + fallback FRED)
- ✅ Calcul segmenté par période (gestion multi-semestres/années)
- ✅ Indemnité forfaitaire de 40 € automatique
- ✅ Export HTML et CSV
- ✅ Historique des calculs
- ✅ Interface responsive style Apple

---

## 🚀 Installation

### Prérequis

- Python 3.10 ou supérieur
- pip (gestionnaire de paquets Python)

### Installation locale

```bash
# Cloner ou télécharger le projet
cd interets_app

# Créer un environnement virtuel (recommandé)
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
venv\Scripts\activate     # Windows

# Installer les dépendances
pip install -r requirements.txt

# Lancer l'application
streamlit run app.py
```

### Déploiement Streamlit Cloud

1. Créer un compte sur [streamlit.io](https://streamlit.io)
2. Connecter votre dépôt GitHub
3. Déployer l'application

---

## 📖 Guide d'utilisation

### 1. Saisie de la facture

1. **Libellé** : Identifiant de la facture (optionnel mais recommandé)
2. **Montant TTC** : Montant principal de la facture
3. **Date d'échéance** : Date contractuelle de paiement
4. **Date de paiement** : Date effective du règlement

### 2. Paramètres de calcul

1. **Type de client** :
   - **Privé** : Application automatique de L.441-10 (BCE + 10 pts)
   - **Public** : Application automatique de R.2192-31 (BCE + 8 pts)

2. **Mode de taux** :
   - **Légal** : Taux BCE actualisé automatiquement
   - **Manuel** : Taux contractuel fixe défini par l'utilisateur

### 3. Résultats

Le calcul affiche :
- Détail des intérêts par période (avec taux BCE et majoration)
- Récapitulatif (intérêts + indemnité forfaitaire)
- Montant total à réclamer

### 4. Exports

- **HTML** : Rapport complet avec mise en forme professionnelle
- **CSV** : Données brutes pour intégration comptable

---

## ⚖️ Références légales

### Article L.441-10 du Code de commerce (Clients privés)

> Les pénalités de retard sont exigibles sans qu'un rappel soit nécessaire.
> Le taux des pénalités est égal au taux d'intérêt appliqué par la BCE
> à son opération de refinancement la plus récente majoré de **10 points**.
> Le taux applicable pendant le premier semestre est celui au 1er janvier ;
> pour le second semestre, celui au 1er juillet.

### Article R.2192-31 du Code de la commande publique (Clients publics)

> Le taux des intérêts moratoires est égal au taux BCE majoré de **8 points**.
> Le taux applicable est celui en vigueur au 1er janvier de l'année civile.

### Article D.441-5 du Code de commerce

> Indemnité forfaitaire pour frais de recouvrement : **40 €**

---

## 🏗️ Architecture

```
interets_app/
├── .streamlit/
│   └── config.toml          # Configuration Streamlit
├── assets/
│   ├── logo.png             # Logo Eurovia
│   └── mon_logo.png         # Logo Recouvrement VINCI
├── app.py                   # Application principale
├── requirements.txt         # Dépendances Python
└── README.md                # Documentation
```

---

## 🔧 Configuration

### Variables d'environnement (optionnel)

```bash
# Proxy d'entreprise (si nécessaire)
export HTTPS_PROXY=http://proxy.entreprise.com:8080
export HTTP_PROXY=http://proxy.entreprise.com:8080
```

### Certificat CA entreprise

Pour les réseaux d'entreprise avec inspection TLS, placer le certificat CA dans :
```
interets_app/corporate_ca.pem
```

---

## 📊 Sources des taux BCE

L'application récupère automatiquement les taux MRO (Main Refinancing Operations) depuis :

1. **Source principale** : API BCE (data-api.ecb.europa.eu)
2. **Fallback** : FRED (Federal Reserve Economic Data)

Les données sont mises en cache pendant 1 heure.

---

## 🐛 Dépannage

### Erreur de connexion BCE

```
Vérifiez :
1. Votre connexion internet
2. Les paramètres proxy de votre entreprise
3. Cliquez sur "Rafraîchir les taux" dans la sidebar
```

### Dates invalides

```
Formats acceptés :
- AAAA-MM-JJ (ISO 8601)
- JJ/MM/AAAA (Français)
- JJ-MM-AAAA
```

---

## 📝 Changelog

### v2.0.0 (Janvier 2026)
- ✨ Refonte complète en Streamlit
- 🎨 Design Apple-like
- 📊 Export HTML et CSV
- 🔄 Téléchargement automatique taux BCE
- 📱 Interface responsive

### v1.0.0
- Version initiale (Tkinter)

---

## 👥 Support

Pour toute question ou assistance :
- 📧 Email : support-it@eurovia.com
- 📞 Hotline : [Numéro interne]

---

## 📄 Licence

Application propriétaire — Eurovia / VINCI Construction
Tous droits réservés © 2026
