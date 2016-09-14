---
title: Le système snapd
language: French
---

<!-- lang: EN
In traditional Linux distributions, software is made available in packages:
-->

Dans les distributions traditionnelles Linux, le logiciel est mis à disposition au travers de paquets :

<!-- lang: EN
- that rely on the availability of services in the OS or other software.
- whose data isn't confined, so can be accessed by other software.
- that can be detrimentally effected by a system or software upgrade.
- that are complex to uninstall or downgrade.
- rely on a small number of approved 'packagers' to add them to the distro repositories.
-->

- Qui comptent sur la disponibilité des services dans le système d'exploitation ou d'autres logiciels.
- Dont les données ne sont pas confinées, et peuvent donc être accessibles par d'autres logiciels.
- Qui peut être préjudiciablement effectuée par une mise à niveau du système ou du logiciel.
- Qui sont complexes à désinstaller ou de rétrograder.
- Qui s'appuient sur un petit nombre d'« empaqueteurs » approuvés pour les ajouter aux référentiels des distributions.

<!-- lang: EN
Creating and distributing software can therefore be a time consuming process and the end result doesn't offer the user a high degree of security and manageability.
-->

Créer et distribuer des logiciels peut donc être un processus long et le résultat final ne propose pas à l'utilisateur un degré élevé de sécurité et de gestion.

<!-- lang: EN
The snapd system aims to fix these challenges by offering:
-->

Le système snapd vise à résoudre ces défis en offrant :

<!-- lang: EN
- System components and applications as self contained (except for the most basic OS features, such as network access), read only images, called snaps.
- A confinement and security model that:

  - Offers snaps a secure storage area isolated from other snaps.
  - Enables snaps to make features available to other snaps and for other snaps to consume those features over defined interfaces.
  - A store where developers can easily make their software directly available to users and from which devices can automatically pull updates on a daily basis.

- A simple transactional update system where snaps can be easily uninstalled (by deleting the snap package) or rolled back (by reverting to the previous snap image and private storage area).
-->

- Des composants du système et des applications en tant qu'images autonome (sauf pour les caractéristiques du système d'exploitation les plus élémentaires, tels que l'accès au réseau), en lecture-seule uniquement, appelées snaps.
- Un confinement et modèle de sécurité qui :

  - Offre aux snaps une zone de stockage sécurisée et isolée des autres snaps.
  - Permet aux snaps de rendre des fonctionnalités disponibles à d'autres snaps et aux autres snaps de consommer ces fonctionnalités sur des interfaces définies.
  - Offre un magasin où les développeurs peuvent facilement mettre leur logiciel directement à la disposition des utilisateurs et à partir duquel les périphériques peuvent charger automatiquement des mises à jour sur une base quotidienne.

- Un système de mises-à-jour transactionnelles simple où les snaps peuvent être facilement être désinstallés (en supprimant le snaps) ou annulés (en revenant à l'image précédente du snaps et la zone de stockage privée).

<!-- lang: EN
On a snapd system these features are implemented by:
-->

Sur un système snapd ces caractéristiques sont mises en œuvre par :

<!-- lang: EN
- **snapd**, a management environment that handles installing and updating snaps using the transactional system, as well as [garbage collection](/docs/core/versions) of old versions of snaps.
- **snapd-confine**, an execution environment for the applications and services delivered in snap packages.
-->

- **snapd**, un environnement de gestion qui gère l'installation et la mise à jour des snaps en utilisant le système transactionnel, ainsi que [la collecte des ordures](/docs/core/versions) des anciennes versions des snaps.
- **snapd-confine**, un environnement d'exécution pour les applications et les services offerts dans les paquets snaps.

<!-- lang: EN
![Snaps are self contained, confined applications that can make use of features in other snaps using Interfaces.](../media/snap_in_snappy_system.png "Snaps in the Snapd System")
-->

![Les snaps sont des applications autonomes et confinése qui peuvent utiliser des fonctionalités d'autres snaps en utilisant des interfaces.](../../media/snap_in_snappy_system.png "Les snaps dans le système snapd")

<!-- lang: EN
The snapd system simplifies the development of devices and their software because, with the exception of a limited number of OS features, you're in control of all the components in your application. You simply add everything needed to the snap package. You then make the snap available using [the store](/docs/core/store "the store"), or, if you are the device creator, create your own store.
-->

Le système de snapd simplifie le développement des dispositifs et de leurs logiciels, car, à l'exception d'un nombre limité de fonctionnalités du système d'exploitation, vous avez le contrôle de tous les composants de votre application. Il suffit d'ajouter tout ce qui est nécessaire dans le paquet snap. Vous rendez ensuite le snap disponible en utilisant [le magasin](/docs/core/magasin "Le magasin"), ou, si vous êtes le concepteur de l'appareil, en créant votre propre magasin.

<!-- lang: EN
## OS snaps
-->

## Les snaps OS

<!-- lang: EN
The OS snap is a repacked `rootfs` that contains just 'enough' to run and manage snaps on a read-only file system. Generally there will also be basic features such as network services, libc, systemd, and others included.
-->

Le snap OS est un `rootfs` ré-empaqueté qui contient juste « assez » pour pouvoir exécuter et gérer des snaps sur un système de fichiers en lecture seule. En général, il y aura aussi des fonctionnalités basiques telles que les services réseau, libc, systemd et d'autres inclus.

<!-- lang: EN
When you install a snap for the first time, the OS snap (`ubuntu-core`) gets installed first, it's used as the platform for subsequently installed application snaps. This way, you can be confident that a snap always runs on the same core stack, regardless of the Linux distribution.
-->

Lorsque vous installez un snap pour la première fois, le snap OS (`ubuntu-core`) est installé en premier lieu, il est utilisé comme plate-forme pour les snaps applicatives installées par la suite. De cette façon, vous pouvez être sûr qu'un snap fonctionne toujours sur la même pile de base, quelle que soit la distribution Linux.
