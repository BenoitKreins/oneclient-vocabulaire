# Vocabulaire / Woordenschat — journal des changements

## v5.0 — 2026-11-04 (avec l'API OneClient Apps v1.0.1)

**Fichiers à envoyer dans `/outils/vocabulaire/` :**
- `vocabulaire-index-v5.0-2026-11-04.html` → à renommer `index.html` ;
- `vocabulaire-redirect-v5.0-2026-11-04.html` → à renommer `redirect.html` (page de retour de la connexion Microsoft, ne rien y ajouter).

**Mise en ligne par GitHub (à partir de cette version) :** dépôt privé `BenoitKreins/oneclient-vocabulaire`, branche `main`. Hostinger copie le dépôt dans `public_html/outils/vocabulaire` à chaque envoi. Dans le dépôt, les fichiers portent déjà leur nom en ligne (`index.html`, `redirect.html`), et chaque version a son étiquette (`v4.2` … `v5.0`).

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
