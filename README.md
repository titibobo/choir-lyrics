# Fiches de chant

Atelier de rédaction des fiches de paroles de la chorale. Les rédacteurs y écrivent une feuille par voix, et l'atelier produit les PDF à envoyer aux choristes.

- **La page** (`index.html`) est hébergée sur GitHub Pages.
- **Les feuilles** sont rangées dans un Google Sheet, par l'Apps Script `Code.gs`.
- **Chaque rédacteur** a son propre code, géré dans l'onglet « Rédacteurs » du Sheet.

## Mise en place (une seule fois, environ 15 minutes)

### 1. Le Google Sheet et son script

1. Sur ton compte Google, crée un Google Sheet vide nommé **Fiches de chant**.
2. Ouvre le menu **Extensions → Apps Script**.
3. Efface le contenu de `Code.gs`, colle à la place le contenu du fichier `Code.gs` fourni, puis enregistre (icône disquette).
4. En haut, choisis la fonction **setup** dans la liste, puis clique sur **Exécuter**.
   - Google demande une autorisation. Choisis ton compte. Si l'écran « Google n'a pas validé cette application » apparaît, clique sur **Paramètres avancés → Accéder à … (non sécurisé)**, puis **Autoriser**. C'est normal pour un script personnel.
5. Reviens au Sheet. Trois onglets sont apparus :
   - **Feuilles**, avec les trois chants repris du carnet ;
   - **Rédacteurs**, avec un code pour Thibault et un pour Clairie ;
   - **Corbeille**.

### 2. Publier le script

1. Dans Apps Script, ouvre **Déployer → Nouveau déploiement**.
2. Clique sur la roue dentée et choisis le type **Application Web**.
3. Règle **Exécuter en tant que : Moi** et **Qui a accès : Tout le monde**.
   - « Tout le monde » est nécessaire pour que la page GitHub puisse joindre le script. Sans code valable, le script refuse tout : il ne lit ni n'écrit rien.
4. Clique sur **Déployer**, puis copie l'**URL de l'application Web**. Elle se termine par `/exec`.

### 3. La page sur GitHub

1. Ouvre `index.html` dans un éditeur de texte. Vers le haut, remplace la ligne

   ```js
   var ADRESSE_SERVICE = '';
   ```

   par la même ligne avec l'URL copiée entre les apostrophes.
2. Sur GitHub, crée un dépôt, par exemple `fiches-chant`, puis dépose-y `index.html` et ce `README.md` (**Add file → Upload files**).
   - Ne mets pas `Code.gs` sur GitHub : il n'est utile que dans Apps Script.
3. Dans le dépôt, ouvre **Settings → Pages**. Sous **Source**, choisis **Deploy from a branch**, puis la branche `main` et le dossier `/ (root)`, et enregistre.
4. Après une minute, l'atelier est en ligne à l'adresse `https://<ton-compte>.github.io/fiches-chant/`.

### 4. Donner les accès

- Envoie à Clairie l'adresse de l'atelier et son code, qui est dans l'onglet **Rédacteurs**.
- **Ajouter un rédacteur :** ajoute une ligne dans cet onglet, avec un nom et un code de ton choix.
- **Retirer un rédacteur :** supprime sa ligne. Son code cesse de fonctionner aussitôt.

## Au quotidien

- **Enregistrement :** il se fait tout seul quelques secondes après la dernière frappe. `Ctrl+S` force l'enregistrement.
- **Voix manquantes :** dans la liste, les pupitres pas encore rédigés (Graves, Medium graves, Medium aigus, Aigus) apparaissent en pointillés. Un clic crée la feuille à partir d'une feuille existante du chant.
- **Pupitre divisé :** « Diviser en Aigus 1 et Aigus 2 » (ou le menu **Division**) donne une feuille à chaque division.
- **Validation :** « Valider la transcription » marque la feuille comme relue, avec le nom de la personne et la date, et un ✓ apparaît dans la liste. Toute modification du texte retire la validation. Un simple changement de titre la conserve.
- **Une feuille par voix :** les pastilles « Créer à partir de cette feuille » recopient le texte vers une autre voix. Il ne reste qu'à ajuster les passages `H:`.
- **Export PDF :** clique sur **PDF de cette voix** ou **PDF de toutes les voix**, puis choisis **Enregistrer au format PDF** dans la fenêtre d'impression.
  - Utilise Chrome ou Edge.
  - Dans « Plus de paramètres », décoche **En-têtes et pieds de page** et coche **Graphiques d'arrière-plan**, sinon le surligné disparaît.
- **Format :** le format A4 ajuste seul la taille du texte et le nombre de colonnes pour tenir sur le moins de pages possible. Le format **Téléphone** produit des pages étroites en gros caractères, à lire sur portable.
- **Récupérer une feuille supprimée :** elle est dans l'onglet **Corbeille**. Recopie sa ligne dans l'onglet **Feuilles**.
- **Modifications simultanées :** si deux personnes modifient la même feuille en même temps, rien n'est écrasé. L'atelier demande quelle version garder.

## Modifier le script plus tard

Après une modification de `Code.gs`, ouvre **Déployer → Gérer les déploiements**, clique sur le crayon, choisis **Version : Nouvelle version**, puis **Déployer**. L'URL ne change pas, donc il n'y a rien à modifier sur GitHub.
