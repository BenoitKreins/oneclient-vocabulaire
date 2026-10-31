# Vocabulaire / Woordenschat — journal des changements

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
