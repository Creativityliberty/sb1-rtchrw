# Document de déploiement : Flash Africa

## 1. Procédures de déploiement

### 1.1 Déploiement du frontend (Next.js)
1. Exécuter les tests automatisés
2. Construire l'application : `npm run build`
3. Déployer sur Vercel :
   - Connecter le repository GitHub à Vercel
   - Configurer les variables d'environnement
   - Déclencher le déploiement via l'interface Vercel ou un push sur la branche principale

### 1.2 Déploiement du backend (Supabase)
1. Appliquer les migrations de base de données : `supabase db push`
2. Déployer les fonctions serverless : `supabase functions deploy`
3. Mettre à jour les règles de sécurité : `supabase db remote commit`

### 1.3 Configuration de Mux pour le streaming
1. Créer un nouveau environnement Mux si nécessaire
2. Configurer les webhooks Mux pour les événements de streaming
3. Mettre à jour les clés API Mux dans les variables d'environnement

### 1.4 Configuration des systèmes de paiement
1. Mettre à jour les clés API Stripe dans les variables d'environnement
2. Configurer les webhooks Stripe pour les événements de paiement
3. Tester les intégrations de paiement mobile africaines dans l'environnement de staging

## 2. Configuration des environnements

### 2.1 Environnement de développement
- URL : dev.flashafrica.com
- Base de données : instance Supabase de développement
- Variables d'environnement : fichier .env.development

### 2.2 Environnement de staging
- URL : staging.flashafrica.com
- Base de données : instance Supabase de staging
- Variables d'environnement : fichier .env.staging

### 2.3 Environnement de production
- URL : www.flashafrica.com
- Base de données : instance Supabase de production
- Variables d'environnement : gérées via l'interface Vercel

### 2.4 Gestion des secrets
- Utiliser Vercel pour stocker les secrets de production
- Utiliser un gestionnaire de secrets local (comme dotenv) pour le développement

## 3. Procédure de rollback

1. Identifier la dernière version stable connue
2. Restaurer le code source à cette version dans le repository
3. Déclencher un nouveau déploiement sur Vercel
4. Restaurer la base de données à partir de la dernière sauvegarde si nécessaire
5. Vérifier le bon fonctionnement de l'application après le rollback

## 4. Monitoring post-déploiement

1. Surveiller les logs d'erreur via Vercel et Supabase
2. Vérifier les métriques de performance (temps de chargement, utilisation des ressources)
3. Surveiller les taux de conversion et d'engagement des utilisateurs
4. Effectuer des tests manuels des fonctionnalités critiques