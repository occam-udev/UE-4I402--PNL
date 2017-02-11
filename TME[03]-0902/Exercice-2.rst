==================================
TME[03]-Premiers pas dans le noyau
==================================

Exercice-2 : Configuration et compilation du noyau Linux
========================================================

Question-1
----------

Decompresser l'archive linux-4.2.3.tar.xz dans le repertoire tmp avec la commande suivante :

.. code-block:: bash

		tar xvJf ${HOME}/Documents/M1-SAR[S2]/UE[4I402]-PNL/
		sopena/pnl/linux-4.2.3.tar.xz -C
		${HOME}/Documents/M1-SAR[S2]/UE[4I402]-PNL/
		sopena/pnl/tmp/

Copier la configuration allegee du noyau dans le repertoire de votre noyau sous le nom .config avec la commande suivante :

.. code-block:: bash

		cp ${HOME}/Documents/M1-SAR[S2]/UE[4I402]-PNL/
		sopena/pnl/linux-config-nl
		${HOME}/Documents/M1-SAR[S2]/UE[4I402]-PNL/
		sopena/pnl/tmp/linux-4.2.3/.config

Acceder a la configuration du noyau Linux a l'aide de la commande make nconfig.

.. tip::
   **Il est conseille d'utiliser la commande make menuconfig qui a la difference de make nconfig, propose une legende.**

Les options de debogages se trouvent dans la majorité des categories et plus specifiquement dans la categorie kernel hacking.

Question-2
----------

Trouver le nombre de coeurs sur votre machine.

.. code-block:: bash

		cat /proc/cpuinfo | grep processor | wc -l

J'ai 8 coeur de disponible.

La valeur admise pour le parametre -j est 9 (nombre de coeurs +1) cependant il ne s'agit pas d'une valeur fixe.
Une valeur correcte a utiliser est 16 (2 fois le nombre de coeurs).

Question-3
----------

Compiler puis afficher les informations de votre image a l'aide de la commande suivante :

.. code-block:: bash

		file arch/x86/boot/bzImage

J'obtiens le resulat suivant :

.. code-block:: bash
		
		arch/x86/boot/bzImage:
		Linux kernel x86 boot executable bzImage, version 4.2.3
		(ockham@TermT-800) #2 SMP Thu Feb 9 15:34:49 CET 2017,
		RO-rootFS, swap_dev 0x7, Normal VGA

Question-4
----------

Modifier le script qemu-run-externKernel.sh en fonction de votre configuration.

Ci-dessous, les modifications apportees au script qemu-run-externKernel.sh :

.. code-block:: bash

		HDA=${HOME}/Documents/M1-SAR[S2]/UE[4I402]-PNL/
		sopena/pnl/pnl-tp.img
		
		HDB=${HOME}/myHome.img
		
		KERNEL=${HOME}/Documents/M1-SAR[S2]/UE[4I402]-PNL/
		sopena/pnl/tmp/linux-4.2.3/arch/x86/boot/bzImage

Le nom du noyau en cours d'execution est obtenue par la commande suivante :

.. code-block:: bash

		uname -r

Il s'agit du noyau 4.2.3, cependant il est impossible de determiner son appartenance.

Question-5
----------

Modifier le nom du noyau (section General Setup, menu Local version) pour qu'il se termine par -pnl.

Apres modification et verification le noyau en cours d'execution est 4.2.3-pnl.

Question-6
----------

La commande suivante affiche la liste des modules charges :

.. code-block:: bash

		lsmod

A partir de la configuration actuelle, je m'appercois qu'aucun module n'est charge car ils sont directement compiles dans le noyau (choix * du menu de configuration) et pas charges sous forme de modules (choix M du menu de configuration).

