# ![GodMode9](https://github.com/d0k3/GodMode9/blob/master/resources/logo.png)
_Un navigateur de fichiers complet pour la console Nintendo 3DS_ :godmode:

GodMode9 est un navigateur de fichiers complet pour la console Nintendo 3DS, vous donnant accès à votre carte SD, aux partitions FAT de votre SysNAND et EmuNAND, ainsi qu'à pratiquement tout le reste. Entre autres fonctionnalités (voir ci-dessous), vous pouvez copier, supprimer, renommer des fichiers et créer des dossiers.


## Attention
_C'est du sérieux_, cela vous donne les moyens d'effectuer pratiquement toutes les modifications imaginables sur toutes les données système disponibles sur la console 3DS. Cependant, des précautions sont prises pour éviter que vous n'endommagiez accidentellement les données de votre console. Le système de permissions en écriture vous protège en vous fournissant des avertissements et en vous obligeant à saisir une séquence de déverrouillage pour activer les permissions en écriture. Il n'est pas possible d'écraser ou de modifier des éléments importants sans ces séquences de déverrouillage, et il n'est pas possible de déverrouiller quelque chose accidentellement.

_Comme toujours, soyez prudent, faites des sauvegardes, juste au cas où_.


## Guide de démarrage rapide
Le bootloader recommandé pour utiliser GodMode9 est [fastboot3DS](https://github.com/derrekr/fastboot3DS). Il existe des [problèmes connuspour certains utilisateurs](https://github.com/d0k3/GodMode9/issues/466) lors de l'utilisation de la configuration standard basée sur [boot9strap](https://github.com/SciresM/boot9strap) et [Luma3DS](https://github.com/AuroraWright/Luma3DS). Si vous insistez pour utiliser cette configuration, suivez les instructions trouvées dans un [certain guide](https://3ds.hacks.guide). Voici comment configurer rapidement GodMode9 (et fastboot3DS) :
* Téléchargez [OpenFirmInstaller](https://github.com/d0k3/OpenFirmInstaller/releases/tag/v0.0.9) et suivez les instructions rapides de configuration disponibles là-bas.
* Copiez le dossier gm9 de l'archive de la version sur votre carte SD. Ensuite, obtenez de bonnes versions de seeddb.bin et encTitleKeys.bin quelque part (ne me demandez pas!) et placez ces deux fichiers dans sd:/gm9/support (optionnel mais recommandé pour une fonctionnalité complète).
* Il est également recommandé de configurer l'horloge RTC si vous exécutez GodMode9 pour la première fois. Trouvez l'option via le bouton HOME -> Plus.... Gardez également à l'esprit que vous devriez régler l'horloge de votre système OS par la suite. Pendant que vous êtes dans le menu Plus..., vous pouvez également définir la luminosité de l'écran sur une valeur fixe de votre choix et calibrer manuellement l'écran tactile (non recommandé - essayez d'abord la configuration automatique).
* Astuce utile #1: Allez [ici](https://3ds.hacks.guide/godmode9-usage) pour des étapes sur la réalisation de certaines tâches courantes dans GodMode9. Les utilisateurs venant de Decrypt9WIP ou Hourglass9 pourraient trouver cela particulièrement utile.
* Astuce utile #2: _Ne déverrouillez jamais le niveau de permission en écriture rouge à moins de savoir exactement ce que vous faites_. Vous remarquerez ce message d'avertissement lorsqu'il apparaît, il affiche un écran entièrement rouge. Il est recommandé de rester toujours au niveau de permission jaune ou inférieur pour être complètement en sécurité. Lisez également plus sur le système de permissions en écriture ci-dessous.

Vous pouvez maintenant exécuter GodMode9 en maintenant le bouton X (ou tout autre bouton que vous avez choisi) au démarrage. Consultez ci-dessous pour une liste des fonctionnalités que vous pouvez utiliser avec ce programme.


## Touches dans GodMode9
GodMode9 est conçu pour être intuitif, les boutons mènent aux résultats que vous attendez. Cependant, certaines fonctionnalités peuvent ne pas être évidentes au premier abord. Voici un aperçu rapide et incomplet de ce que chaque bouton / combinaison de boutons fait.

Bouton <A>: Le bouton <A> est le bouton "confirmer" / "choisir". Il confirme les invites et sélectionne les entrées dans les menus. Dans la vue principale des fichiers, il ouvre un sous-menu pour les fichiers et les répertoires (utilisez <R+A> sur les répertoires pour un sous-menu, incluant également la recherche de titres précieuse). Dans le visualiseur hexadécimal, <A> passe en mode édition.
Bouton <B>: Le bouton <B> est le bouton "annuler" / "retour". Utilisez-le pour quitter les menus sans action, maintenez-le lors des opérations sur les fichiers pour annuler ces opérations.
Bouton <X>: Dans la vue principale des fichiers, le bouton <X> supprime les fichiers marqués. Avec <R+X>, les fichiers peuvent être renommés.
Bouton <Y>: Dans la vue principale des fichiers, le bouton <Y> copie et colle les fichiers. Avec <R+Y>, vous pouvez créer des dossiers et des fichiers factices.
Bouton <L>: Le bouton <L> est le bouton "marquer". Utilisez-le avec <GAUCHE> / <DROITE> pour marquer / démarquer tous les fichiers dans un dossier, maintenez-le et utilisez <HAUT> / <BAS> pour sélectionner plusieurs fichiers.
Bouton <R>: Le bouton <R> est le bouton "commutateur". Il passe les boutons à leur fonction secondaire. Les exceptions notables sont <R+L> pour une capture d'écran (fonctionne presque partout), <R+GAUCHE> / <R+DROITE> pour changer de volet et <R+BAS> pour recharger la liste des fichiers.
Bouton <START>: Utilisez le bouton <START> pour redémarrer à partir de GodMode9. Utilisez <R+START> pour éteindre votre 3DS.
Bouton <SELECT>: Le bouton <SELECT> efface ou restaure le presse-papiers (selon qu'il est vide ou non).
Bouton <HOME>: Le bouton <HOME> entre dans le menu HOME, y compris les sous-menus des scripts / payloads, les options de formatage de la SD, le réglage de l'RTC, et plus encore. Le bouton <POWER> est une autre façon d'entrer dans le menu HOME.
Combo <R+HAUT>: Ce combo méconnu, lorsque maintenu au démarrage, met en pause le démarrage de GodMode9 afin que vous puissiez regarder l'écran de démarrage un peu plus longtemps.
Combo <R+GAUCHE>: Si vous avez installé GodMode9 comme chargeur d'amorçage, ce combo de touches entre dans le menu de démarrage. Maintenez lors du démarrage! Si vous avez construit GodMode9 comme SALTMODE et l'avez comme chargeur d'amorçage, le combo de touches est simplement le bouton <START>.

## Comment compiler ceci / informations pour les développeurs
Construisez `GodMode9.firm` via `make firm`. Cela nécessite [firmtool](https://github.com/TuxSH/firmtool), [Python 3.5+](https://www.python.org/downloads/) et [devkitARM](https://sourceforge.net/projects/devkitpro/) installés.

Vous pouvez exécuter `make release` pour obtenir un package prêt à être publié de tous les fichiers requis. Pour construire SafeMode9 (une variante de GodMode9 plus sûre, avec des permissions en écriture limitées) au lieu de GodMode9, compilez avec make FLAVOR=SafeMode9. Pour basculer entre les écrans, compilez avec make SWITCH_SCREENS=1. Pour une personnalisation supplémentaire, vous pouvez choisir la police interne en remplaçant font_default.frf dans le répertoire data. Vous pouvez également définir la luminosité fixe via make FIXED_BRIGHTNESS=x, où x est une valeur entre 0...15.

Une personnalisation supplémentaire est possible en codant en dur aeskeydb.bin (il suffit de mettre le fichier dans le dossier data lors de la compilation). Tous les fichiers placés dans le dossier data apparaîtront dans le lecteur V:, mais gardez à l'esprit qu'il y a une limite rigide de 223,5 Ko pour tous les fichiers à l'intérieur, y compris les frais généraux. Un exécuteur de script autonome est compilé en fournissant autorun.gm9 (encore une fois, dans le dossier data) et en construisant avec make SCRIPT_RUNNER=1. Il y a plus de possibilités de personnalisation, lisez les Makefiles pour en savoir plus.

Pour construire un .firm signé avec les clés de démarrage SPI (pour ntrboot et similaires), exécutez make NTRBOOT=1. Vous devrez peut-être renommer les fichiers de sortie si l'installateur ntrboot que vous utilisez utilise des noms de fichiers codés en dur. Certaines fonctionnalités telles que l'accès boot9 / boot11 ne sont actuellement pas disponibles depuis l'environnement ntrboot.


## Mode du Bootloader
Identique à [boot9strap](https://github.com/SciresM/boot9strap) ou [fastboot3ds](https://github.com/derrekr/fastboot3DS), GodMode9 peut être installé dans la partition FIRM du système ('FIRM0'). Lorsqu'il est exécuté à partir d'une partition FIRM, GodMode9 se mettra par défaut en mode chargeur d'amorçage et tentera de démarrer, dans l'ordre, FIRM depuis FCRAM (voir [A9NC](https://github.com/d0k3/A9NC/releases)), 0:/bootonce.firm (sera supprimé lors d'un démarrage réussi), 0:/boot.firm, 1:/boot.firm. En mode du Bootloader, maintenez R+GAUCHE au démarrage pour entrer dans le menu de démarrage. L'installation de GodMode9 dans une partition FIRM est uniquement recommandée pour les développeurs et écrasera boot9strap ou tout autre chargeur d'amorçage que vous avez installé à cet endroit.
*L'installation de GodMode9 dans une partition FIRM est uniquement recommandée pour les développeurs et écrasera [boot9strap](https://github.com/SciresM/boot9strap) ou tout autre Bootloader que vous avez installé à cet endroit*.


## Système de permissions d'écriture
GodMode9 offre un système de permissions d'écriture qui vous protège contre toute modification accidentelle de votre système, la perte de données et/ou la modification de données système importantes. Pour déverrouiller une permission d'écriture, une séquence de déverrouillage doit être entrée. Il est impossible de le faire par accident. Le système de permissions d'écriture est basé sur des couleurs, et la barre supérieure de l'écran affiche la couleur correspondant au niveau actuel de permission d'écriture. Aucune permission au-dessus du niveau jaune ne peut être déverrouillée sur SafeMode9.
Vert : A ce niveau de permission, la modification des fichiers système n'est pas possible. Vous ne pouvez pas éditer ou supprimer les sauvegardes de jeu ni les données installées. Cependant, gardez à l'esprit que tout ce qui n'est pas lié au système ou personnalisé sur votre carte SD n'est pas protégé.
Jaune : Vous pouvez modifier les fichiers système à ce niveau de permission. Les données uniques à votre console et non disponibles ailleurs ne sont toujours pas modifiables. Tous les dommages que vous introduisez peuvent être réparés par logiciel, mais la perte de sauvegardes de jeu et de données installées est possible si vous n'êtes pas prudent. Il est fortement recommandé de faire une sauvegarde NAND à partir de ce niveau.
Orange : Ce niveau est similaire au niveau jaune, mais permet en plus les modifications aux données uniques à la console. Tous les dommages que vous introduisez sont encore réparables par logiciel, mais si vous manipulez cela, avoir une sauvegarde NAND est une nécessité absolue.
Rouge : C'est le plus haut niveau de permission régulière. Il n'y a pas de limites aux modifications des fichiers système, et si vous n'êtes pas assez prudent, vous pouvez briquer votre console et/ou supprimer votre installation A9LH/B9S. Les briques à ce niveau peuvent parfois nécessiter une réparation matérielle. Si vous n'avez pas de sauvegarde NAND à ce stade, vous semblez vouloir risquer sérieusement votre console.
Bleu : Ce niveau de permission est réservé aux modifications de la mémoire système. Bien que rien de grave ne se produise probablement, les conséquences des modifications peuvent être imprévisibles. Il existe même une (bien que très petite) chance de briquer votre console, peut-être même de manière permanente. Marchez avec prudence à ce niveau.


## Fichiers de support
Pour certaines fonctionnalités, GodMode9 peut nécessiter des "fichiers de support". Ces fichiers doivent être placés dans `0:/gm9/support` ou `1:/gm9/support`. Les fichiers de support contiennent des informations supplémentaires nécessaires aux opérations de décryptage. Une liste des fichiers de support et de leurs fonctions est disponible ci-dessous. S'il vous plaît, ne demandez pas de fichiers de support - trouvez-les vous-même.
*__`aeskeydb.bin`__: Ce fichier doit contenir 0x25keyX, 0x18keyX et 0x1BkeyX pour activer le décryptage des fichiers NCCH cryptés en 7x / Secure3 / Secure4, 0x11key95 / 0x11key96 pour le support de décryptage FIRM et 0x11keyOTP / 0x11keyIVOTP pour le support cryptographique du secteur secret 0x96. Les points d'entrée autres que [boot9strap](https://github.com/SciresM/boot9strap) ou [fastboot3ds](https://github.com/derrekr/fastboot3DS) peuvent nécessiter un fichier aeskeydb.bin. Ce fichier est inclus dans les versions standard de GM9. Pas besoin de le chasser !
*__`seeddb.bin`__: Ce fichier est facultatif mais nécessaire pour décrypter et monter des NCCHs et des CIA cryptés par seed (si le seed en question n'est pas installé dans votre NAND). Notez que votre seeddb.bin doit également contenir le seed spécifique au jeu que vous souhaitez décrypter.
*__`encTitleKeys.bin`__ / __`decTitleKeys.bin`__: Ces fichiers sont facultatifs et fournissent des titlekeys nécessaires pour décrypter et installer du contenu téléchargé depuis le CDN (pour les contenus DSi et 3DS).

## Polices et traductions
GodMode9 prend également en charge les polices et les traductions personnalisées en tant que fichiers de support. Ils utilisent tous deux des formats personnalisés : les polices utilisent des fichiers FRF (Font RIFF) créés à l'aide du script Python `fontriff.py` dans le dossier 'utils'. Les traductions utilisent des fichiers TRF (Translation RIFF) à partir du script transriff.py. Des exemples des entrées pour ces scripts sont disponibles dans les dossiers 'fonts' et 'languages' du dossier 'resources'.

Les fichiers TRF peuvent être placés dans `0:/gm9/languages` pour apparaître dans le menu de langue accessible depuis le menu HOME et affichés lors du premier chargement. Les traductions officielles sont fournies par la communauté via [GodMode9 Crowdin](https://crowdin.com/project/GodMode9). Les langues peuvent utiliser une police spéciale en ayant un FRF avec le même nom, par exemple `en.trf` et `en.frf`.

## Lecteurs dans GodMode9
GodMode9 offre un accès aux données système via des lecteurs, une liste de ce que chaque lecteur contient et des informations supplémentaires suivent ci-dessous. Certains de ces lecteurs sont amovibles (comme le lecteur `7:`), d'autres ne seront visibles que s'ils sont disponibles (lecteur `8:` et tout ce qui est associé à EmuNAND, par exemple). Des informations sur le système de fichiers de la console 3DS sont également disponibles sur [3Dbrew.org](https://3dbrew.org/wiki/Flash_Filesystem).
*__`0: SDCARD`__ : La carte SD actuellement insérée dans le slot de la carte SD. Le dossier 0:/Nintendo 3DS contient les installations de logiciels et les données extdata et est spécialement protégé par le système de permissions d'écriture. La carte SD peut être démontée depuis le répertoire racine via les boutons R+B, sinon la carte SD est toujours disponible.
*__`1: SYSNAND CTRNAND`__ : La partition CTRNAND sur SYSNAND. Elle contient le système d'exploitation de votre console 3DS et les installations de logiciels système. Les données ici sont protégées par le système de permissions d'écriture.
*__`2: SYSNAND TWLN`__ : La partition TWLN sur SYSNAND. Elle contient le système d'exploitation en mode TWL de votre console 3DS et les installations de logiciels système. Les données ici sont protégées par le système de permissions d'écriture.
*__`3: SYSNAND TWLP`__ : La partition TWLP sur SYSNAND. Elle contient les photos prises en mode TWL.
*__`A: SYSNAND SD`__ : Ce lecteur est utilisé pour un accès spécial aux données sur votre carte SD. Il est lié à un sous-dossier à l'intérieur de `0:/Nintendo 3DS` et contient les logiciels et les données extdata installés sur la SD depuis SYSNAND. Le cryptage dans ce dossier est géré uniquement lorsqu'il est accédé via le lecteur A: (pas depuis 0:). Cela est protégé par le système de permissions d'écriture.
*__`S: SYSNAND VIRTUAL`__ : Ce lecteur donne accès à toutes les partitions de SYSNAND, certaines d'entre elles étant critiques pour la fonctionnalité de base du système. Cela est protégé par le système de permissions d'écriture, mais une fois déverrouillé, les modifications peuvent briquer le système.
*__`4: EMUNAND CTRNAND`__ : Identique à `1:`, mais gère le CTRNAND sur EMUNAND. Pour les configurations multi-EmuNAND, la partition EMUNAND active peut être changée via le menu HOME.
*__`5: EMUNAND TWLN`__ : Identique à `2`, mais gère le TWLN sur EMUNAND. Aucune protection d'écriture ici car cette partition n'est jamais utilisée en EMUNAND.
*__`6: EMUNAND TWLP`__ : Identique à `3`, mais gère le TWLP sur EMUNAND.
*__`B: EMUNAND SD`__ : Identique à A:, mais gère le sous-dossier `0:/Nintendo 3DS` associé à EMUNAND. En cas de NANDs liées, c'est identique à A:. Cela est également protégé par le système de permissions d'écriture.
*__`E: EMUNAND VIRTUAL`__ : Identique à `S:`, mais gère les partitions système sur EMUNAND. Aucun risque de briquage ici car EMUNAND n'est jamais critique pour la fonctionnalité du système.
*__`7: FAT IMAGE / IMGNAND CTRNAND`__ : Fournit un accès aux images FAT montées. Lorsqu'une image NAND est montée, cela donne accès au CTRNAND de l'image NAND montée.
*__`8: BONUS DRIVE / IMGNAND TWLN`__ : Fournit un accès au lecteur bonus sur SYSNAND. Le lecteur bonus peut être configuré via le menu HOME sur les consoles 3DS qui le permettent. Lorsqu'une image NAND est montée, cela donne accès au TWLN de l'image NAND montée.
*__`9: RAM DRIVE / IMGNAND TWLP`__ : Fournit un accès au lecteur RAM. Toutes les données stockées dans le lecteur RAM sont temporaires et seront effacées après un redémarrage. Lorsqu'une image NAND est montée, cela donne accès au TWLP de l'image NAND montée.
*__`I: IMGNAND VIRTUAL`__ : Lorsqu'une image NAND est montée, cela donne accès aux partitions à l'intérieur de l'image NAND.
*__`C: GAMECART`__ : C'est en lecture seule et donne accès à la cartouche de jeu actuellement insérée dans le slot de cartouche. Cela peut être utilisé pour les dumps de cartouches CTR et TWL. Les flashcards sont prises en charge seulement dans une certaine mesure.
*__`G: GAME IMAGE`__ : Les images CIA/NCSD/NCCH/EXEFS/ROMFS/FIRM peuvent être accessibles via ce lecteur lorsqu'elles sont montées. C'est en lecture seule.
*__`K: AESKEYDB IMAGE`__ : Une image `aeskeydb.bin` peut être montée et accédée via ce lecteur. Le lecteur affiche toutes les clés à l'intérieur du aeskeydb.bin. C'est en lecture seule.
*__`T: TICKET.DB IMAGE / BDRI IMAGE`__ : Les fichiers de base de données de tickets peuvent être montés et accessibles via ce lecteur. Cela offre un accès facile et rapide à tous les tickets à l'intérieur de `ticket.db`. Ce lecteur offre également un accès à d'autres images BDRI, comme la base de données de titres (title.db).
*__`M: MEMORY VIRTUAL`__ : Fournit un accès à diverses régions de la mémoire. Cela est protégé par une permission d'écriture spéciale, et la prudence est conseillée lors des modifications à l'intérieur de ce lecteur. Ce lecteur donne également accès à `boot9.bin`, `boot11.bin` (uniquement pour boot9strap) et `otp.mem` (systèmes sighaxed uniquement).
*__`V: VRAM VIRTUAL`__ : Ce lecteur réside en partie dans la mémoire interne ARM9 et contient des fichiers essentiels à GodMode9. La police (au format FRF), le logo de démarrage (au format PNG) et le fichier readme s'y trouvent, ainsi que tout fichier fourni dans le dossier data au moment de la compilation. C'est en lecture seule.
*__`Y: TITLE MANAGER`__ : Le gestionnaire de titres est accessible via le menu HOME et offre un accès facile à tous les titres installés.
*__`Z: LAST SEARCH`__ : Après une opération de recherche, les résultats de la recherche se trouvent dans ce lecteur. Le lecteur peut être accessible ultérieurement pour revenir aux résultats de recherche précédents.


## Digital preservation
GodMode9 is one of the most important tools for digital preservation of 3DS content data. Here's some stuff you should know:
* __Dumping game cartridges (size < 4GiB)__: Game cartridges turn up inside the `C:` drive (see above). For most carts all you need to do is copy the `.3DS` game image to some place of your choice. Game images dumped by GodMode9 contain no identifying info such as private headers or savegames. Private headers can be dumped in a separate image.
* __Dumping game cartridges (size = 4GiB)__: Everything written above applies here as well. However, the FAT32 file system (which is what the 3DS uses) is limited to _4GiB - 1byte_. Take note that the `.3DS` game image, as provided by GodMode9 actually misses the last byte in these cases. That byte is 0xFF and unused in all known cases. It is not required for playing the image. If you need to check, we also provide split files (`.000`, `.001)`, which contain all the data. If you need a valid checksum for the `.3DS` game image, append a 0xFF byte before checking.
* __Building CIAs (all types)__: You may convert compatible file types (game images, installed content, CDN content) to the CIA installable format using the A button menu. To get a list of installed content, press HOME, select `Title manager` and choose a drive. Take note that `standard` built CIAs are decrypted by default (decryption allows better compression by ZIP and 7Z). If you should need an encrypted CIA for some reason, apply the encryption to the CIA afterwards.
* __Building CIAs (legit type)__: Installed content can be built as `legit` or `standard` CIA. Legit CIAs preserve more of the original data and are thus recommended for preservation purposes. When building legit CIAs, GodMode9 keeps the original crypto and tries to find a genuine, signature-valid ticket. If it doesn't find one on your system, it will use a generic ticket instead. If it only finds a personalized one, it still offers to use a generic ticket. It is not recommended to use personalized tickets - only choose this if you know what you're doing.
* __Checking CIAs__: You may also check your CIA files with the builtin `CIA checker tool`. Legit CIAs with generic tickets are identified as `Universal Pirate Legit`, which is the recommended preservation format where `Universal Legit` is not available. Note: apart from system titles, `Universal Legit` is only available for a handful of preinstalled games from special edition 3DS consoles.


## What you can do with GodMode9
With the possibilites GodMode9 provides, not everything may be obvious at first glance. In short, __GodMode9 includes improved versions of basically everything that Decrypt9 has, and more__. Any kind of dumps and injections are handled via standard copy operations and more specific operations are found inside the A button menu. The A button menu also works for batch operations when multiple files are selected. For your convenience a (incomplete!) list of what GodMode9 can do follows below.

### Basic functionality
* __Manage files on all your data storages__: You wouldn't have expected this, right? Included are all standard file operations such as copy, delete, rename files and create folders. Use the L button to mark multiple files and apply file operations to multiple files at once.
* __Make screenshots__: Press R+L anywhere. Screenshots are stored in PNG format.
* __Use multiple panes__: Press R+left|right. This enables you to stay in one location in the first pane and open another in the second pane.
* __Search drives and folders__: Just press R+A on the drive / folder you want to search.
* __Compare and verify files__: Press the A button on the first file, select `Calculate SHA-256`. Do the same for the second file. If the two files are identical, you will get a message about them being identical. On the SDCARD drive (`0:`) you can also write an SHA file, so you can check for any modifications at a later point.
* __Hexview and hexedit any file__: Press the A button on a file and select `Show in Hexeditor`. A button again enables edit mode, hold the A button and press arrow buttons to edit bytes. You will get an additional confirmation prompt to take over changes. Take note that for certain files, write permissions can't be enabled.
* __View text files in a text viewer__: Press the A button on a file and select `Show in Textviewer` (only shows up for actual text files). You can enable wordwrapped mode via R+Y, and navigate around the file via R+X and the dpad.
* __Chainload FIRM payloads__: Press the A button on a FIRM file, select `FIRM options` -> `Boot FIRM`. Keep in mind you should not run FIRMs from dubious sources and that the write permissions system is no longer in place after booting a payload.
* __Chainload FIRM payloads from a neat menu__: The `payloads` menu is found inside the HOME button menu. It provides any FIRM found in `0:/gm9/payloads` for quick chainloading.
* __Inject a file to another file__: Put exactly one file (the file to be injected from) into the clipboard (via the Y button). Press A on the file to be injected to. There will be an option to inject the first file into it.

### Scripting functionality
* __Run .gm9 scripts from anywhere on your SD card__: You can run scripts in .gm9 format via the A button menu. .gm9 scripts use a shell-like language and can be edited in any text editor. For an overview of usable commands have a look into the sample scripts included in the release archive. *Don't run scripts from untrusted sources.*
* __Run .gm9 scripts via a neat menu__: Press the HOME button, select `More...` -> `Scripts...`. Any script you put into `0:/gm9/scripts` (subdirs included) will be found here. Scripts ran via this method won't have the confirmation at the beginning either.

### SD card handling
* __Format your SD card / setup an EmuNAND__: Press the HOME button, select `More...` -> `SD format menu`. This also allows to setup a RedNAND (single/multi) or GW type EmuNAND on your SD card. You will get a warning prompt and an unlock sequence before any operation starts.
* __Handle multiple EmuNANDs__: Press the HOME button, select `More...` -> `Switch EmuNAND` to switch between EmuNANDs / RedNANDs. (Only available on multi EmuNAND / RedNAND systems.)
* __Run it without an SD card / unmount the SD card__: If no SD card is found, you will be offered to run without the SD card. You can also unmount and remount your SD card from the file system root at any point.
* __Direct access to SD installed contents__: Just take a look inside the `A:`/`B:` drives. On-the-fly-crypto is taken care for, you can access this the same as any other content.
* __Set (and use) the RTC clock__: For correct modification / creation dates in your file system, you need to setup the RTC clock first. Press the HOME Button and select `More...` to find the option. Keep in mind that modifying the RTC clock means you should also fix system OS time afterwards.

### Game file handling
* __List titles installed on your system__: Press HOME and select `Title manager`. This will also work via R+A for `CTRNAND` and `A:`/`B:` drives. This will list all titles installed in the selected location.
* __Install titles to your system__: Just press A on any file you want installed and select `Install game image` from the submenu. Works with NCCH / NCSD / CIA / DSiWare SRLs / 3DS CDN TMDs / DSi CDN TMDs / NUS TMDs.
* __(Batch) Uninstall titles from your system__: Most easily done via the HOME menu `Title manager`. Just select one or more titles and find the option inside the `Manage title...` submenu.
* __Build CIAs from NCCH / NCSD (.3DS) / SRL / TMD__: Press A on the file you want converted and the option will be shown. Installed contents are found most easily via the HOME menu `Title manager`. Where applicable, you will also be able to generate legit CIAs. Note: this works also from a file search and title listing.
* __Dump CXIs / NDS from TMD (installed contents)__: This works the same as building CIAs, but dumps decrypted CXIs or NDS rom dumps instead. Note: this works also from a file search and title listing.
* __Decrypt, encrypt and verify NCCH / NCSD / CIA / BOSS / FIRM images__: Options are found inside the A button menu. You will be able to decrypt/encrypt to the standard output directory or (where applicable) in place.
* __Decrypt content downloaded from CDN / NUS__: Press A on the file you want decrypted. For this to work, you need at least a TMD file (`encTitlekeys.bin` / `decTitlekeys.bin` also required, see _Support files_ below) or a CETK file. Either keep the names provided by CDN / NUS, or rename the downloaded content to `(anything).nus` or `(anything).cdn` and the CETK to `(anything).cetk`.
* __Batch mode for the above operations__: Just select multiple files of the same type via the L button, then press the A button on one of the selected files.
* __Access any file inside NCCH / NCSD / CIA / FIRM / NDS images__: Just mount the file via the A button menu and browse to the file you want. For CDN / NUS content, prior decryption is required for full access.
* __Rename your NCCH / NCSD / CIA / NDS / GBA files to proper names__: Find this feature inside the A button menu. Proper names include title id, game name, product code and region.
* __Trim NCCH / NCSD / NDS / GBA / FIRM / NAND images__: This feature is found inside the A button menu. It allows you to trim excess data from supported file types. *Warning: Excess data may not be empty, bonus drives are stored there for NAND images, NCSD card2 images store savedata there, for FIRMs parts of the A9LH exploit may be stored there*.
* __Dump 3DS / NDS / DSi type retail game cartridges__: Insert the cartridge and take a look inside the `C:` drive. You may also dump private headers from 3DS game cartridges. The `C:` drive also gives you read/write access to the saves on the cartridges. Note: For 4GiB cartridges, the last byte is not included in the .3ds file dump. This is due to restrictrions of the FAT32 file system.

### NAND handling
* __Directly mount and access NAND dumps or standard FAT images__: Just press the A button on these files to get the option. You can only mount NAND dumps from the same console.
* __Restore NAND dumps while keeping your A9LH / sighax installation intact__: Select `Restore SysNAND (safe)` from inside the A button menu for NAND dumps.
* __Restore / dump NAND partitions or even full NANDs__: Just take a look into the `S:` (or `E:`/ `I:`) drive. This is done the same as any other file operation.
* __Transfer CTRNAND images between systems__: Transfer the file located at `S:/ctrnand_full.bin` (or `E:`/ `I:`). On the receiving system, press A, select `CTRNAND Options...`, then `Transfer to NAND`.
* __Embed an essential backup right into a NAND dump__: This is available in the A button menu for NAND dumps. Essential backups contain NAND header, `movable.sed`, `LocalFriendCodeSeed_B`, `SecureInfo_A`, NAND CID and OTP. If your local SysNAND does not contain an embedded backup, you will be asked to do one at startup. To update the essential SysNAND backup at a later point in time, press A on `S:/nand.bin` and select `NAND image options...` -> `Update embedded backup`.
* __Install an AES key database to your NAND__: For `aeskeydb.bin` files the option is found in `aeskeydb.bin options` -> `Install aeskeydb.bin`. Only the recommended key database can be installed (see above). With an installed key database, it is possible to run the GodMode9 bootloader completely from NAND.
* __Install FIRM files to your NAND__: Found inside the A button menu for FIRM files, select `FIRM options` -> `Install FIRM`. __Use this with caution__ - installing an incompatible FIRM file will lead to a __brick__. The FIRMs signature will automagically be replaced with a sighax signature to ensure compatibility.
* __Actually use that extra NAND space__: You can set up a __bonus drive__ via the HOME menu, which will be available via drive letter `8:`. (Only available on systems that have the extra space.)
* __Fix certain problems on your NANDs__: You can fix CMACs for a whole drive (works on `A:`, `B:`, `S:` and `E:`) via an entry in the R+A button menu, or even restore borked NAND headers back to a functional state (inside the A button menu of borked NANDs and available for `S:/nand_hdr.bin`). Recommended only for advanced users!

### System file handling
* __Check and fix CMACs (for any file that has them)__: The option will turn up in the A button menu if it is available for a given file (f.e. system savegames, `ticket.db`, etc...). This can also be done for multiple files at once if they are marked.
* __Mount ticket.db files and dump tickets__: Mount the file via the A button menu. Tickets are sorted into `eshop` (stuff from eshop), `system` (system tickets), `unknown` (typically empty) and `hidden` (hidden tickets, found via a deeper scan) categories. All tickets displayed are legit, fake tickets are ignored
* __Inject any NCCH CXI file into Health & Safety__: The option is found inside the A button menu for any NCCH CXI file. NCCH CXIs are found, f.e. inside of CIAs. Keep in mind there is a (system internal) size restriction on H&S injectable apps.
* __Inject and dump GBA VC saves__: Find the options to do this inside the A button menu for `agbsave.bin` in the `S:` drive. Keep in mind that you need to start the specific GBA game on your console before dumping / injecting the save. _To inject a save it needs to be in the clipboard_.
* __Dump a copy of boot9, boot11 & your OTP__: This works on sighax, via boot9strap only. These files are found inside the `M:` drive and can be copied from there to any other place.

### Support file handling
* __Build `decTitleKeys.bin` / `encTitleKeys.bin` / `seeddb.bin`__: Press the HOME button, select `More...` -> `Build support files`. `decTitleKeys.bin` / `encTitleKeys.bin` can also be created / merged from tickets, `ticket.db` and merged from other `decTitleKeys.bin` / `encTitleKeys.bin` files via the A button menu.
* __Build, mount, decrypt and encrypt `aeskeydb.bin`__: AES key databases can be merged from other `aeskeydb.bin` or build from legacy `slot??Key?.bin` files. Just select one or more files, press A on one of them and then select `Build aeskeydb.bin`. Options for mounting, decrypting and encrypting are also found in the A button menu.


## License
You may use this under the terms of the GNU General Public License GPL v2 or under the terms of any later revisions of the GPL. Refer to the provided `LICENSE.txt` file for further information.

## Contact info
You can chat directly with us via IRC @ #GodMode9 on [libera.chat](https://web.libera.chat/#GodMode9) or [Discord](https://discord.gg/BRcbvtFxX4)!

## Credits
This tool would not have been possible without the help of numerous people. Thanks go to (in no particular order)...
* **Archshift**, for providing the base project infrastructure
* **Normmatt**, for sdmmc.c / sdmmc.h and gamecart code, and for being of great help on countless other occasions
* **Cha(N)**, **Kane49**, and all other FatFS contributors for [FatFS](http://elm-chan.org/fsw/ff/00index_e.html)
* **Wolfvak** for ARM11 code, FIRM binary launcher, exception handlers, PCX code, Makefile and for help on countless other occasions
* **SciresM** for helping me figure out RomFS and for boot9strap
* **SciresM**, **Myria**, **Normmatt**, **TuxSH** and **hedgeberg** for figuring out sighax and giving us access to bootrom
* **ihaveamac** for first developing the simple CIA generation method and for being of great help in porting it
* **wwylele** and **aspargas2** for documenting and implementing the DISA, DIFF, and BDRI formats
* **dratini0** for savefile management, based on [TWLSaveTool](https://github.com/TuxSH/TWLSaveTool/)
* **Pk11** for unicode and translation support
* **b1l1s** for helping me figure out A9LH compatibility
* **Gelex** and **AuroraWright** for helping me figure out various things
* **stuckpixel** for the new 6x10 font and help on various things
* **Al3x_10m** for help with countless hours of testing and useful advice
* **WinterMute** for helping me with his vast knowledge on everything gamecart related
* **profi200** for always useful advice and helpful hints on various things
* **windows-server-2003** for the initial implementation of if-else-goto in .gm9 scripts
* **Kazuma77** for pushing forward scripting, for testing and for always useful advice
* **TurdPooCharger** for being one of the most meticulous software testers around
* **JaySea**, **YodaDaCoda**, **liomajor**, **Supster131**, **imanoob**, **Kasher_CS** and countless others from freenode #Cakey and the GBAtemp forums for testing, feedback and helpful hints
* **Shadowhand** for being awesome and [hosting my nightlies](https://d0k3.secretalgorithm.com/)
* **Plailect** for putting his trust in my tools and recommending this in [The Guide](https://3ds.guide/)
* **SirNapkin1334** for testing, bug reports and for hosting the original GodMode9 Discord server
* **Lilith Valentine** for testing and helpful advice
* **Project Nayuki** for [qrcodegen](https://github.com/nayuki/QR-Code-generator)
* **Amazingmax fonts** for the Amazdoom font
* The fine folks on **the official GodMode9 IRC channel and Discord server**
* The fine folks on **freenode #Cakey**
* All **[3dbrew.org](https://www.3dbrew.org/wiki/Main_Page) editors**
* Everyone I possibly forgot, if you think you deserve to be mentioned, just contact us!
