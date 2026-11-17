# 🧪 Atelier Pratique 01 : Gestion des utilisateurs et des groupes dynamiques

* **Formation :** Gestion des identités et des accès dans Microsoft Entra ID
* **Formateur :** Yassine KHALID
* **Durée estimée :** 30 minutes
* **Environnement :** [Portail Microsoft Entra (`entra.microsoft.com`)](https://entra.microsoft.com)

---

## 🎯 Contexte et Objectifs

Vous êtes administrateur des identités pour l'entreprise **Contoso France**. Le département **Cloud** (ou *Marketing* selon votre groupe de travail) accueille de nouveaux collaborateurs ainsi qu'un auditeur externe. 

Votre mission consiste à :
1. Créer un compte utilisateur interne avec les bons attributs métier.
2. Automatiser l'attribution des accès via un **groupe de sécurité dynamique**.
3. Inviter un prestataire externe (B2B) avec des droits restreints.
4. Contrôler le bon fonctionnement de l'automatisation.

---

## 📋 Étape 1 : Créer un utilisateur interne

1. Connectez-vous au portail d'administration : [https://entra.microsoft.com](https://entra.microsoft.com).
2. Dans le menu de gauche, accédez à **Identité** > **Utilisateurs** > **Tous les utilisateurs**.
3. Cliquez sur **Nouvel utilisateur** > **Créer un nouvel utilisateur**.
4. Dans l'onglet **De base**, renseignez les informations suivantes :
   * **Nom d'utilisateur principal (UPN) :** `alex.martin` *(conservez le domaine par défaut de votre locataire)*
   * **Nom d'affichage :** `Alex Martin`
   * **Mot de passe :** Décochez *Générer automatiquement un mot de passe* et définissez un mot de passe temporaire que vous noterez soigneusement.
5. Passez à l'onglet **Propriétés** et descendez jusqu'à la section **Informations sur l'emploi** :
   * **Titre du poste :** `Ingénieur Cloud`
   * **Service (Department) :** `Cloud` *(⚠️ Respectez exactement la casse)*
6. Cliquez sur **Revoir + créer**, puis sur **Créer**.

> 💡 *Optionnel (Bonus) :* Explorez le menu **Opérations en bloc > Création en bloc** pour télécharger le modèle CSV d'importation en masse.

---

## ⚙️ Étape 2 : Créer un groupe de sécurité dynamique

1. Dans le menu de gauche, accédez à **Identité** > **Groupes** > **Tous les groupes**.
2. Cliquez sur **Nouveau groupe**.
3. Configurez les paramètres généraux du groupe :
   * **Type de groupe :** `Sécurité`
   * **Nom du groupe :** `SG-Equipe-Cloud`
   * **Description du groupe :** `Groupe dynamique rassemblant tous les collaborateurs du service Cloud`
   * **Type d'appartenance :** `Utilisateur dynamique`
4. Cliquez sur **Ajouter une requête dynamique**.
5. Dans l'éditeur de règles, configurez la condition suivante :
   * **Propriété :** `department`
   * **Opérateur :** `Equals`
   * **Valeur :** `Cloud`
6. *(Facultatif)* Cliquez sur l'onglet **Valider les règles (en préversion)**, ajoutez **Alex Martin** et cliquez sur **Valider** pour tester votre syntaxe.
7. Cliquez sur **Enregistrer** en haut de la page, puis sur **Créer**.

---

## 🤝 Étape 3 : Inviter un utilisateur externe (Entra B2B)

1. Retournez dans **Identité** > **Utilisateurs** > **Tous les utilisateurs**.
2. Cliquez sur **Nouvel utilisateur** > **Inviter un utilisateur externe**.
3. Renseignez les informations de l'auditeur externe :
   * **Adresse de courrier :** Utilisez une adresse e-mail personnelle valide à laquelle vous avez accès (ex: Gmail, Outlook.com) pour pouvoir tester l'invitation.
   * **Nom d'affichage :** `Auditeur Externe`
   * **Message d'invitation :** `Bienvenue sur l'espace collaboratif de Contoso France.`
4. Dans l'onglet **Affectations**, cliquez sur **Ajouter un rôle** et attribuez le rôle **Lecteur global** (*Global Reader*).
5. Cliquez sur **Revoir + inviter**, puis sur **Inviter**.

---

## ✅ Étape 4 : Vérification et Validation

1. Accédez à **Identité** > **Groupes** > **Tous les groupes**, puis ouvrez le groupe **`SG-Equipe-Cloud`**.
2. Cliquez sur **Membres** dans le menu de gauche du groupe.
3. Vérifiez qu'**Alex Martin** apparaît automatiquement dans la liste.
   * *Note : Le moteur d'évaluation dynamique de Microsoft Entra ID peut prendre entre **2 et 5 minutes** pour traiter la règle. Actualisez la page si nécessaire.*
4. Consultez l'onglet **Historique du traitement dynamique** pour observer l'état de la dernière évaluation.
5. Vérifiez votre boîte mail personnelle pour constater la réception de l'invitation B2B.

---

### 🔍 Questions de contrôle
* Pourquoi l'utilisateur `Auditeur Externe` n'a-t-il pas été ajouté automatiquement au groupe `SG-Equipe-Cloud` ?
* Quelle licence minimale est requise dans Microsoft Entra ID pour utiliser les groupes dynamiques ?