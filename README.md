# Vocabulaire / Woordenschat

Application d'apprentissage du vocabulaire néerlandais (liste Selor, art. 11bis), en ligne sur https://oneclient.be/outils/vocabulaire/.

## Contenu

| Fichier | Rôle |
| --- | --- |
| `index.html` | L'application complète, en un seul fichier (données, styles, scripts, bibliothèque de connexion Microsoft) |
| `redirect.html` | Page de retour de la connexion Microsoft (MSAL). Ne rien y ajouter. |
| `.htaccess` | Empêche la lecture en ligne de `.git`, des fichiers `.md` et `.yml` |
| `CHANGELOG.md` | Journal des changements, une entrée par version |

## Mise en ligne

Hostinger (hPanel > Avancé > Git) copie ce dépôt dans `public_html/outils/vocabulaire` à chaque envoi sur `main`. Chaque version est un commit nommé « Vocabulaire vX.Y » (historique depuis la v4.2). La version en ligne est visible dans le code de la page : `<meta name="app-version">`.

## Synchronisation (à partir de la v5.0)

Facultative. Comptes : Microsoft Entra External ID. Données : API OneClient Apps (dépôt `oneclient-apps-api`) et Azure Cosmos DB, en Belgique.
