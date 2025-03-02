Phi-3-mini WebGPU RAG Chatbot

## Démo pour présenter WebGPU et le modèle RAG
Le modèle RAG avec Phi-3 Onnx Hosted utilise l'approche de génération augmentée par récupération, combinant la puissance des modèles Phi-3 avec l'hébergement ONNX pour des déploiements IA efficaces. Ce modèle est essentiel pour affiner des modèles sur des tâches spécifiques à un domaine, offrant un mélange de qualité, de rentabilité et de compréhension de contexte étendu. Il fait partie de la suite Azure AI, qui propose une large sélection de modèles faciles à trouver, tester et utiliser, répondant aux besoins de personnalisation de diverses industries. Les modèles Phi-3, y compris Phi-3-mini, Phi-3-small et Phi-3-medium, sont disponibles dans le catalogue de modèles Azure AI et peuvent être ajustés et déployés de manière autonome ou via des plateformes comme HuggingFace et ONNX, illustrant l'engagement de Microsoft envers des solutions IA accessibles et efficaces.

## Qu'est-ce que WebGPU 
WebGPU est une API graphique web moderne conçue pour offrir un accès efficace au processeur graphique (GPU) d'un appareil directement depuis les navigateurs web. Elle est destinée à succéder à WebGL, avec plusieurs améliorations clés :

1. **Compatibilité avec les GPU modernes** : WebGPU est conçu pour fonctionner de manière transparente avec les architectures GPU contemporaines, en exploitant des API système comme Vulkan, Metal et Direct3D 12.
2. **Performances améliorées** : Elle prend en charge les calculs généraux sur GPU et des opérations plus rapides, ce qui la rend adaptée aussi bien au rendu graphique qu'aux tâches d'apprentissage automatique.
3. **Fonctionnalités avancées** : WebGPU offre un accès à des capacités GPU plus avancées, permettant des charges de travail graphiques et computationnelles plus complexes et dynamiques.
4. **Réduction de la charge JavaScript** : En déléguant davantage de tâches au GPU, WebGPU réduit considérablement la charge sur JavaScript, offrant de meilleures performances et des expériences plus fluides.

WebGPU est actuellement pris en charge dans des navigateurs comme Google Chrome, avec des travaux en cours pour étendre le support à d'autres plateformes.

### 03.WebGPU
Environnement requis :

**Navigateurs pris en charge :** 
- Google Chrome 113+
- Microsoft Edge 113+
- Safari 18 (macOS 15)
- Firefox Nightly.

### Activer WebGPU :

- Dans Chrome/Microsoft Edge 

Activez le flag `chrome://flags/#enable-unsafe-webgpu`.

#### Ouvrez votre navigateur :
Lancez Google Chrome ou Microsoft Edge.

#### Accédez à la page des flags :
Dans la barre d'adresse, tapez `chrome://flags` et appuyez sur Entrée.

#### Recherchez le flag :
Dans la boîte de recherche en haut de la page, tapez 'enable-unsafe-webgpu'.

#### Activez le flag :
Trouvez le flag #enable-unsafe-webgpu dans la liste des résultats.

Cliquez sur le menu déroulant à côté et sélectionnez Enabled.

#### Redémarrez votre navigateur :

Après avoir activé le flag, vous devrez redémarrer votre navigateur pour que les modifications prennent effet. Cliquez sur le bouton Relancer qui apparaît en bas de la page.

- Pour Linux, lancez le navigateur avec `--enable-features=Vulkan`.
- Safari 18 (macOS 15) a WebGPU activé par défaut.
- Dans Firefox Nightly, entrez about:config dans la barre d'adresse et `set dom.webgpu.enabled to true`.

### Configuration du GPU pour Microsoft Edge 

Voici les étapes pour configurer un GPU haute performance pour Microsoft Edge sous Windows :

- **Ouvrez les paramètres :** Cliquez sur le menu Démarrer et sélectionnez Paramètres.
- **Paramètres système :** Allez dans Système, puis Affichage.
- **Paramètres graphiques :** Faites défiler vers le bas et cliquez sur Paramètres graphiques.
- **Choisissez une application :** Sous « Choisir une application pour définir une préférence », sélectionnez Application de bureau, puis Parcourir.
- **Sélectionnez Edge :** Accédez au dossier d'installation d'Edge (généralement `C:\Program Files (x86)\Microsoft\Edge\Application`) et sélectionnez `msedge.exe`.
- **Définissez la préférence :** Cliquez sur Options, choisissez Haute performance, puis cliquez sur Enregistrer.
Cela garantira que Microsoft Edge utilise votre GPU haute performance pour de meilleures performances.
- **Redémarrez** votre machine pour que ces paramètres prennent effet.

### Ouvrez votre Codespace :
Accédez à votre dépôt sur GitHub.
Cliquez sur le bouton Code et sélectionnez Ouvrir avec Codespaces.

Si vous n'avez pas encore de Codespace, vous pouvez en créer un en cliquant sur Nouveau codespace.

**Remarque** Installation de l'environnement Node dans votre Codespace
Exécuter une démo npm depuis un Codespace GitHub est une excellente façon de tester et développer votre projet. Voici un guide étape par étape pour vous aider à démarrer :

### Configurez votre environnement :
Une fois votre Codespace ouvert, assurez-vous que Node.js et npm sont installés. Vous pouvez vérifier cela en exécutant :
```
node -v
```
```
npm -v
```

S'ils ne sont pas installés, vous pouvez les installer en utilisant :
```
sudo apt-get update
```
```
sudo apt-get install nodejs npm
```

### Accédez à votre répertoire de projet :
Utilisez le terminal pour accéder au répertoire où se trouve votre projet npm :
```
cd path/to/your/project
```

### Installez les dépendances :
Exécutez la commande suivante pour installer toutes les dépendances nécessaires listées dans votre fichier package.json :

```
npm install
```

### Lancez la démo :
Une fois les dépendances installées, vous pouvez exécuter votre script de démonstration. Cela est généralement spécifié dans la section scripts de votre package.json. Par exemple, si votre script de démonstration s'appelle start, vous pouvez exécuter :

```
npm run build
```
```
npm run dev
```

### Accédez à la démo :
Si votre démo implique un serveur web, Codespaces fournira une URL pour y accéder. Cherchez une notification ou consultez l'onglet Ports pour trouver l'URL.

**Remarque :** Le modèle doit être mis en cache dans le navigateur, ce qui peut prendre un certain temps à charger.

### Démo RAG
Téléchargez le fichier markdown `intro_rag.md` to complete the RAG solution. If using codespaces you can download the file located in `01.InferencePhi3/docs/`

### Sélectionnez votre fichier :
Cliquez sur le bouton intitulé « Choisir un fichier » pour sélectionner le document que vous souhaitez télécharger.

### Téléchargez le document :
Après avoir sélectionné votre fichier, cliquez sur le bouton « Télécharger » pour charger votre document pour RAG (génération augmentée par récupération).

### Commencez votre chat :
Une fois le document téléchargé, vous pouvez démarrer une session de chat en utilisant RAG basée sur le contenu de votre document.

**Avertissement** :  
Ce document a été traduit à l'aide de services de traduction automatique basés sur l'intelligence artificielle. Bien que nous nous efforcions d'assurer l'exactitude, veuillez noter que les traductions automatisées peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d'origine doit être considéré comme la source faisant autorité. Pour des informations critiques, il est recommandé de recourir à une traduction professionnelle réalisée par un humain. Nous déclinons toute responsabilité en cas de malentendus ou de mauvaises interprétations résultant de l'utilisation de cette traduction.