---
title: "Fichier YAML de métadonnées"
---


<!-- lang: EN
Snaps, when they are installed or manually created (eg. without using the `snapcraft` command) are defined by a set of metadata specified in `meta/snap.yaml`:
-->

Les snaps, lorsqu'ils sont installés ou manuellement créés (par exemple, sans utiliser la commande `snapcraft`.), sont définis par un ensemble de métadonnées spécifié dans dans le fichier `meta/snap.yaml`.

<!-- lang: EN
## Purpose of snap.yaml
-->

## Objectif du fichier `snap.yaml`

<!-- lang: EN
This file describes the snap package and is essential for defining the content and usable features of the snap. 
-->

Ce fichier décrit le paquet snap et est essentiel pour définir le contenu et les fonctionnalités utilisables du snap.

<!-- lang: EN
## Keys used in the snap.yaml 
-->

## Mot-clés utilisés dans le fichier `snap.yaml`

<!-- lang: EN
Key | Required | Description 
:---- | ---- | :---- 
<code>name</code> | Yes | The name of the snap. The name may use any combination of lower case letters and numbers plus the '-' character but must start with a letter.
<code>version</code> | Yes | The version of the snap. The version can be defined with any combination of upper and lower case letters, number and the '.', '+', '~', and '-' characters.
<code>summary</code> | No | A short summary of the snap.
<code>description</code> | No | A long description of the snap.
<code>license-agreement</code> | No | Set to `explicit` if the user needs to accept the content of the `meta/license.txt` file before the snap can be installed.
<code>license-version</code> | No | A string defining the version of the licence text. When its value changes and `license-agreement` is `explicit` it causes the user to be prompted to accept the content of `meta/license.txt` again.
<code>type</code> | No |  The type of the snap, can be:  `app`, the default if `type` is omitted or empty; or `gadget`, a special snap that Gadgets can use to customize snappy for their hardware.
<code>architectures</code> | No | A YAML list of supported architectures,  defaults to  `["all"]` if omitted or empty.
<code>apps</code> | No | The map of apps (binaries and services) that a snap provides.
<code>&nbsp;&nbsp;&nbsp;&lt;app name></code> | Yes | The name of the app or service.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;command</code> | Yes |The command to start the application or service.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;daemon</code>| Yes | The type of daemon that will run the application (as a service): `simple`, `forking`, `oneshot`, or `dbus`
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;stop-command</code> | No |  The command to stop the service.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;stop-timeout</code> | No |  The time in seconds to wait for the service to stop
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;restart-condition</code> | No |  Specifies the restart       condition. Can be one of `on-failure` (default), `never`, `on-success`,       `on-abnormal`, `on-abort`,  and `always`. See `systemd.service(5)` (search for `Restart=`) for details.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;post-stop-command</code> | No |  A command that runs after the service has stopped.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;slots</code> | No | A map of interfaces.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ports</code> | No |  Defines which ports the service will work.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;internal</code> | Yes | The ports the service will to connect to.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tagname</code> | Yes | A free form name.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port</code> | No |  Number/protocol, for example `80/tcp`.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;negotiable</code> | No |  `Y` if the app can use a different port.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;external</code> | Yes | The ports the service offers to the world.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tagname</code> | Yes | A free form name, some names have meaning like "ui".
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port</code> | No |  Number/protocol, for example `80/tcp`.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;negotiable</code> | No |  `Y` if the app can use a different port.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;socket</code> | No |  Set to `true` if the service is socket activated. Must be specified with `listen-stream`.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;listen-stream</code> | No |  The full path of the stream socket or an abstract socket. When specifying an absolute path, it should normally be in one of the app-specific writable directories. <br />When specifying an abstract socket, it must start with `@` and typically be followed by either the snap package name or the snap package name followed by `\_` and any other characters, for example  `@name` or `@name\_something`.
-->

Mot-Clé | Requis | Description 
:---- | ---- | :---- 
<code>name</code> | Oui | Le nom du composant logiciel enfichable. Le nom peut utiliser toute combinaison de lettres minuscules et des nombres, plus le caractère '-' mais doit commencer par une lettre.
<code>version</code> | Oui | La version du snap. La version peut être définie avec une combinaison de lettres majuscules et minuscules, des nombres et les caractères '.', '+', '~', et '-'.
<code>summary</code> | Non | Un bref résumé du snap.
<code>description</code> | Non | Une description longue du snap.
<code>license-agreement</code> | Non | A régler sur `explicit` si l'utilisateur doit accepter le contenu du fichier `meta/license.txt` pour que le snap puisse s'installer.
<code>license-version</code> | NoN | Une chaîne définissant la version du texte de la licence. Lorsque sa valeur change et que la clé `license-agreement` est réglée sur `explicit`, il provoque l'invitation pour l'utilisateur à accepter à nouveau le contenu du fichier `meta/license.txt`.
<code>type</code> | Non |  Le type de snap, qui peut être: `app`, la valeur par défaut si la clé `type` est omise ou vide; ou `gadget`, un snap spécial que les Gadgets peuvent utiliser pour personnaliser Snappy pour leur matériel.
<code>architectures</code> | Non | Une liste YAML list des architectures supportées, par défaut réglée sur `["all"]` si elle est omise ou vide.
<code>apps</code> | Non | La carte des applications (binaires et services) que le snap fournit.
<code>&nbsp;&nbsp;&nbsp;&lt;app name></code> | Oui | Le nom de l'application ou du service.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;command</code> | Oui | La comamnde pour démarer l'application ou le service.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;daemon</code>| Oui | Le type de démon qui va exécuter l'application (en tant que service): `simple`, `forking`, `oneshot`, ou `dbus`
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;stop-command</code> | Non |  La commande pour stopper le service.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;stop-timeout</code> | Non |  Le temps en secondes à attendre pour que le service s'arrête.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;restart-condition</code> | Non |  Spécifie les conditions de redémarrage. Peut être l'une des valeur suivante : `on-failure` (défaut), `never`, `on-success`, `on-abnormal`, `on-abort`, and `always`. Voir `systemd.service(5)` (Rechercher `Restart=`) pour plus de details.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;post-stop-command</code> | Non |  Une commande qui s'exécute après que le service ce soit arrêté.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;slots</code> | Non | Une carte des interfaces.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ports</code> | Non |  Défini sur quels ports le service fonctionnera.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;internal</code> | Oui | Les ports sur lesquel le service se connectera.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tagname</code> | Oui | Un nom de forme libre.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port</code> | Non |  Numéro/protocole, par exemple `80/tcp`.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;negotiable</code> | Non |  `Y` si l'application peut utiliser un port différent.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;external</code> | Oui | Le ports que le service expose au monde
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tagname</code> | Oui | Un nom de forme libre, certains noms ont un sens comme "ui".
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port</code> | Non |  Numéro/protocole, par exemple `80/tcp`.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;negotiable</code> | Non |  `Y` si l'application peut utiliser un port différent.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;socket</code> | Non |  A définir sur `true` si le service est un connecteur activé. Doit être spécifié avec `listen-stream`.
<code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;listen-stream</code> | Non |  Le chemin complet du connecteur ou un connecteur abstrait. Lorsque vous spécifiez un chemin absolu, il devrait normalement être l'un des répertoires inscriptibles spécifiques aux applications. <br />Lorsqu'un conecteur abstrait est spécifié, il doit commencer par `@` et généralement être suivi soit par le nom du package snap ou le nom du paquet snap suivi par `\_` et n'importe quel autre caractère, par exemple `@name` ou `@name\_something`.
