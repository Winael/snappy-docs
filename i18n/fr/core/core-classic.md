---
title: "Ubuntu Core et Classique"
language: french
---


<!-- lang: EN
## What is Ubuntu Core?
-->

## Qu'est-ce qu'Ubuntu Core ?

<!-- lang: EN
Ubuntu Core is a lightweight, transactionally updated OS for devices targeted at the Internet of Things (IoT) space. It consists of a minimal `rootfs` and key services such as network. All other user features are added by installing additional snaps into a snapd system or device. In simple terms, it can be thought of as the smallest version of Ubuntu needed to support a system.
-->

Ubuntu Core est un OS léger transactionnellement mise à jour pour des périphériques ciblés pour l'espace de l'Internet des Objets (IdO). Il se compose d'un `rootfs` minime et de services clés tels que le réseau. Toutes les autres caractéristiques de l'utilisateur sont ajoutés en installant des snaps supplémentaires dans un système snapd ou périphérique. En termes simples, il peut être considéré comme la plus petite version d'Ubuntu nécessaire pour supporter un système.

<!-- lang: EN
Practical implementations of Ubuntu Core in a snapd system consist of:
-->

L'implémentation pratique d'Ubuntu Core dans un système snapd consiste en :

<!-- lang: EN
- Kernel snap
- Gadget snap
- OS snap
-->

- Un snap Kernel
- Des snaps Gadget
- Un snap OS

<!-- lang: EN
Ubuntu Core is delivered in the OS snap (see [Kinds of Snaps](/docs/core/snaps "Kinds of Snaps") for more details on these and the other types of snaps). 
-->

Ubuntu Core est livré dans le snap OS (voir [Types de Snaps] (/docs/core/snaps "Type de Snaps») pour plus de détails sur ces questions et les autres types de snaps).

<!-- lang: EN
## Differences to Ubuntu Classic
-->

## Différences avec Ubuntu Classique

<!-- lang: EN
Ubuntu Core diverges from the standard model of server and desktop Ubuntu distributions (Ubuntu Classic), the key differences are summarized in the table below:
-->

Ubuntu Core diverge du modèle standard de distributions Ubuntu Serveur et de Bureau (Ubuntu Classic), les principales différences sont résumées dans le tableau ci-dessous :

<!-- lang: EN
Ubuntu Classic | Ubuntu Core
:---- | :----
The base rootfs and kernel are delivered as a monolithic package that doesn't enable transactional updates. | OS and kernel delivered as separate snaps, offering transactional updates.
Can be both a development and target platform. | Acts as a target platform only.
Applications delivered in DEB packages or as snaps. | Applications delivered as snaps.
The rootfs file system can be written to and therefore could be tampered with. | The rootfs file system is read only, preventing tampering.
-->

Ubuntu Classique | Ubuntu Core
:---- | :----
Les rootfs de base et le noyau sont livrés comme un ensemble monolithique qui ne permet pas les mises à jour transactionnelles . | L'OS et le noyau sont livrés en snaps distincts, offrant des mises à jour transactionnelles.
Peut être à la fois une plateforme de développement et une plateforme cible. | Agit comme une plate-forme cible seulement.
Les applications sont livrées en paquets DEB ou en snaps. | Les applications sont livrées en snaps.
Le système de fichier rootfs peut être écrit et peut donc être altéré. | Le système de fichiers rootfs est en lecture seule, ce qui empêche la falsification.
 
<!-- lang: EN
## Release cycles
-->

## Cycles de publication

<!-- lang: EN
New versions of Ubuntu Core will be released every two years, with each release being referred to as a "series" suffixed with the release year. For example, the current release is Series 16 and the next will be Series 18. 
-->

Les nouvelles versions de Ubuntu Core seront publiées tous les deux ans, chaque version étant designée comme une «série» suffixé avec l'année de sortie. Par exemple, la version actuelle est la série 16 et la prochaine sera de la série 18.

