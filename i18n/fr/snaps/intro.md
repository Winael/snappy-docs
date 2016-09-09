---
title: "Qu'est-ce qu'un snap?"
---

<!-- lang: EN
A `snap` :

* is a squashFS filesystem containing your app code and a `snap.yaml` file containing specific metadata. It has a read-only file-system and, once installed, a writable area.

* is self-contained. It bundles most of the libraries and runtimes it needs and can be updated and reverted without affecting the rest of the system.

* is confined from the OS and other apps through security mechanisms, but can exchange content and functions with other snaps according to fine-grained policies controlled by the user and the OS defaults.
-->

Un `snap` :

* est un système de fichiers squashfs contenant le code de votre application et un fichier `snap.yaml` contenant des métadonnées spécifiques. Il dispose d'un système de fichiers en lecture seule et, une fois installé, d'une zone inscriptible.

* est autonome. Il regroupe la plupart des bibliothèques et moteurs d'exécution dont il a besoin et peut être mis à jour ou remis en arrière sans affecter le reste du système.

* est confiné par rapport au système d'exploitation et aux autres applications grâce à des mécanismes de sécurité, mais il peut échanger du contenus et des fonctions avec d'autres snaps en fonction des politiques bien précises contrôlées par l'utilisateur et les paramètres par défaut du système d'exploitation
