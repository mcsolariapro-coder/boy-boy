# 🤖 Bot Discord Professionnel Français

Bot Discord complet avec modération avancée, système de tickets, auto-modération, logs et bien plus encore.

## ✨ Fonctionnalités

### 🔨 Modération
- `+ban` - Bannir un membre avec options avancées
- `+unban` - Débannir un utilisateur
- `+kick` - Expulser un membre
- `+mute` / `+unmute` - Rendre muet / Unmute
- `+warn` - Système d'avertissements cumulatifs
- `+warnings` - Consulter les warns d'un membre
- `+clearwarns` - Effacer les avertissements
- `+clear` - Supprimer des messages (1-100)
- `+slowmode` - Activer le mode lent
- `+lock` / `+unlock` - Verrouiller/déverrouiller un salon
- `+nick` - Modifier le pseudo d'un membre

### 🎫 Système de Tickets
- Panel interactif avec menu déroulant
- Catégories personnalisables (Support, Report, Partenariat, Staff, Question)
- Transcripts automatiques en .txt
- Boutons de contrôle (Fermer, Claim)
- Notifications au staff
- Archives automatiques

### 🤖 Auto-Modération
- **Anti-Spam** : Détecte les messages identiques (3+ en 5s)
- **Anti-Flood** : Messages trop rapides (5+ en 3s)
- **Anti-Raid** : Détection d'arrivées massives (10+ en 10s)
- **Anti-Invites** : Bloque les invitations Discord
- **Anti-Liens** : Option pour bloquer tous les liens
- **Filtre de mots** : Blacklist personnalisable
- **Sanctions automatiques** : 
  - 3 warns → Mute 1h
  - 4 warns → Mute 24h
  - 5 warns → Kick
  - 6+ warns → Ban

### 📋 Système de Logs
- Messages supprimés et édités
- Bannissements / Débannissements
- Arrivées / Départs de membres
- Changements de pseudo et rôles
- Création/suppression de salons
- Création/suppression de rôles

### 👋 Bienvenue & Départ
- Messages personnalisables avec variables :
  - `{user}` - Mention
  - `{user.name}` - Nom
  - `{server}` - Nom du serveur
  - `{membercount}` - Nombre de membres
- DM automatique aux nouveaux
- Attribution automatique de rôles

### 🎭 Auto-Rôles
- Rôles automatiques à l'arrivée
- **Reaction Roles** : Message interactif avec réactions
- Support des émojis personnalisés
- Modes unique ou multiple

### ℹ️ Utilitaire
- `+help` - Menu d'aide complet
- `+userinfo` - Informations sur un membre
- `+serverinfo` - Statistiques du serveur
- `+avatar` - Afficher l'avatar HD
- `+ping` - Latence du bot
- `+botinfo` - Informations du bot
- `+say` - Faire parler le bot
- `+embed` - Créateur d'embeds

## 🚀 Installation

### Prérequis
- Python 3.8 ou supérieur
- Un token de bot Discord

### Étapes

1. **Cloner le projet**
```bash
git clone <votre-repo>
cd bot_discord
```

2. **Installer les dépendances**
```bash
pip install -r requirements.txt
```

3. **Configuration**
```bash
# Copier le fichier d'exemple
cp .env.example .env

# Éditer .env et ajouter votre token
nano .env
```

4. **Lancer le bot**
```bash
python main.py
```

## ⚙️ Configuration Initiale

### 1. Inviter le bot
Utilisez ce lien avec les permissions suivantes :
- Administrator (recommandé) OU
- Manage Server, Manage Roles, Manage Channels, Manage Messages, Ban Members, Kick Members, Moderate Members

### 2. Première configuration
Une fois le bot sur votre serveur, utilisez :
```
/config
```
Pour accéder au panneau de configuration complet.

### 3. Configurer les salons
```
/config logs #salon-logs
/config welcome #bienvenue
/config tickets #tickets
```

### 4. Configurer les messages
```
/setwelcome 🎉 Bienvenue {user} sur {server} !
```

### 5. Créer le panel de tickets
```
/ticket-setup
```

## 📁 Structure du Projet

```
bot_discord/
├── main.py                 # Fichier principal
├── requirements.txt        # Dépendances
├── .env.example           # Exemple de configuration
├── database/
│   └── db.py              # Système de base de données
├── cogs/
│   ├── moderation.py      # Commandes de modération
│   ├── tickets.py         # Système de tickets
│   ├── welcome.py         # Bienvenue/départ
│   ├── autoroles.py       # Auto-rôles
│   ├── utility.py         # Commandes utilitaires
│   ├── automod.py         # Auto-modération
│   ├── logs.py            # Système de logs
│   └── news.py            # News (à développer)
└── data/                  # Données sauvegardées (créé auto)
    ├── config.json
    ├── warnings.json
    ├── tickets.json
    └── ...
```

