# Vocabulaire / Woordenschat — journal des changements

## v5.2.1 — 2026-11-05

**Mise en ligne :** par GitHub (dépôt `oneclient-vocabulaire`), seul `index.html` change.

- Correction (présente depuis la v5.0) : la liste créée d'office au premier lancement (« Mes termes prioritaires ») n'était jamais envoyée en ligne, même après y avoir ajouté des termes. Sur un deuxième appareil, ces termes arrivaient sans leur liste et se retrouvaient rangés dans une autre liste. Cette liste est maintenant synchronisée dès son premier terme (et reste locale tant qu'elle est vide).
- Testé par l'interface : création d'une liste, ajout d'un terme par le formulaire (y compris depuis la liste B1–B2 affichée, le terme va alors dans une liste personnelle), import par lot, modification d'un terme B1–B2, duplication de la liste B1–B2 (263 termes, modification conservée), renommage et suppression d'une liste, puis réception de l'ensemble sur un deuxième appareil.
- Version visible dans le fichier : `<meta name="app-version" content="Vocabulaire 5.2.1 — 2026-11-05">` et `APP_VERSION = "5.2.1"`.

## v5.2 — 2026-11-04

**Mise en ligne :** par GitHub (dépôt `oneclient-vocabulaire`), seul `index.html` change.
**API :** aucun changement (v1.2.0).

- Nouvelle liste intégrée « Vocabulaire courant B1–B2 » (NL : « Algemene woordenschat B1–B2 ») : 263 termes, à côté du syllabus 11bis.
  - Noms avec leur article (de/het), traduction française avec article, une phrase d'exemple en néerlandais et sa traduction française, une catégorie (Travail, Santé, Économie…).
  - Liste relue à partir de la liste fournie (268 lignes) : 5 doublons retirés (ervaring, invloed, uitzondering, advies, veiligheid). Articles corrigés : *het* succes, *het* recept. Corrections : de pijn (au lieu de « de pijnen »), mislukken (au lieu de « misbreken »), vaag (au lieu de « vage »), « Iedere burger », « volgende maand ». Mots néerlandais retirés de la traduction française (« le spectacle », « le contrat », « le moyen », « le rassemblement », « les dégâts », « les environs »). Catégories traduites en français. Toutes les phrases d'exemple ont maintenant leur traduction française.
  - Comme pour le syllabus : un terme peut être masqué ou modifié pour soi (synchronisé), et la liste peut être dupliquée pour en faire une liste personnelle. Chacun peut ajouter ses propres termes dans ses listes personnelles.
  - Badge de carte « B1–B2 · catégorie », source « Liste B1–B2 — n° ».
- Les termes masqués et le bouton « Restaurer » sont comptés par liste intégrée.
- Adresse e-mail de contact retirée de la page Compte. Le message affiché si la suppression du compte est indisponible ne renvoie plus vers une adresse.
- Version visible dans le fichier : `<meta name="app-version" content="Vocabulaire 5.2 — 2026-11-04">` et `APP_VERSION = "5.2"`.

## v5.1 — 2026-11-04 (avec l'API OneClient Apps v1.2.0)

**Mise en ligne :** par GitHub (dépôt `oneclient-vocabulaire`), seul `index.html` change.

- Nouveau bouton « Supprimer mon compte » (Réglages > Compte) : efface les données en ligne et le compte de connexion Microsoft (adresse e-mail et mot de passe). Avant, il fallait écrire à l'adresse de contact. La copie de l'appareil est conservée et l'application repasse en mode local.
- « Supprimer mes données en ligne » reste disponible pour effacer les données sans fermer le compte.
- Si la suppression du compte n'est pas encore active côté serveur, un message le dit et renvoie vers l'adresse de contact.
- Reprend le réveil de l'API de la v5.0.4.
- Version visible dans le fichier : `<meta name="app-version" content="Vocabulaire 5.1 — 2026-11-04">` et `APP_VERSION = "5.1"`.

## v5.0.4 — 2026-11-04

**Mise en ligne :** par GitHub (dépôt `oneclient-vocabulaire`), seul `index.html` change.

- Envoi des codes depuis no-reply@oneclient.be plus fiable : l'application « réveille » l'API (appel à `/api/health`) à l'ouverture de la page Compte et au clic sur « Activer la synchronisation » ou « Se reconnecter ». Quand Entra demande ensuite à l'API d'envoyer le code (inscription, mot de passe oublié), elle a eu le temps de démarrer. Sans réveil, un démarrage à froid dépassait les 2 secondes accordées par Entra, et le code partait depuis l'adresse Microsoft.
- Au plus un réveil toutes les 2 minutes. La requête part même si la page est quittée juste après (keepalive). Aucun coût supplémentaire notable.
- Alternative évaluée et écartée pour l'instant : une instance toujours prête (environ 6,6 $ par mois à 512 Mo, 26 $ à 2048 Mo, calculateur Azure du 4 novembre 2026).
- Version visible dans le fichier : `<meta name="app-version" content="Vocabulaire 5.0.4 — 2026-11-04">` et `APP_VERSION = "5.0.4"`.

## v5.0.3 — 2026-11-04

**Mise en ligne :** par GitHub (dépôt `oneclient-vocabulaire`), seul `index.html` change.

- Langue de la page Microsoft : l'application envoie maintenant le code complet et le marché (`ui_locales=nl-NL&mkt=nl-NL`, ou `fr-FR`), comme dans la documentation d'Entra External ID. Avec le code court (`nl`), la page s'affichait dans la langue du navigateur.
- Version visible dans le fichier : `<meta name="app-version" content="Vocabulaire 5.0.3 — 2026-11-04">` et `APP_VERSION = "5.0.3"`.

## v5.0.2 — 2026-11-04

**Mise en ligne :** par GitHub (dépôt `oneclient-vocabulaire`), seul `index.html` change.
**Supabase / Azure :** aucun changement.

- Correction : « Activer la synchronisation » échouait avec `endpoints_resolution_error`. La bibliothèque de connexion Microsoft (MSAL 5) vérifie que l'émetteur annoncé par l'annuaire correspond à l'adresse de connexion configurée. L'annuaire externe annonce un émetteur basé sur son identifiant (`https://<ID>.ciamlogin.com/<ID>/v2.0`), qui ne correspondait pas à l'adresse configurée par son nom (`oneclientapps.onmicrosoft.com`). L'adresse de connexion utilise maintenant l'ID de l'annuaire.
- Version visible dans le fichier : `<meta name="app-version" content="Vocabulaire 5.0.2 — 2026-11-04">` et `APP_VERSION = "5.0.2"`.

## v5.0.1 — 2026-11-04

**Mise en ligne :** par GitHub (dépôt `oneclient-vocabulaire`), seul `index.html` change. `redirect.html` reste en v5.0.
**Supabase / Azure :** aucun changement.

- Correction : « Activer la synchronisation » attend la fin de l'initialisation de la connexion Microsoft. Avant, un clic trop rapide après l'ouverture de la page affichait « Impossible d'initialiser la connexion au serveur ».
- Diagnostic : si la connexion Microsoft ne s'initialise vraiment pas, le message affiche maintenant le code de l'erreur entre parenthèses (par exemple `endpoints_resolution_error` quand la page Microsoft est injoignable ou bloquée par le navigateur).
- Même chose pour le bouton « Se reconnecter ».
- Version visible dans le fichier : `<meta name="app-version" content="Vocabulaire 5.0.1 — 2026-11-04">` et `APP_VERSION = "5.0.1"`.

## v5.0 — 2026-11-04 (avec l'API OneClient Apps v1.0.1)

**Fichiers à envoyer dans `/outils/vocabulaire/` :**
- `vocabulaire-index-v5.0-2026-11-04.html` → à renommer `index.html` ;
- `vocabulaire-redirect-v5.0-2026-11-04.html` → à renommer `redirect.html` (page de retour de la connexion Microsoft, ne rien y ajouter).

**Mise en ligne par GitHub (à partir de cette version) :** dépôt privé `BenoitKreins/oneclient-vocabulaire`, branche `main`. Hostinger copie le dépôt dans `public_html/outils/vocabulaire` à chaque envoi. Dans le dépôt, les fichiers portent déjà leur nom en ligne (`index.html`, `redirect.html`), et chaque version est un commit nommé « Vocabulaire vX.Y » (historique depuis la v4.2).

**Supabase :** aucun changement. L'application ne l'utilise plus (arrêt prévu en phase 7).
**Azure :** l'API `oneclient-apps-api` v1.0.1 doit être en ligne (`/api/health`).

- Mode local par défaut : plus d'écran de connexion au démarrage, aucun compte n'est nécessaire pour apprendre.
- Synchronisation facultative : Réglages > Compte > « Activer la synchronisation ». Une page Microsoft (Entra External ID) s'ouvre pour créer un compte ou se connecter avec un e-mail et un mot de passe, dans la langue de l'application.
- Données en ligne enregistrées dans Azure Cosmos DB (Belgique), via l'API OneClient Apps. Plus de Supabase.
- À la première activation, tout ce qui est sur l'appareil est envoyé vers le compte. Sur un appareil vide, tout est récupéré.
- Synchronisation par lot : les changements sont envoyés environ une seconde après la modification (nouvel essai toutes les 30 secondes hors connexion). Les changements des autres appareils sont récupérés toutes les minutes quand la page est visible, et à chaque retour sur la page. Bouton « Synchroniser maintenant ».
- État visible : point de couleur et texte (synchronisé, en attente, hors ligne, reconnexion nécessaire, erreur).
- Protection contre le changement de compte : si un autre compte se connecte sur le même appareil, l'application demande confirmation avant de mélanger les données.
- « Se déconnecter » arrête la synchronisation et garde les données sur l'appareil.
- « Supprimer mes données en ligne » efface tout ce qui est enregistré en ligne pour ce compte, sur tous les appareils, et garde la copie de l'appareil. Le compte Microsoft reste ouvert (suppression sur demande à l'adresse de contact, automatisée en phase 6).
- Mot de passe oublié : géré par la page Microsoft (« Mot de passe oublié ? »).
- Reprise automatique de la v4 : les données Supabase déjà présentes dans ce navigateur (progression, listes, termes, réglages) sont reprises en local au premier lancement. Les anciens jetons de connexion Supabase sont effacés.
- Une liste par défaut vide créée automatiquement n'est pas envoyée en ligne. Elle est retirée si le compte a déjà ses listes (plus de liste en double sur un nouvel appareil).
- Adresse de contact affichée en permanence dans Réglages > Compte.
- Version visible dans le fichier : `<meta name="app-version" content="Vocabulaire 5.0 — 2026-11-04">` et `APP_VERSION = "5.0"`.

