---
id: q2u6boUm4STaNcKoixMvJ
title: CahierCharges
desc: ''
updated: 1636960425215
created: 1636960353304
---
# Sujet TP

## 1 Cahier des charges

Le Système à concevoir doit permettre le fonctionnement simplifié d’une borne de recharge de véhicule
électrique, élément clé du développement dans les villes de véhicules électriques. La borne de recharge
standard permet à un utilisateur de raccorder son véhicule électrique pour le recharger en toute sécurité et
rapidement. Elle dispose d’un ou deux socles de prises protégés par une trappe verrouillable, de voyants sur
la face avant (Disponible, Défaut) et sur le côté (Charge, Prise), de boutons poussoirs (Charge, Stop), de
transmission de données pour son exploitation et sa maintenance et d’un lecteur de badge pour identifier le
client (voir Annexe 1).
Dans ce système, le client doit s’enregistrer auprès de l’opérateur pour disposer d’un badge d’identification.
L’opérateur peut contrôler à distance l’ensemble de ses bornes par un système de communication GPRS/3G
(par exemple connaître l’ensemble des bornes hors service et les statistiques d’utilisation de chacune
d’elles).
Il existe 4 modes de recharge différents. Le schéma de charge retenu en France est la charge en mode 3 avec
un connecteur de type 3 côté borne fournissant un courant alternatif jusqu’à 500V de 3.6kVA (charge
normale) jusqu'à 22 kVA (charge accélérée) (voir Figure 2). Dans ce contexte, la charge des batteries du
véhicule est contrôlée par la borne de recharge.
Le fonctionnement concernant la recharge d’un véhicule est le suivant : Si la borne est disponible (voyant
« Disponible » allumé), le client s’authentifie : en cas de succès le voyant « Charge» clignote pendant 8 s,
sinon « Défaut » clignote rouge pendant 8 s. Le client dispose de 1 minute pour appuyer sur le bouton
« Charge ». Le voyant « disponible » est alors éteint. La trappe du socle de prises est déverrouillée, et
l’utilisateur peut connecter la prise à son véhicule. Une fois connectée, la prise est verrouillée et le voyant
« Prise » allumé. Commence ensuite le cycle de dialogue / charge avec le véhicule.
Le circuit de recharge dédié et imposé dans le « Mode 3 » est défini dans la proposition de norme IEC
61851-1 « ELECTRIC VEHICLE CONDUCTIVE CHARGING SYSTEM ». Cela permet de garantir une
sécurité maximale des utilisateurs lors de la recharge de leur véhicule électrique. La Figure 3 représente la
connectique entre une borne et un véhicule.
Un contrôleur de recharge, nommé générateur SAVE et situé côté infrastructure, vérifie les éléments
suivants avant d’enclencher la recharge :
Vérification que le véhicule est bien connecté au système (Etat B); Vérification que la masse du véhicule est
bien reliée au circuit de protection de l’installation (Etat C); Vérification de la cohérence des puissances
entre le câble, le véhicule et le circuit de recharge (Etat D); Détermination de la puissance maximale de
recharge qui sera allouée au véhicule.
L’ensemble de ces vérifications et de la communication se font au travers d’une communication sur fil
spécifique, dit « fil PILOTE ». Voir la représentation d’une prise Type 3 sur la Figure 2 et la connectique
entre la borne et le véhicule en Figure 3 (on notera la présence du connecteur S2 sur le véhicule). La figure
4 représente la valeur de la tension durant le processus.
Ainsi, la charge se fait en fonction du dialogue suivant entre le véhicule et la borne (Figure 4):
• Etat A : véhicule électrique non connecté, le générateur SAVE fournit une tension de + 12V. Le voyant
« charge » s’allume en rouge.
• Etat B : véhicule électrique connecté et système d’alimentation non disponible, la tension chute à +9V.
S2 est ouvert.
• Etat C : véhicule électrique connecté et système d’alimentation disponible, le générateur SAVE fournit
un signal carré +9V / -12V de fréquence 1 kHz qui aura pour effet de fermer le contacteur S2 sur le
véhicule.
• Etat D : S2 est fermé et engendre une nouvelle chute de tension à 6V. Le générateur SAVE fournit un
signal (+6V/-12V) de fréquence 1 kHz à rapport cyclique variable. (signal PWM modulation en largeur
d’impulsion). Ce rapport cyclique indique la puissance que la borne peut fournir au chargeur. La largeur
d’impulsion varie linéairement entre 100 us (6A fourni par la borne) et 800 us (48A). La position fermée
de S2 indique que le chargeur du véhicule électrique peut recevoir de l’énergie. La fermeture de S2
entraîne la fermeture d’un contacteur du circuit puissance sur la borne de recharge (AC). (il n’apparait
pas sur le schéma)
• Etat E : Quand le véhicule détecte que la batterie est chargée, S2 est ouvert. Le signal remonte à 9V/-
12V, indiquant à la borne d’ouvrir le contacteur AC. Le voyant « charge » s’allume en Vert.
• Etat F : retour à 12V quand la prise est déconnectée. Le voyant « charge » s’éteint.
Lors de la reprise du véhicule, le client s’identifie à nouveau sur la borne. Si le véhicule est encore en
charge, il appuie sur le bouton « Stop », sinon il peut le récupérer directement après l’avoir débranché. Le
contacteur AC doit être ouvert, la prise déverrouillée. Une fois la prise débranchée par le client, la trappe
doit être verrouillée, voyant « Prise » éteint et le voyant « disponible » allumé.
L’administrateur du système disposera d’une console de gestion des abonnements. Pour ajouter un nouveau
client celui-ci indiquera les informations personnelles du client (nom, etc …) et associera une carte dont la
lecture se fera par le lecteur de carte. Pour supprimer un client, l’administrateur lira la carte et procèdera à la
suppression du client associé.