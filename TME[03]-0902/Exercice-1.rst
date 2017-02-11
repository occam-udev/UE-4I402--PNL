==================================
TME[03]-Premiers pas dans le noyau
==================================

Exercice-1 : Environnement de developpement
===========================================

Question-1
----------

Que ce passe t-il lorsqu'on lance la commande suivante ??

.. code-block:: bash
		
	  qemu-system-x86_64 -hda pnl-tp.img

La commande execute l'emulateur qemu et utilise le fichier pnl-tp.img
comme image disque.

Question-2
----------

Generez une image personnelle a l'aide des commandes suivantes :

.. code-block:: bash

		dd bs=1M count=50 if=/dev/zero of=${HOME}/myHome.img
		
		/sbin/mkfs.ext4 -F ${HOME}/myHome.img

Question-3
----------

Modifier le script qemu-run.sh en fonction de votre configuration.

Ci-dessous, les modifications apportees au script qemu-run.sh :

.. code-block:: bash

		HDA=${HOME}/Documents/M1-SAR[S2]/UE[4I402]-PNL/
		sopena/pnl/pnl-tp.img
		
		HDB=${HOME}/myHome.img

