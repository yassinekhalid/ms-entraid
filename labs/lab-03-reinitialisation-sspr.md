# 🔑 Atelier Pratique 03 : Déploiement de la réinitialisation de mot de passe en libre-service (SSPR)

* **Formation :** Gestion des identités et des accès dans Microsoft Entra ID
* **Formateur :** Yassine KHALID
* **Durée estimée :** 35 minutes
* **Environnement :** [Portail Microsoft Entra (`entra.microsoft.com`)](https://entra.microsoft.com) + Portail SSPR (`aka.ms/ssprsetup`)

---

## 🎯 Contexte et Objectifs

Le support informatique de **Contoso France** reçoit de nombreux appels liés à des oublis de mots de passe. Vous êtes chargé de déployer la fonctionnalité **SSPR (Self-Service Password Reset)** pour le groupe pilote `SG-Equipe-Cloud` afin de rendre les utilisateurs autonomes tout en maintenant un haut niveau de sécurité.

Votre mission consiste à :
1. Activer le SSPR uniquement pour le groupe pilote `SG-Equipe-Cloud`.
2. Exiger **2 méthodes d'authentification** distinctes pour autoriser une réinitialisation.
3. Enregistrer les informations de récupération sur le compte test.
4. Simuler un oubli de mot de passe et vérifier les journaux d'audit.

---

## 📋 Étape 1 : Activer le SSPR pour le groupe pilote

1. Connectez-vous sur [https://entra.microsoft.com](https://entra.microsoft.com).
2. Dans le menu de gauche, accédez à **Identité** > **Utilisateurs** > **Réinitialisation du mot de passe**.
3. Dans l'onglet **Propriétés** :
   * Sous *Réinitialisation de mot de passe en libre-service activée*, sélectionnez **Sélectionné**.
   * Cliquez sur **Aucun groupe sélectionné**, recherchez et choisissez **`SG-Equipe-Cloud`**, puis cliquez sur **Sélectionner**.
4. Cliquez sur **Enregistrer** en haut de la page.

---

## 🛠️ Étape 2 : Configurer les méthodes d'authentification et l'inscription

1. Toujours dans la section **Réinitialisation du mot de passe**, cliquez sur **Méthodes d'authentification** dans le menu de gauche.
2. Configurez les options suivantes :
   * **Nombre de méthodes requises pour la réinitialisation :** Sélectionnez `2`.
   * **Méthodes accessibles aux utilisateurs :** Cochez :
     * `Notification par application mobile`
     * `Adresse de courrier électronique`
3. Cliquez sur **Enregistrer**.
4. Dans le menu de gauche, cliquez sur **Inscription** :
   * Vérifiez que **Exiger des utilisateurs qu'ils s'inscrivent lors de la connexion** est réglé sur **Oui**.
   * Définissez le *Nombre de jours avant que les utilisateurs ne soient invités à reconfirmer leurs informations d'authentification* sur `180`.
5. Cliquez sur **Enregistrer**.
6. *(Facultatif)* Explorez le menu **Notifications** pour activer l'envoi d'un e-mail d'alerte aux utilisateurs lors d'un changement de mot de passe.

---

## 📝 Étape 3 : Enregistrer les méthodes de récupération (Côté utilisateur)

1. Ouvrez une nouvelle **fenêtre de navigation privée** (*InPrivate* ou *Incognito*).
2. Accédez directement au portail d'inscription des informations de sécurité : [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
3. Connectez-vous avec le compte d'**Alex Martin** (`alex.martin@<votre-domaine>`).
4. Dans la page **Informations de sécurité**, vérifiez que **Microsoft Authenticator** est déjà présent (grâce à l'inscription combinée du Lab 2).
5. Cliquez sur **+ Ajouter une méthode de connexion** :
   * Choisissez **Adresse de courrier** dans la liste déroulante, puis cliquez sur **Ajouter**.
   * Saisissez une adresse e-mail secondaire personnelle (⚠️ *ne saisissez jamais l'adresse professionnelle `@onmicrosoft.com` du compte lui-même*).
   * Récupérez le code de vérification reçu par e-mail, saisissez-le et cliquez sur **Suivant**.
6. Fermez la fenêtre de navigation privée.

---

## 🔄 Étape 4 : Simuler un oubli de mot de passe

1. Ouvrez une nouvelle **fenêtre de navigation privée**.
2. Accédez au portail de réinitialisation de mot de passe : [https://passwordreset.microsoftonline.com](https://passwordreset.microsoftonline.com).
3. Saisissez l'identifiant d'**Alex Martin** (`alex.martin@<votre-domaine>`), recopiez les caractères du Captcha, puis cliquez sur **Suivant**.
4. Sélectionnez **J'ai oublié mon mot de passe**, puis cliquez sur **Suivant**.
5. Validez la **première étape de vérification** :
   * Choisissez *Envoyer un message électronique à mon adresse de courrier secondaire*.
   * Saisissez le code reçu par e-mail et cliquez sur **Suivant**.
6. Validez la **seconde étape de vérification** :
   * Choisissez *Approuver une notification sur mon application mobile*.
   * Validez la correspondance numérique sur votre smartphone.
7. Définissez un **nouveau mot de passe** conforme aux règles de complexité et cliquez sur **Terminer**.

---

## ✅ Étape 5 : Contrôler les journaux d'audit

1. Revenez sur votre session administrateur dans le portail **Microsoft Entra**.
2. Accédez à **Identité** > **Supervision et intégrité** > **Journaux d'audit**.
3. Filtrez sur la catégorie **UserManagement** ou recherchez les activités récentes concernant **Alex Martin**.
4. Repérez l'événement **`Reset password (self-service)`** et vérifiez que son statut est **Réussite**.

---

### 🔍 Questions de contrôle
* Pourquoi est-il recommandé d'exiger **2 méthodes** au lieu d'une seule pour la réinitialisation de mot de passe ?
* Quelle fonctionnalité complémentaire est nécessaire si l'entreprise utilise un Active Directory local synchronisé avec Entra ID ?