## v4.4 — 2026-10-31 (avec la fonction send-email v2.0)

**Fichiers à envoyer :**
- `vocabulaire-index-v4.4-2026-10-31.html` → à renommer `index.html` dans `/outils/vocabulaire/` ;
- `vocabulaire-send-email-v2.0-2026-10-31.ts` → à coller dans Supabase, fonction `send-email`, fichier `index.ts`, puis déployer.

**Base de données Supabase :** aucun changement.

- Liens des e-mails (mot de passe oublié, confirmation d'inscription, changement d'adresse) : ils pointent maintenant vers l'application sur oneclient.be au lieu d'une adresse supabase.co. L'application vérifie elle-même le lien.
- Sécurité : la fonction n'accepte comme destination du lien que l'adresse de l'application (APP_URL). Les autres adresses sont ignorées.
- Le jeton est retiré de la barre d'adresse dès l'ouverture de la page.
- Un lien déjà utilisé ou expiré affiche « Ce lien n'est plus valable… » (FR) / « Deze link is niet meer geldig… » (NL).
- Le lien n'est consommé que quand la page s'exécute dans le navigateur. Avant, un simple chargement de l'adresse par un antivirus de messagerie pouvait l'utiliser.

## v4.3 — 2026-10-31

**Fichier à envoyer :** `vocabulaire-index-v4.3-2026-10-31.html` → à renommer `index.html` à la mise en ligne.
**Base de données Supabase :** aucun changement.

- Icônes de son : les émoticônes 🔊 sont remplacées par l'icône plate (haut-parleur), la même que sur la carte :
  - bouton « Écouter la réponse » au verso de la carte ;
  - boutons d'écoute devant les exemples (indice et verso) ;
  - boutons « Tester la voix NL / FR » dans Réglages > Audio.
- Info-bulle des boutons d'exemple : « Écouter » (FR) / « Beluisteren » (NL), au lieu de l'émoticône.
- Version visible dans le fichier : balise `<meta name="app-version">` en tête, et `APP_VERSION = "4.3"`.
- Inchangé : les icônes du menu et des onglets des réglages restent en émoticônes (dont 🔊 Audio).

## v4.2 — dernière version livrée avant ce journal

**Fichier :** `en-ligne/index.html`.
Synchronisation Supabase multi-appareils, limite de 1 000 termes par liste, pages plein écran, page « Méthode Leitner », bouton « Supprimer mon compte », langue du compte enregistrée (FR/NL).
