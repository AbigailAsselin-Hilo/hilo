# 🤝 Contribuer  

Rapporter tout problème est une excellente manière pour tous de contribuer au projet.  

Si vous rencontrez des problèmes ou observez des comportements étranges, veuillez soumettre une "Issue" en y joignant vos journaux.  

## 📜 Activer la journalisation de débogage  
Pour activer la journalisation de débogage, ajoutez ceci dans votre fichier `configuration.yaml` :  

```yaml
logger:
  default: info
  logs:
    custom_components.hilo: debug
    pyhilo: debug
```

Si vous avez de l'expérience en Python ou avec Home Assistant et souhaitez contribuer au code, n'hésitez pas à soumettre une pull request.  

---

# 🛠️ Préparer un environnement de développement via VSCode DevContainer  

Pour faciliter le développement, un environnement est disponible via DevContainer de VSCode. Assurez-vous d'avoir **VSCode** et **Docker** installés sur votre ordinateur.  

1. Ouvrez le dossier du projet dans VSCode.  
2. Installez l'extension **Remote - Containers**.  
3. Ouvrez la palette de commandes (**Ctrl+Shift+P** ou **Cmd+Shift+P**) et recherchez :  
   ```
   Remote-Containers: Reopen in Container
   ```
4. Attendez que l'environnement soit prêt.  
5. Ouvrez un terminal dans VSCode et exécutez :  
   ```bash
   scripts/develop
   ```
   pour installer les dépendances et lancer Home Assistant.  
6. VSCode devrait vous proposer d'ouvrir un navigateur pour accéder à Home Assistant. Sinon, ouvrez manuellement :  
   ```
   http://localhost:8123
   ```
7. Effectuez la configuration initiale de Home Assistant.  
8. Ajoutez l'intégration **Hilo** via l'interface utilisateur.  
9. Modifiez les fichiers dans le dossier `custom_components/hilo` et observez les changements en temps réel dans Home Assistant.  

Dans le terminal où vous avez lancé `scripts/develop`, les journaux de Home Assistant et de l'intégration Hilo devraient défiler.  

---

# ✅ Avant de soumettre une Pull Request  

Il est essentiel de tester vos modifications sur une installation locale. Vous pouvez modifier les fichiers `.py` de l'intégration directement dans votre dossier `custom_components/hilo`.  

⚠ **N'oubliez pas votre copie de sauvegarde!**  

Si vous devez modifier `python-hilo` pour vos tests, installez votre fork avec la commande suivante dans votre CLI :  

```bash
pip install -e git+https://github.com/VOTRE_FORK_ICI/python-hilo.git#egg=python-hilo
```

Redémarrez ensuite Home Assistant pour que l'installation prenne effet. Pour revenir en arrière :  

```bash
pip install python-hilo
```

Puis redémarrez Home Assistant.  

---

# 🚀 Soumettre une Pull Request  

1. **Créez un fork** du dépôt dans votre espace utilisateur.  
2. **Clonez-le** sur votre ordinateur.  
3. Pour maintenir une certaine standardisation du code, nous utilisons des **linters** et des **validateurs** exécutés via des hooks `pre-commit` :  

   ```bash
   pre-commit install --install-hooks
   ```

4. Apportez vos modifications au code.  
5. Une fois terminé, ajoutez les fichiers modifiés :  

   ```bash
   git add path/to/file
   ```

6. Créez un commit :  

   ```bash
   git commit -m "J'ai changé ceci parce que ..."
   ```

7. Poussez les changements vers votre dépôt distant :  

   ```bash
   git push
   ```

8. Sur le dépôt d'origine, **GitHub** devrait vous proposer de créer une **Pull Request** (PR). Suivez les instructions.  
