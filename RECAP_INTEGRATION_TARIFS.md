# Récapitulatif de l'intégration : Page Tarifs & Contrats d'entretien (SEA)

Ce document détaille l'ensemble des travaux réalisés pour la conception, l'intégration Contao et la configuration technique de la nouvelle page **« Tarifs & Contrats d'entretien »** du site *SEA - Énergie Assistance* (Vannes).

---

## 1. Contexte & Objectifs

- **Demande cliente (Élisa - SEA)** :
  - Valoriser les contrats d'entretien avec une structure claire et transparente.
  - Présenter **2 formules uniques** :
    - **Formule Standard** : Visite annuelle réglementaire, nettoyage, vérification de sécurité et attestation officielle.
    - **Formule Confort** (mise en avant comme la formule recommandée) : Visite annuelle + dépannages illimités sous 24 à 48h, main-d'œuvre et déplacement inclus, remise ou pièces d'usure incluses.
  - Proposer des tarifs adaptés selon le type d'équipement via des onglets interactifs.
  - Assumer un positionnement tarifaire premium justifié par la qualité de service et la transparence (4 piliers de réassurance).
  - Fournir un tableau comparatif exhaustif des prestations pour faciliter la décision du client.
  - Répondre aux questions fréquentes (FAQ) pour lever les freins.
  - Humaniser le service en présentant les interlocuteurs clés : **Benoît** (Gérant & Responsable technique) et **Élisa** (Accueil & Relation client).
  - Intégrer un formulaire de devis complet, relié au système de gestion de leads et au Notification Center avec des e-mails HTML chartés.

---

## 2. Configuration Contao & Structure de la page

- **Page Contao** :
  - **ID** : `320`
  - **Titre & Nom** : `Tarifs & Contrats d'entretien`
  - **Alias** : `tarifs` (URL : `http://energie-assistance.test/tarifs`)
  - **Layout** : `35` (Full-Width)
  - **Statut de publication** : `published = 1`
  - **Menu de navigation** : `hide = 1` *(Masquée du menu principal pour le moment, accessible uniquement par son URL directe)*.
- **Article principal** :
  - **ID** : `474` (Article pleine largeur cadré par les wrappers RockSolid Custom Elements).
- **SEO & Structure des titres** :
  - Un seul `<h1>` sur la page (`Tarifs & Contrats d'entretien - SEA` dans le breadcrumb).
  - Les titres des sections sont hiérarchisés en `<h2>` et sous-titres en `<h3>`.

---

## 3. Détail des sections de contenu intégrées

### Section 1 : Introduction & Sélecteur d'onglets tarifaires
- **Éléments Contao** :
  - Wrapper centré (`rsce_client_centered_wrapper_start` ID `6080` / `stop` ID `6093`).
  - Titre de section (`rsce_client_headline_box_custom` ID `6081`) : *« Nos contrats d'entretien »*, sous-titre *« Des formules claires adaptées à vos équipements »*.
  - Sélecteur d'onglets (`rsce_client_tab_nav` ID `6083`) :
    1. **Pompe à chaleur (PAC)** (Air/Eau & Air/Air)
    2. **Chaudière Gaz & Fioul** (Condensation et classique)
    3. **Chauffe-eau & Solaire** (Thermodynamique, électrique et solaire thermique)
  - Tables de prix 2 colonnes (`rsce_client_pricing_table` IDs `6085`, `6088`, `6091`) :
    - Colonne Standard : 149 €/an (PAC) | 139 €/an (Chaudière) | 119 €/an (Chauffe-eau).
    - Colonne Confort (Recommandée, mise en avant visuelle, badge "La plus choisie", CTA principal) : 229 €/an (PAC) | 199 €/an (Chaudière) | 169 €/an (Chauffe-eau).
    - Boutons d'action pointant directement avec une ancre fluide vers `#devis`.

### Section 2 : Les 4 piliers de réassurance ("Pourquoi notre tarif est plus élevé")
- **Éléments Contao** :
  - Wrapper centré (`rsce_client_centered_wrapper_start` ID `6094` / `stop` ID `6098`).
  - Titre de section (`rsce_client_headline_box_custom` ID `6095`).
  - Grille de 4 cartes icônes (`rsce_client_icon_boxes` ID `6097`) :
    1. **Techniciens salariés** (Aucune sous-traitance, techniciens formés et certifiés RGE).
    2. **Visite complète (45 min à 1 h)** (Vérification méthodique des points de contrôle, attestation officielle).
    3. **Pièces d'origine en stock** (Pièces fabricants certifiées dans les véhicules et à l'atelier de Vannes).
    4. **+30 ans sur le bassin de Vannes** (Entreprise locale historique reconnue).
  - Icônes stylisées en blanc pur (`#ffffff` avec font-size `2.5em`).

