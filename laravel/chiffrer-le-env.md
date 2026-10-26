# Chiffrer le fichier .env pour le mettre dans un dépôt

**Le problème.** Le fichier `.env` contient les mots de passe et les clés d'API : il ne doit jamais aller dans Git. Mais sans lui, impossible de relancer le projet sur une autre machine.

**La solution.** Laravel sait chiffrer son propre fichier d'environnement :

```bash
php artisan env:encrypt
```

Cela crée `.env.encrypted`, qui peut aller dans le dépôt, et affiche une clé. La clé se range dans un gestionnaire de mots de passe, jamais dans le dépôt.

Pour retrouver le `.env` sur une autre machine :

```bash
php artisan env:decrypt --key=base64:...
```

Sans la clé, le fichier chiffré est illisible.
