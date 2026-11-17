# 🔐 Formation : Gestion des identités et des accès dans Microsoft Entra ID

Bienvenue sur le dépôt officiel des ateliers pratiques de cette journée de formation dédiée à **Microsoft Entra ID** (anciennement Azure Active Directory).

* **Formateur :** Yassine KHALID
* **Durée :** 1 journée (7 heures)
* **Parcours de référence :** [Microsoft Learn — Manage identity and access in Microsoft Entra ID](https://learn.microsoft.com/en-us/training/paths/manage-identity-and-access/)

---

## 🎯 Présentation de la formation

L'objectif de cette journée est de maîtriser les fondamentaux de la gouvernance et de la sécurisation des identités dans le cloud Microsoft. À travers un scénario fil rouge autour de l'entreprise fictive **Contoso France**, chaque notion théorique est immédiatement mise en application via un atelier pratique guidé.

### 🗺️ Programme et Ateliers Pratiques

| Module | Thématique | Atelier Pratique | Durée |
| :--- | :--- | :--- | :---: |
| **Module 01** | Utilisateurs, invités B2B et groupes dynamiques | [Lab 01 — Gestion des utilisateurs et des groupes](./labs/lab-01-utilisateurs-groupes.md) | 30 min |
| **Module 02** | Authentification multifacteur (MFA) et Accès Conditionnel | [Lab 02 — Sécurisation des accès avec le MFA](./labs/lab-02-authentification-mfa.md) | 35 min |
| **Module 03** | Réinitialisation de mot de passe en libre-service (SSPR) | [Lab 03 — Déploiement et test du SSPR](./labs/lab-03-reinitialisation-sspr.md) | 35 min |

---

## 🛠️ Prérequis généraux (Poste stagiaire)

Avant de démarrer le premier atelier, assurez-vous de disposer des éléments suivants :

* **Un navigateur web moderne** (Microsoft Edge ou Google Chrome) avec la possibilité d'ouvrir des **fenêtres de navigation privée** (*InPrivate* / *Incognito*).
* **Un accès au portail d'administration :** [https://entra.microsoft.com](https://entra.microsoft.com).
* **Un compte administrateur de laboratoire** disposant d'un rôle privilégié (idéalement *Administrateur général* / *Global Administrator* sur un locataire de test dédié).
* **Licences du locataire :** Une licence d'évaluation ou active **Microsoft Entra ID P1** (ou P2 / Microsoft 365 E3/E5) est indispensable pour les règles dynamiques, l'Accès Conditionnel et le SSPR ciblé par groupe.

---

## 📋 Prérequis spécifiques par atelier

### 🧪 [Lab 01 : Utilisateurs et Groupes Dynamiques](./labs/lab-01-utilisateurs-groupes.md)
* **Accès portail :** Droit de création d'utilisateurs et de groupes dans Microsoft Entra ID.
* **Adresse e-mail externe :** Disposer d'une adresse e-mail personnelle valide (Gmail, Outlook.com, etc.) pour tester la réception et l'acceptation d'une invitation partenaire **B2B**.
* **Licence :** Entra ID P1 minimum activée sur le locataire pour débloquer l'option *Appartenance dynamique*.

### 🛡️ [Lab 02 : Authentification Multifacteur (MFA) et Accès Conditionnel](./labs/lab-02-authentification-mfa.md)
* **Prérequis Lab 01 :** Le compte utilisateur test (`Alex Martin`) et le groupe dynamique (`SG-Equipe-Cloud`) doivent avoir été créés et peuplés.
* **Smartphone :** Avoir installé l'application mobile gratuite **Microsoft Authenticator** (disponible sur iOS et Android) pour scanner le QR Code d'enrôlement et valider la correspondance numérique.
* **Configuration locataire :** Les *Paramètres de sécurité par défaut* (*Security Defaults*) doivent être **désactivés** afin de pouvoir créer et activer une stratégie d'**Accès Conditionnel**.
* **Sécurité :** Identifier clairement l'UPN de votre compte Administrateur connecté pour l'exclure de la stratégie MFA.

### 🔑 [Lab 03 : Réinitialisation de mot de passe en libre-service (SSPR)](./labs/lab-03-reinitialisation-sspr.md)
* **Prérequis Lab 01 & 02 :** L'utilisateur test `Alex Martin` doit être membre du groupe `SG-Equipe-Cloud` et avoir déjà enregistré **Microsoft Authenticator** sur son compte.
* **Adresse e-mail de récupération :** Disposer d'une adresse e-mail secondaire accessible (différente de l'identifiant professionnel `@onmicrosoft.com` du compte test) pour recevoir le code de vérification à usage unique.

---

## 🔗 Raccourcis utiles pour la journée

* **Portail d'administration Entra ID :** [https://entra.microsoft.com](https://entra.microsoft.com)
* **Portail des applications utilisateur :** [https://myapplications.microsoft.com](https://myapplications.microsoft.com)
* **Inscription des méthodes MFA / SSPR :** [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup)
* **Portail de réinitialisation de mot de passe :** [https://passwordreset.microsoftonline.com](https://passwordreset.microsoftonline.com)