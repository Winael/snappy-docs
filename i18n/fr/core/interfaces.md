---
title: "Interfaces"
language: French
---

<!-- lang: EN
Interfaces allow snaps to communicate or share resources according to the
protocol established by the interface.
-->

Les interfaces permettent snaps de communiquer ou de partager des ressources selon le protocole établi par l'interface.

<!-- lang: EN
Each connection has two ends, a "plug" (consumer) and a "slot" (provider).  A
plug and a slot can be connected if they use the same interface name.  The
connection grants necessary permissions for snaps to operate according to the
protocol.
-->

Chaque connexion a deux extrémités, un _"plug"_ (consommateur) et un _"slot"_ (fournisseur). 
Un _plug_ et un _slot_ peuvent être connectés s'ils utilisent le même nom d'interface. 
La connexion accorde les autorisations nécessaires pour que les snaps puissent fonctionner 
selon le protocole.


<img src="https://assets.ubuntu.com/v1/4d5afbf9-Snapcraft-Interfaces-plugs-and-slots.svg" alt="Interfaces - Plugs et Slots" style="width: 80%;"/>


<!-- lang: EN
Slots may support multiple connections to plugs.  For example the core snap
exposes the ``network`` slot and all applications that can talk over the
network connect their plugs there.
-->

Les _slots_ peuvent prendre en charge plusieurs connexions vers des _plugs_. 
Par exemple, le snap de base expose le ``slot network`` et toutes les 
applications qui peuvent parler sur le réseau  y connectent leurs _plugs_.

<!-- lang: EN
The availability of an interface depends on a number of factors and may be
may be provided by the core snap or via snaps providing the slot.  The
available interfaces on a given system can be seen with ``snap interfaces``.
-->

La disponibilité d'une interface dépend d'un certain nombre de facteurs et 
peut être fournie par le snap de base ou par snap fournissant un _slot_. 
Les interfaces disponibles sur un système donné peuvent être vu avec 
``snap interfaces``.

<!-- lang: EN
## Transitional interfaces
-->

## Interfaces transitoires

<!-- lang: EN
Most interfaces are designed for strong application isolation and user control
such that auto-connected interfaces are considered safe and users choose what
applications to trust and to what extent via manually connected interfaces.
-->

La plupart des interfaces sont conçues pour une forte isolation de l'application
un fort contrôle par utilisateur de telle que les interfaces auto-connectés sont 
considérés comme sûrs et les utilisateurs choisissent à quelles applications faire
confiance et dans quelle mesure via les interfaces connectées manuellement.

<!-- lang: EN
Some interfaces are considered transitional to support traditional Linux
desktop environments and these transitional interfaces typically are
auto-connected. Since many of the underlying technologies in these environments
were not designed with strong application isolation in mind, users should only
install applications using these interfaces from trusted sources.  Transitional
interfaces will be deprecated as replacement or modified technologies that
enforce strong application isolation are available.
-->

Certaines interfaces sont considérées comme transitionnelles pour supporter les 
environnements de bureau Linux traditionnels et ces interfaces de transition sont
typiquement auto-connectées. Comme bon nombre des technologies sous-jacentes dans 
ces environnements n'ont pas été conçues avec une isolation applicative forte 
à l'esprit, les utilisateurs doivent installer uniquement des applications utilisant
ces interfaces à partir de sources fiables. Les interfaces transitoires seront 
déconseillées dès que les technologies de remplacement ou les modification qui 
imposent l'isolement fort de l'application seront disponibles.

<!-- lang: EN
## Making connections
-->

## Créer des connexions

<!-- lang: EN
Interfaces may either be auto-connected on install or manually connected after
install.
-->

Les interfaces peuvent être soit auto-connectées lors de l'installation ou 
connectées manuellement après l'installation.

<!-- lang: EN
To list the available connectable interfaces and connections:
-->

Pour lister les interfaces et les connexions connectables disponibles:

    $ snap interfaces

<!-- lang: EN
To make a connection :
-->

Pour créer une connexion :

    $ snap connect <snap>:<plug interface> <snap>:<slot interface>

<!-- lang: EN
To disconnect snaps:
-->

Pour déconnecter des snaps :

    $ snap disconnect <snap>:<plug interface> <snap>:<slot interface>

<!-- lang: EN
Consider a snap ``foo`` that uses ``plugs: [ log-observe ]``. Since
``log-observe`` is not auto-connected, ``foo`` will not have access to the
interface upon install:
-->

Considérons un snap ``foo`` qui utilise ``plugs: [ log-observe ]``. Puisque l'interface ``log-observe`` n'est pas auto-connectée, ``foo`` n'aura pas accès à l'interface lors de son l'installation :

    $ sudo snap install foo
    $ snap interfaces
    Slot                 Plug
    :log-observe         -
    -                    foo:log-observe

<!-- lang: EN
You may manually connect using ``snap connect``:
-->

Vous pourrez manuellement vous y connecter en utilisant ``snap connect`` :

    $ sudo snap connect foo:log-observe core:log-observe
    $ snap interfaces
    Slot                 Plug
    :log-observe         foo:log-observe

<!-- lang: EN
and disconnect using ``snap disconnect``:
-->

