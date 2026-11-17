# 🛡️ Atelier Pratique 02 : Sécurisation des accès avec le MFA et l'Accès Conditionnel

* **Formation :** Gestion des identités et des accès dans Microsoft Entra ID
* **Formateur :** Yassine KHALID
* **Durée estimée :** 35 minutes
* **Environnement :** [Portail Microsoft Entra (`entra.microsoft.com`)](https://entra.microsoft.com) + Smartphone (App Microsoft Authenticator)

---

## 🎯 Contexte et Objectifs

Pour protéger **Contoso France** contre le vol d'identifiants et le phishing, la direction informatique impose l'authentification multifacteur (MFA) pour tous les membres de l'équipe Cloud.

Votre mission consiste à :
1. Vérifier et activer la méthode **Microsoft Authenticator** avec correspondance numérique.
2. Créer une stratégie d'**Accès Conditionnel** ciblant l'équipe Cloud tout en protégeant votre compte administrateur.
3. Tester l'enrôlement et l'expérience de connexion en tant qu'utilisateur final.

> 🚨 **ATTENTION — CONSIGNE DE SÉCURITÉ CRITIQUE :**  
> Lors de la création de la stratégie d'Accès Conditionnel, veillez à **exclure impérativement votre compte Administrateur connecté** afin d'éviter tout blocage de votre session d'administration.

---

## 📋 Étape 1 : Configurer la stratégie de méthodes d'authentification

1. Connectez-vous sur [https://entra.microsoft.com](https://entra.microsoft.com).
2. Dans le menu de gauche, accédez à **Protection** > **Méthodes d'authentification** > **Stratégies**.
3. Cliquez sur **Microsoft Authenticator**.
4. Sous l'onglet **Activer et cibler** :
   * Basculez le bouton **Activer** sur **Oui**.
   * Sélectionnez **Tous les utilisateurs** (ou ciblez uniquement le groupe `SG-Equipe-Cloud`).
5. Sous l'onglet **Configurer**, vérifiez que l'option **Exiger la correspondance de numéros pour les notifications Push** est définie sur **Activé** (par défaut géré par Microsoft).
6. Cliquez sur **Enregistrer**.

---

## 🔐 Étape 2 : Créer une stratégie d'Accès Conditionnel

1. Dans le menu de gauche, accédez à **Protection** > **Accès conditionnel** > **Stratégies**.
2. Cliquez sur **Nouvelle stratégie**.
3. Donnez un nom explicite à la stratégie : `CA-Exiger-MFA-Equipe-Cloud`.
4. Sous **Affectations**, cliquez sur **Utilisateurs** :
   * **Inclure :** Sélectionnez *Sélectionner des utilisateurs et des groupes* > Cochez **Utilisateurs et groupes** > Recherchez et sélectionnez **`SG-Equipe-Cloud`**.
   * **Exclure (⚠️ OBLIGATOIRE) :** Cliquez sur l'onglet **Exclure** > Cochez **Utilisateurs et groupes** > Recherchez et sélectionnez **votre propre compte Administrateur** connecté actuellement.
5. Sous **Ressources cibles**, cliquez sur **Aucune ressource cible sélectionnée** :
   * **Inclure :** Sélectionnez **Toutes les applications cloud** (acceptez l'avertissement affiché).
6. Sous **Contrôles d'accès**, cliquez sur **Accorder** :
   * Sélectionnez **Accorder l'accès**.
   * Cochez la case **Exiger l'authentification multifacteur**.
   * Cliquez sur **Sélectionner** en bas du panneau.
7. En bas de la page, basculez l'état de la stratégie de *Rapport uniquement* sur **Activé**.
8. Cliquez sur **Créer**.

---

## 📱 Étape 3 : Enrôler et tester l'expérience utilisateur

1. Ouvrez une **fenêtre de navigation privée** (*InPrivate* ou *Incognito*) sur votre navigateur.
2. Rendez-vous sur le portail des applications : [https://myapplications.microsoft.com](https://myapplications.microsoft.com).
3. Connectez-vous avec le compte d'**Alex Martin** (`alex.martin@<votre-domaine>`).
   * *Si demandé, mettez à jour son mot de passe temporaire.*
4. Un écran s'affiche avec le message : **"Plus d'informations sont requises"** (votre organisation a besoin de plus d'informations pour assurer la sécurité de votre compte). Cliquez sur **Suivant**.
5. Sur votre smartphone, ouvrez l'application **Microsoft Authenticator** :
   * Appuyez sur **+** (Ajouter un compte) > **Compte professionnel ou scolaire** > **Scanner un code QR**.
   * Suivez les instructions à l'écran sur votre ordinateur pour afficher le QR Code et scannez-le.
6. Validez la notification de test en saisissant le **numéro à 2 chiffres** affiché sur votre écran d'ordinateur.
7. Terminez l'assistant jusqu'à accéder au portail **Mes applications**.

---

## ✅ Étape 4 : Vérification dans les journaux de connexion

1. Revenez sur votre session administrateur dans le portail **Microsoft Entra**.
2. Accédez à **Identité** > **Supervision et intégrité** > **Journaux de connexion**.
3. Recherchez la connexion récente d'**Alex Martin** et cliquez dessus.
4. Consultez les onglets suivants dans le volet de détails :
   * **Détails de l'authentification :** Vérifiez que l'exigence MFA a été satisfaite via *Notification d'application mobile*.
   * **Accès conditionnel :** Vérifiez que la stratégie `CA-Exiger-MFA-Equipe-Cloud` apparaît avec le statut **Réussite**.

---

### 🔍 Questions de contrôle
* Pourquoi la correspondance numérique (*Number Matching*) protège-t-elle contre les attaques par fatigue MFA (*MFA Fatigue*) ?
* Quelle est la différence majeure entre les *Paramètres de sécurité par défaut* et l'*Accès Conditionnel* ?