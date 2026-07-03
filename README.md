# RND.SHOP

Site vitrine / boutique (Boost Valorant, Émulateur HWID, Unlock All, Comptes NFA).
Reconstruit à partir de la version déployée après reset du PC.

**🌐 En ligne : https://clbsb63-arch.github.io/mon-site/**

## Contenu

| Fichier | Rôle |
|---|---|
| `index.html` | Le site complet (React chargé via CDN, **aucune installation requise**). Contient la config + toute l'application. |
| `style.css` | Feuille de style (identique à l'original). |
| `logo.png` / `logo-emblem.png` | Logos. |
| `robots.txt`, `sitemap.xml` | SEO. |

## Voir le site

- **En local** : double-clique sur `index.html` (une connexion internet est nécessaire, React/Babel sont chargés depuis un CDN).
- **En ligne** : voir « Déployer » ci-dessous.

## Modifier

Tout est dans `index.html` :
- Les **prix**, **rangs**, **produits** : blocs `EMU`, `UNLOCK`, `ACC_PRICE`, `boostPrice` en haut du script.
- Les **textes FR/EN** : objet `T`.
- Le **lien Discord**, le **PayPal** et les **webhooks** : objet `window.RND_CONFIG` (début du 1er `<script>`).

## ⚠️ Sécurité — À FAIRE

Les **webhooks Discord** et le **lien PayPal** sont visibles par n'importe quel visiteur (c'est un site statique, tout le code est public). Ils étaient **déjà exposés** dans l'ancien site.

➡️ **Régénère les 2 webhooks Discord** (Salon → Paramètres → Intégrations → Webhooks → régénérer/supprimer), puis remplace les URLs dans `window.RND_CONFIG` au début de `index.html`. Sinon n'importe qui peut poster dans tes salons.

Pour une vraie sécurité, il faudrait passer les webhooks côté serveur (fonction serverless) — non fait ici car ça sort du cadre d'un site statique.

## Déployer sur Vercel

Site **statique** : aucun build nécessaire.

**Déjà déployé sur GitHub Pages** → https://clbsb63-arch.github.io/mon-site/
Le dépôt `mon-site` est branché sur Pages (source : branche `main`, racine `/`).
**Chaque `git push` sur `main` redéploie automatiquement le site en ~1 minute.**

### Mettre à jour le site
```bash
# depuis le dossier du projet
git add -A
git commit -m "mes modifs"
git push
```

### (Optionnel) Déployer aussi sur Vercel
1. Sur [vercel.com](https://vercel.com) → New Project → importe `clbsb63-arch/mon-site`.
2. Framework Preset « Other » → Deploy. (Permet de récupérer le domaine `rnd-shop.vercel.app`.)