et vous déconnecter en utilisant ``snap disconnect`` :

    $ sudo snap disconnect foo:log-observe core:log-observe
    $ snap interfaces # shows they are disconnected
    Slot                 Plug
    :log-observe         -
    -                    foo:log-observe

<!-- lang: EN
On the other hand, ``bar`` could use ``plugs: [ network ]`` and since
``network`` is auto-connected, ``bar`` has access to the interface upon
install:
-->

D'un autre côté, `` bar`` pourrait utiliser ``plugs: [ network ] `` et puisque
``network`` est automatiquement connecté, ``bar`` a accès à l'interface lors 
de l'installation :

    $ sudo snap install bar
    $ snap interfaces
    Slot                 Plug
    :network             bar:network

<!-- lang: EN
You may disconnect an auto-connected interface:
-->

Vous pouvez déconnecter une interface auto-connectée :

    $ sudo snap disconnect bar:network core:network
    $ snap interfaces
    Slot                 Plug
    :network             -
    -                    bar:network

<!-- lang: EN
Whether the slot is provided by the core snap or not doesn't matter in terms of
snap interfaces except that if the slot is provided by a snap, a snap that
implements the slot must be installed for it to be connectable. Eg, the
``bluez`` interface is not provided by the core snap so a snap author
implementing the bluez service might use ``slots: [ bluez ]``. Then after
install, the bluez interface shows up as available:
-->

Que ce soit le _slot_  qui soit fourni par le snap de base ou non, cela n'a pas d'importance en termes d'interfaces de snap sauf si le _slot_ est fourni par un snap, un snap qui implémente un _slot_ doit être installé pour être connectable. Par exemple, l'interface de `` bluez`` n'est pas fourni par le snap de base de sorte qu'un auteur de snap implémentant un service bluez pourrait utiliser `` slots: [bluez]``. Ensuite, après l'installation, l'interface bluez apparaîtrait comme disponible :

    $ sudo snap install foo-blue
    $ snap interfaces
    Slot                 Plug
    foo-blue:bluez       -

<!-- lang: EN
Now install and connect works like before (eg, ``baz`` uses
``plugs: [ bluez ]``):
-->

Maintenant l'installation et la connexion fonctionnent comme avant (ex: ``baz`` utilisent ``plugs: [bluez ]``) :

    $ sudo snap install baz
    $ snap interfaces
    Slot                 Plug
    foo-blue:bluez       -
    -                    baz:bluez
    $ sudo snap connect baz:bluez foo-blue:bluez
    $ snap interfaces
    Slot                 Plug
    foo-blue:bluez       baz:bluez

<!-- lang: EN
## Supported Interfaces
-->

## Interfaces supportées

<!-- lang: EN
A complete list of interfaces is provided in the [Interfaces reference](/docs/reference/interfaces "Interfaces reference"). You can also discover a list of interfaces available on a system and the snaps using them with `snap interfaces` or use the command to get more specific information, including:
-->

Une liste complète des interfaces est fournie dans le [Guide de référence des Interfaces](/docs/reference/interfaces "Guide de Référence des Interfaces"). Vous pouvez également découvrir une liste des interfaces disponibles sur un système et les snaps les utilisant avec `snap interfaces` ou utilisez la commande pour obtenir des informations plus spécifiques, y compris :

<!-- lang: EN
- `snap interfaces <snap>` to find the slots offered and plugs used by the specified snap.
- `snap interfaces <snap>:<slot or plug>` for details of only the specified slot or plug.
- `snap interfaces -i=<interface> [<snap>]` to get a filtered list of  plugs and/or slots.
-->

- `snap interfaces <snap>` pour trouver les _slots_ offerts et les _plugs_ utilisés pas un snap spécifié.
- `snap interfaces <snap>:<slot or plug>` pour plus de détails sur le _slot_ ou le _plug_ spécifié.
- `snap interfaces -i=<interface> [<snap>]` pour obtenir une liste filtrée des _plugs_ et/ou _slots_ disponibles.

<!-- lang: EN
## Creating an interface
-->

## Créer une interfaces

<!-- lang: EN
The OS snap exposes a number of interfaces to grant snaps access to system functions. You can extend this access by creating your own interfaces.
-->

Le snap OS expose un certain nombre d'interfaces pour accorder aux snaps des accès aux fonctions du système. Vous pouvez étendre ces accès en créant vos propres interfaces.

<!-- lang: EN
The following tutorial will show you how: [Your first interface](http://www.zygoon.pl/2016/08/creating-your-first-snappy-interface.html).
-->

Le tutoriel suivant vous expliquera comment faire : [Votre première interface [ENG]](http://www.zygoon.pl/2016/08/creating-your-first-snappy-interface.html).

<!-- lang: EN
### Requesting an interface
-->

## Demander une interface

<!-- lang: EN
You can also file an interface request by [opening an bug report](https://bugs.launchpad.net/snappy/+bugs?field.tag=snapd-interface) with the `snapd-interface` bug tag.
-->

Vous pouvez également déposer une demande d'interface par [l'ouverture d'un rapport de bogue] (https://bugs.launchpad.net/snappy/+bugs?field.tag=snapd-interface) avec le tag de bogue `snapd-interface`.