### Section 3 : Tableau comparatif détaillé des prestations
- **Éléments Contao** :
  - Wrapper centré (`rsce_client_centered_wrapper_start` ID `6099` / `stop` ID `6103`).
  - Titre de section (`rsce_client_headline_box_custom` ID `6100`).
  - Tableau HTML Contao (`ce_table` ID `6101`, classe `.table-comparatif-tarifs`) :
    - 8 lignes comparatives (Visite annuelle, attestation, dépannages illimités, priorité sous 24-48h, main d'œuvre dépannage, déplacement, remise pièces, suivi entretien).
    - Mise en surbrillance de la colonne Confort (fond bleuté subtil, badge "Recommandé", texte bleu accent).
    - Scroll horizontal fluide sur mobile et tablette.
  - Note d'information légale et contractuelle (`ce_text` ID `6102`).

### Section 4 : FAQ en accordéons
- **Éléments Contao** :
  - Wrapper centré (`rsce_client_centered_wrapper_start` ID `6104` / `stop` ID `6111`).
  - Titre de section (`rsce_client_headline_box_custom` ID `6105`).
  - 5 accordéons indépendants (`ce_accordionSingle` IDs `6106` à `6110`) :
    1. *L'entretien annuel de mon équipement est-il obligatoire ?*
    2. *Quelle est la différence entre la formule Standard et Confort ?*
    3. *Intervenez-vous sur toutes les marques ?*
    4. *Sous quel délai intervenez-vous en cas de panne avec le contrat Confort ?*
    5. *Comment souscrire à un contrat d'entretien ?*
  - Centrage horizontal cadré (`max-width: 900px; margin: 0 auto;`).

### Section 5 : Processus & Présentation de Benoît
- **Éléments Contao** :
  - Wrapper centré (`rsce_client_centered_wrapper_start` ID `6112` / `stop` ID `6116`).
  - Titre de section (`rsce_client_headline_box_custom` ID `6113`) : *« Comment se déroule votre souscription ? »*.
  - Boîte de présentation de **Benoît** (`rsce_client_team_boxes` ID `6114`, classe `.team-box-benoit`) avec photo ronde, badge Gérant & Responsable technique, et citation sur l'engagement qualité de SEA.
  - Timeline en 4 étapes (`rsce_client_timeline` ID `6115`, classe `.timeline-contrats`) :
    - Étape 1 : Demande en ligne ou par téléphone
    - Étape 2 : Devis clair & sans surprise
    - Étape 3 : Visite d'entretien approfondie
    - Étape 4 : Suivi annuel & sérénité

### Section 6 : Demande de devis & Présentation d'Élisa
- **Éléments Contao** :
  - Wrapper centré avec ID d'ancrage (`rsce_client_centered_wrapper_start` ID `6117` avec CSS ID `#devis` / `stop` ID `6121`).
  - Titre de section (`rsce_client_headline_box_custom` ID `6118`) : *« Demandez votre devis personnalisé »*.
  - Boîte de présentation d'**Élisa** (`rsce_client_team_boxes` ID `6119`, classe `.team-box-elisa`) : photo ronde, rôle « Accueil, Conseils & Relation Client SEA Vannes » et message d'accueil rassurant.
  - Formulaire de demande de devis (`form` ID `6120`, classe `.form-devis-wrapper`).

---

## 4. Configuration du Formulaire de Devis & Gestion des Leads

- **Formulaire Contao** : `tl_form` ID `5` (alias `demande-devis-entretien`).
- **Champs de formulaire (`tl_form_field`)** :
  - `formule` (Select obligatoire) : Choix entre Formule Confort (Recommandée) et Formule Standard.
  - `appareil_type` (Select obligatoire) : PAC, Chaudière gaz, Chaudière fioul, Chauffe-eau, Solaire, Autre.
  - `appareil_marque` (Text) : Marque de l'équipement (ex: Saunier Duval, Daikin, Atlantic...).
  - `appareil_age` (Text) : Année ou âge approximatif de l'installation.
  - `name` (Text obligatoire) : Nom et prénom du prospect.
  - `email` (Text obligatoire, validation e-mail).
  - `phone` (Text obligatoire, validation téléphone).
  - `address` (Text obligatoire) : Adresse de l'installation.
  - `postal_city` (Text obligatoire) : Code postal et ville.
  - `message` (Textarea facultatif) : Précisions supplémentaires.
  - `date` (Hidden) : `{{date::d/m/Y H:i}}` pour horodatage automatique.
  - `website_url` (Text, classe `honeyshow`) : Sécurité antispam silencieuse honeypot.
  - Bouton submit stylisé : *« Demander mon devis gratuit »*.
- **Intégration Contao Leads (terminal42/contao-leads)** :
  - `leadEnabled = 1`
  - `leadStore = 1` sur l'ensemble des champs de données utiles.
  - **Nom du menu dans le back-office** : `Demandes de devis entretien`.
  - **Record label (`leadLabel`) complet** :
    ```
    ##date## - ##name## - ##phone## - ##email## - ##formule## - ##appareil_type## - ##appareil_marque## - ##postal_city## - ##message##
    ```

---

## 5. Notification Center : Templates d'e-mails dédiés

Deux notifications distinctes sont désormais en place, utilisant la passerelle **Mailjet** (`tl_nc_gateway` ID `1`) :

### A. Notification Devis Entretien (`tl_nc_notification` ID `4`)
1. **Alerte Admin (Message ID 3)** :
   - **Destinataire** : `contact@energie-assistance.fr`
   - **Copie cachée (BCC)** : `contact@bioweb.fr`
   - **Reply-To** : `##form_email##` (permet de répondre directement au prospect)
   - **Objet** : `{{page::rootTitle}} - Demande de devis contrat entretien - ##form_name##`
   - **Contenu** : Template HTML responsive avec le logo SEA, tableau récapitulatif détaillé de l'équipement (formule choisie, appareil, marque, âge), coordonnées complètes de l'installation et message complémentaire.
2. **Accusé de réception Client (Message ID 4)** :
   - **Destinataire** : `##form_email##`
   - **Expéditeur** : `{{page::rootTitle}} - SEA` (`contact@energie-assistance.fr`)
   - **Objet** : `{{page::rootTitle}} - Votre demande de devis d'entretien a bien été reçue`
   - **Contenu** : Message chaleureux et personnalisé au nom du client, récapitulant sa sélection, annonçant la prise en charge par Élisa sous 24 à 48h ouvrées, avec rappel des coordonnées téléphoniques directes de l'agence de Vannes (`02 97 40 50 17`).

### B. Notification Formulaire de Contact général (`tl_nc_notification` ID `3`)
- **Mise à niveau complète** :
  - **Admin (Message ID 1)** : Passage à la nouvelle charte HTML avec logo SEA, bandeau d'alerte, coordonnées structurées, message dans un bloc propre, et `Reply-To` configuré sur `##form_email##`.
  - **Client (Message ID 2)** : Accusé de réception graphique personnalisé rappelant le message transmis, rassurant sur la prise en charge rapide par l'agence de Vannes et fournissant les coordonnées directes de l'entreprise.

---

## 6. Intégration SCSS & Compilation Compass

- **Fichier modifié** : Uniquement `files/client/scss/client.scss`.
- **Règles de compatibilité Ruby Sass 3.4.25** :
  - Utilisation de codes hexadécimaux et valeurs explicites (évitement des fonctions Sass complexes sur des variables non typées pouvant lever l'erreur `String can't be coerced into Integer`).
  - Compilation exécutée avec succès (`compass compile files/client/scss/`).
- **Nouveaux blocs de style ajoutés** :
  - `.table-comparatif-tarifs` (Tableau comparatif, zebra hover, styles de cellules, badges).
  - `.faq-accordion-item` (Accordéons FAQ centrés et aérés).
  - `.team-box-benoit` & `.team-box-elisa` (Cartes de présentation d'équipe, photos circulaires bordées de bleu SEA `#0d89c7`, typographie soignée).
  - `.timeline-contrats` (Mise en page de la chronologie en 4 étapes).
  - `.form-devis-wrapper` / `.form-devis-tarifs` (Formulaire sur 2 colonnes avec inputs stylisés, focus bleu SEA et bouton d'action orange `#f69323`).

---

## 7. URL d'accès direct & Statut

- **Lien de prévisualisation locale** : [http://energie-assistance.test/tarifs](http://energie-assistance.test/tarifs)
- **Lien direct vers la section devis** : [http://energie-assistance.test/tarifs#devis](http://energie-assistance.test/tarifs#devis)
- **Menu** : Actuellement masquée (`hide = 1`), accessible uniquement via l'URL ci-dessus.
- **Git** : Aucun commit ni push n'a été effectué conformément à la consigne.