## 🔧 Commandes Avancées

### Modération
```bash
# Bannir avec suppression de messages
/ban @user raison:"spam" delete_days:7

# Mute temporaire
/mute @user duration:1h raison:"flood"

# Purge ciblée
/clear 50
```

### Tickets
```bash
# Créer le panel
/ticket-setup

# Ajouter quelqu'un à un ticket
/ticket-add @user

# Fermer un ticket
/ticket-close raison:"résolu"
```

### Auto-Rôles
```bash
# Ajouter un rôle auto
/autorole-add @Membre

# Créer un reaction role
/reactionrole title:"Choisissez vos rôles" description:"Réagissez ci-dessous"
/reactionrole-add message_id:123456 emoji:🎮 role:@Gamer
```

## 📊 Base de Données

Le bot utilise JSON pour le stockage (développement). Pour la production, remplacez par PostgreSQL.

Structure des données :
- `warnings.json` - Avertissements
- `config.json` - Configuration des serveurs
- `tickets.json` - Tickets
- `autoroles.json` - Rôles automatiques
- `blacklist.json` - Mots interdits
- `logs.json` - Logs d'événements

## 🛡️ Sécurité

- Rate limiting intégré (5 commandes/10s par utilisateur)
- Vérification de hiérarchie des rôles
- Validation des inputs
- Logs d'erreurs détaillés
- Chiffrement recommandé pour les données sensibles

## 🔄 Mise à Jour

```bash
git pull
pip install -r requirements.txt --upgrade
python main.py
```

## 🐛 Dépannage

### Le bot ne répond pas
1. Vérifiez que le token est correct dans `.env`
2. Assurez-vous que les intents sont activés sur le Discord Developer Portal
3. Vérifiez les permissions du bot sur le serveur

### Les commandes slash n'apparaissent pas
1. Attendez jusqu'à 1 heure (synchronisation Discord)
2. Relancez le bot
3. Vérifiez les permissions `applications.commands`

### Erreurs de permissions
1. Le bot doit avoir un rôle au-dessus des rôles qu'il gère
2. Activez les permissions nécessaires dans les paramètres du serveur

## 📝 Développement

### Ajouter un nouveau module
1. Créer un fichier dans `cogs/`
2. Créer une classe héritant de `commands.Cog`
3. Ajouter `async def setup(bot)` à la fin
4. Le module sera chargé automatiquement au démarrage

Exemple :
```python
from discord.ext import commands

class MonModule(commands.Cog):
    def __init__(self, bot):
        self.bot = bot
    
    @commands.command()
    async def ma_commande(self, ctx):
        await ctx.send("Hello!")

async def setup(bot):
    await bot.add_cog(MonModule(bot))
```

## 🤝 Contribution

Les contributions sont les bienvenues ! N'hésitez pas à :
1. Fork le projet
2. Créer une branche (`git checkout -b feature/NouvelleFonctionnalite`)
3. Commit vos changements (`git commit -m 'Ajout de...'`)
4. Push (`git push origin feature/NouvelleFonctionnalite`)
5. Ouvrir une Pull Request

## 📜 Licence

Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.

## 🆘 Support

Pour obtenir de l'aide :
- Ouvrir une issue sur GitHub
- Rejoindre le serveur Discord de support
- Consulter la documentation

## 🎯 Roadmap

### À venir
- [ ] Système d'XP et de niveaux
- [ ] Économie virtuelle
- [ ] Mini-jeux
- [ ] Intégration API de news (Steam, IGN)
- [ ] Intégration Anime (MyAnimeList)
- [ ] Dashboard web
- [ ] Backup automatique vers le cloud
- [ ] Support multi-langue complet
- [ ] Statistiques avancées
- [ ] IA pour modération avancée

### En développement
- [x] Modération de base
- [x] Système de tickets
- [x] Auto-modération
- [x] Logs complets
- [x] Welcome/Goodbye
- [x] Auto-rôles & Reaction roles

## 💡 Astuces

### Optimisation
- Utilisez un VPS pour héberger 24/7
- Activez le sharding pour >2500 serveurs
- Utilisez PostgreSQL en production
- Configurez des backups automatiques

### Bonnes pratiques
- Configurez les logs dès le début
- Testez sur un serveur de test d'abord
- Sauvegardez régulièrement la base de données
- Utilisez des rôles de staff dédiés

## 🌟 Fonctionnalités Premium (À développer)

- Dashboard web personnalisé
- Statistiques avancées en temps réel
- Backup cloud automatique
- Support prioritaire
- Customisation avancée
- API access

## 📞 Contact

- Discord : [Votre serveur]
- Email : contact@example.com
- GitHub : [Votre profil]

---

**Made with ❤️ in France** 🇫🇷
#   b o y - b o y  
 