````md id="lab14storage"
# LAB 14 — Sauvegarde des Données Android

![Android](https://img.shields.io/badge/Platform-Android-green)
![Java](https://img.shields.io/badge/Language-Java-orange)
![Security](https://img.shields.io/badge/Focus-Mobile%20Security-blue)

## 📌 Description

Ce laboratoire présente les mécanismes de persistance locale Android avec :

- SharedPreferences
- EncryptedSharedPreferences
- Internal Storage
- Cache
- External Storage

Objectif :
sauvegarder des données localement en appliquant les bonnes pratiques de sécurité.

---

# 🎯 Objectifs

- stocker des préférences utilisateur ;
- sécuriser les données sensibles ;
- manipuler les fichiers internes ;
- utiliser le cache Android ;
- comprendre le stockage externe.

---

# ⚙️ Prérequis

- Android Studio
- Java
- Android SDK
- Connaissances Android basiques

---

# 🚀 Tâche 1 — Création du Projet

Créer :

```text id="k3x7mn"
Empty Activity
Language: Java
````
<img width="489" height="1024" alt="image" src="https://github.com/user-attachments/assets/c6d31140-3ea9-4439-8c05-b3a449561e2b" />


---

# 📱 Tâche 2 — SharedPreferences

Écriture :

```java id="u7p2qa"
SharedPreferences prefs =
getSharedPreferences("app", MODE_PRIVATE);

prefs.edit()
.putString("theme","dark")
.apply();
```

Lecture :

```java id="m8v4rd"
String theme =
prefs.getString("theme","light");
```

---

# 🔐 Tâche 3 — EncryptedSharedPreferences

Dépendance :

```gradle id="r2q9lx"
implementation "androidx.security:security-crypto:1.1.0-alpha06"
```

Exemple :

```java id="x5m1pt"
EncryptedSharedPreferences.create(
"secure_prefs",
masterKeyAlias,
context,
EncryptedSharedPreferences.PrefKeyEncryptionScheme.AES256_SIV,
EncryptedSharedPreferences.PrefValueEncryptionScheme.AES256_GCM
);
```

---

# 📂 Tâche 4 — Internal Storage

Écriture fichier :

```java id="n6v8yk"
FileOutputStream fos =
openFileOutput("data.txt", MODE_PRIVATE);

fos.write("Hello".getBytes());

fos.close();
```

---

# 🗄 Tâche 5 — Cache Android

Créer cache :

```java id="w1r5qs"
File cacheFile =
new File(getCacheDir(), "temp.txt");
```

---

# 💾 Tâche 6 — External Storage

Exemple :

```java id="j4m7vn"
File file =
new File(
getExternalFilesDir(null),
"backup.txt"
);
```

---

# 🔥 Bonnes Pratiques Sécurité

* éviter les secrets en clair ;
* utiliser le chiffrement ;
* nettoyer le cache ;
* limiter les logs ;
* protéger les fichiers sensibles.

---

# ✅ Checklist Sécurité

* [x] données chiffrées
* [x] cache nettoyé
* [x] permissions minimales
* [x] logs contrôlés
* [x] stockage sécurisé

---

# 📚 Concepts Appris

* SharedPreferences
* Encrypted Storage
* Internal Storage
* Cache Management
* Android Security

---

# ⚠️ Remarque

Ne jamais stocker :

* mots de passe
* tokens
* clés API

en clair dans l’application.

---

# 👨‍💻 Auteur

Ayoub Laafar — EMSI Marrakech

```
```
