# 🧭 The North Face — NLP Recommender & Topic Modeling

Projet Data Science visant à booster les conversions e-commerce de **The North Face** grâce à :
1. Un **système de recommandation** basé sur la similarité des descriptions produits.
2. Une **restructuration du catalogue** via **topic modeling** pour révéler de nouvelles catégories de navigation.

## 📖 Contexte

The North Face est une marque américaine spécialisée dans les équipements outdoor.  
Le département marketing souhaite :
- Suggérer automatiquement des produits proches de celui consulté (*"vous pourriez aussi aimer…"*) → **recommender system**.
- Identifier de nouvelles catégories de produits par **topic modeling** → améliorer la navigation du site.

## 🎯 Objectifs

- **Clustering (DBSCAN + cosine)** : grouper les produits avec descriptions proches.
- **Système de recommandation** : proposer 5 articles similaires appartenant au même cluster.
- **Topic Modeling (LSA via TruncatedSVD)** : extraire 10–20 thèmes latents dans les descriptions produits.
- **Visualisation** : générer des **wordclouds** pour interpréter clusters et topics.

## ✅ Résultats attendus

- **Clustering DBSCAN** : formation de ~10–20 groupes de produits cohérents.  
  - Exemple : vestes techniques vs vestes lifestyle, pantalons de trek vs pantalons casual.
  - Les wordclouds par cluster révèlent les mots caractéristiques de chaque groupe.
- **Recommandations** : pour un produit donné, le système retourne 5 produits du même cluster → pertinence contextuelle.
- **Topic Modeling (LSA)** : extraction de 10–20 thèmes latents.  
  - Exemple de topics : *rain, waterproof, jacket* (vêtements imperméables), *hiking, trek, lightweight* (randonnée), *warm, insulated, down* (chauds/doudounes).  
  - Les wordclouds par topic permettent une interprétation qualitative.

👉 Ces résultats permettent de **valider l’approche** et de **challenger la structure du catalogue** actuelle.

## 📊 Interprétation métier

- **Amélioration UX** : navigation plus fluide grâce à des catégories plus naturelles (topics).  
- **Recommandations cross-sell** : suggestion de produits proches → augmentation du panier moyen.  
- **Segmentation produit** : insights pour le marketing (ex. gammes techniques vs lifestyle).  

💡 **Priorité métier** : offrir des recommandations pertinentes tout en limitant la complexité pour l’utilisateur.

## ⚠️ Limites du projet

- **Qualité des descriptions** : dépend fortement du niveau de détail et du vocabulaire marketing.  
- **Paramètres DBSCAN sensibles** : ajustement de `eps` et `min_samples` nécessaire selon le corpus.  
- **Topics LSA** : parfois difficiles à interpréter (mélange de thèmes).  
- **Langue** : projet basé sur l’anglais (spaCy `en_core_web_sm`) → nécessite une adaptation pour le français.

## 🚀 Pistes d’amélioration & Déploiement

1. **Modèles plus avancés**  
   - Utiliser des embeddings contextuels (BERT, Sentence-BERT) au lieu de TF-IDF → meilleure capture du sens.
2. **Recommandations temps réel**  
   - Déployer une API (FastAPI) qui renvoie les produits similaires à un item consulté.
3. **Intégration e-commerce**  
   - Ajouter un bandeau *"Vous pourriez aussi aimer…"*, branché sur le moteur de recommandations.
4. **Monitoring**  
   - Surveiller la répartition des clusters et l’évolution des topics dans le temps (nouveaux produits).
5. **Personnalisation utilisateur**  
   - Combiner historique de navigation + clusters produits → recommandations hybrides.
