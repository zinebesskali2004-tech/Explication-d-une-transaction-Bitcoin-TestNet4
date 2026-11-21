# Explication-d-une-transaction-Bitcoin-TestNet4
Analyse et explication du fonctionnement d'une transaction Bitcoin sur le réseau de test TestNet4, de son émission à sa confirmation sur la blockchain.
Projet collectif : Analyse d'une transaction Bitcoin sur TestNet4
Informations générales
Formation : Master FINTECH / Blockchain
Encadrant : Pr. A. ELBASRI
Thème : Étude et analyse du fonctionnement d'une transaction Bitcoin sur TestNet4
Membres du groupe
Ouijdane Bouchkara
Imane BOUAARJA
Khaoula AGOUZAL
Amal Tabyi
Chaimaa Aaggour
Zineb Es-skali
Marouaa Maarouf
Introduction générale
Une transaction Bitcoin est une opération qui transfère une valeur en bitcoins d'une ou plusieurs sorties précédemment reçues vers de nouvelles sorties destinées à un ou plusieurs bénéficiaires. Contrairement à un système bancaire classique, Bitcoin ne fonctionne pas avec un solde centralisé par compte : le réseau vérifie plutôt des unités de valeur non dépensées, appelées UTXO.

Ce travail présente les éléments essentiels d'une transaction réalisée sur Bitcoin TestNet4 : les entrées (inputs), les sorties (outputs), les frais (fees), les confirmations et le mécanisme UTXO. L'objectif est de comprendre la structure d'une transaction et la manière dont elle est vérifiée et enregistrée sur la blockchain.

Précision méthodologique : TestNet4 est un réseau de test. Les bitcoins qui y circulent n'ont pas de valeur monétaire réelle et servent à expérimenter des transactions sans utiliser de vrais BTC. Les montants et les exemples numériques présentés dans ce travail sont illustratifs ; ils ne correspondent pas à une transaction réelle identifiée par un hash.

Partie 1 — Présentation de Bitcoin TestNet4
Bitcoin TestNet4 est un réseau alternatif destiné aux développeurs, étudiants et utilisateurs qui souhaitent tester le fonctionnement de Bitcoin. Il reprend les principales règles techniques du réseau Bitcoin, mais utilise des bitcoins de test.

Cela permet de créer des adresses, recevoir des fonds de test, construire des transactions et observer leur validation sans risquer de véritables fonds.

Pourquoi utiliser TestNet4 ?
Apprendre à envoyer et recevoir des bitcoins dans un environnement d'expérimentation.
Observer les détails d'une transaction à l'aide d'un explorateur de blocs compatible TestNet4.
Comprendre les entrées, les sorties, les frais et les confirmations.
Tester des applications ou des scripts avant de les utiliser sur le réseau principal.
Il faut veiller à sélectionner un explorateur compatible avec TestNet4 : les explorateurs du réseau principal Bitcoin et ceux des réseaux de test ne présentent pas nécessairement les mêmes transactions.

Partie 2 — Structure générale d'une transaction Bitcoin
Une transaction Bitcoin est un ensemble de données diffusé au réseau. Elle indique quelles sorties existantes sont utilisées comme entrées et quelles nouvelles sorties sont créées.

Elle contient notamment des références aux sorties dépensées, les scripts ou données de déverrouillage nécessaires, les montants affectés aux nouvelles sorties et des informations techniques.

Les principales étapes
L'utilisateur choisit une ou plusieurs sorties non dépensées qu'il contrôle.
Il construit une transaction qui référence ces sorties en tant qu'inputs.
Il définit une ou plusieurs outputs : paiement au destinataire et, généralement, monnaie rendue à l'expéditeur.
Il signe la transaction afin de prouver qu'il est autorisé à dépenser les inputs.
La transaction est diffusée au réseau, vérifiée par les nœuds, puis peut être incluse dans un bloc par un mineur.
Une transaction peut être consultée grâce à son identifiant, appelé TXID (Transaction ID), dans un explorateur compatible avec le réseau utilisé. Le TXID permet de retrouver les détails de la transaction.

Partie 3 — Inputs : les entrées de la transaction
Les inputs sont les entrées utilisées par une transaction. Chaque input fait référence à une sortie d'une transaction antérieure. Cette sortie antérieure doit encore être disponible, c'est-à-dire ne pas avoir déjà été dépensée.

Informations visibles dans un input
TXID précédent : identifiant de la transaction qui a créé la sortie utilisée.
Index de sortie (vout) : numéro qui permet d'identifier précisément la sortie concernée dans cette transaction.
Données de déverrouillage : éléments permettant de satisfaire les conditions de dépense, par exemple une signature numérique.
Exemple : si une transaction antérieure a créé deux sorties, numérotées 0 et 1, l'input peut référencer la sortie numéro 1 de cette transaction. Il ne consomme pas toute la transaction antérieure, mais cette sortie précise.

Une transaction peut contenir plusieurs inputs lorsque le montant à payer est supérieur à la valeur d'une seule sortie disponible. Les valeurs de tous les inputs sont alors additionnées.

Partie 4 — Outputs : les sorties de la transaction
Les outputs sont les nouvelles sorties créées par la transaction. Chaque output associe un montant en satoshis à une condition de dépense, généralement représentée par un script.

Cette condition indique qui pourra dépenser cette sortie et sous quelles conditions.

Les deux types de sorties les plus courants dans un paiement
Sortie destinée au bénéficiaire : elle contient le montant que l'expéditeur souhaite envoyer à l'adresse du destinataire.

Sortie de monnaie (change) : si les inputs totalisent davantage que le paiement et les frais, le reste peut être renvoyé vers une adresse contrôlée par l'expéditeur.

Exemple illustratif : une personne utilise un input de 0,01000000 BTC pour envoyer 0,00600000 BTC. Une partie peut être renvoyée à l'expéditeur sous forme de monnaie, tandis qu'une petite différence est prélevée comme frais.

Attention : la monnaie rendue n'est pas automatique dans tous les cas. Si la valeur des inputs est exactement égale au paiement plus les frais, aucune sortie de change n'est nécessaire.

Partie 5 — Frais de transaction (Fees)
Les frais de transaction sont la différence entre la valeur totale des inputs et la valeur totale des outputs. Ils rémunèrent indirectement les mineurs qui incluent les transactions dans les blocs.

Les frais ne sont pas calculés comme un pourcentage fixe du montant envoyé : ils dépendent principalement de la taille de la transaction en octets virtuels (vB) et du taux de frais choisi (sat/vB).

Formule
Frais = Somme des inputs − Somme des outputs

Exemple de calcul
Élément	Montant
Input total	100 000 satoshis
Output total	99 500 satoshis
Frais	500 satoshis
Dans cet exemple, les frais sont égaux à 100 000 − 99 500 = 500 satoshis.

Un satoshi est la plus petite unité de bitcoin :

1 BTC = 100 000 000 satoshis.

Le taux de frais est souvent exprimé en sat/vB. À taille égale, un taux plus élevé peut inciter les mineurs à traiter la transaction plus rapidement, surtout lorsque le réseau est encombré. Le délai n'est toutefois jamais garanti.

Partie 6 — Confirmations d'une transaction
Une transaction diffusée sur le réseau n'est pas immédiatement confirmée. Elle peut d'abord être transmise entre les nœuds et rester en attente dans le mempool, c'est-à-dire l'ensemble des transactions non encore incluses dans un bloc par un nœud donné.

Lorsqu'un mineur inclut la transaction dans un bloc accepté par le réseau, elle reçoit sa première confirmation. Chaque nouveau bloc ajouté après celui qui contient la transaction augmente son nombre de confirmations.

Comment interpréter les confirmations ?
0 confirmation : la transaction est diffusée ou en attente, mais n'est pas encore incluse dans un bloc confirmé.
1 confirmation : la transaction est incluse dans un bloc accepté.
Plusieurs confirmations : des blocs supplémentaires ont été ajoutés après le bloc contenant la transaction ; cela renforce la confiance dans son enregistrement.
Le nombre de confirmations est un indicateur de sécurité, mais il ne constitue pas une garantie mathématique absolue contre toute réorganisation de la chaîne.

Le niveau de confirmations attendu dépend du montant, du risque accepté et du contexte d'utilisation. Sur TestNet4, les confirmations servent surtout à observer et tester le mécanisme.

Partie 7 — UTXO : le modèle des sorties non dépensées
UTXO signifie Unspent Transaction Output, c'est-à-dire « sortie de transaction non dépensée ».

Bitcoin ne stocke pas le solde d'un utilisateur comme une ligne unique dans un compte bancaire. Le montant disponible est représenté par un ensemble de sorties non dépensées que l'utilisateur peut dépenser en respectant leurs conditions.

Fonctionnement du modèle UTXO
Une transaction crée une ou plusieurs outputs.
Tant qu'une output n'a pas été utilisée comme input, elle constitue un UTXO.
Lorsqu'une nouvelle transaction dépense cet UTXO, celui-ci est consommé et ne peut pas être dépensé une deuxième fois.
La nouvelle transaction crée à son tour de nouveaux outputs, qui pourront devenir de futurs UTXO.
Exemple simple
Supposons qu'une personne possède un UTXO de 100 000 satoshis. Elle l'utilise pour payer 60 000 satoshis et prévoit 1 000 satoshis de frais.

La transaction peut créer :

Une sortie de 60 000 satoshis pour le destinataire.
Une sortie de monnaie de 39 000 satoshis pour l'expéditeur.
100 000 = 60 000 + 39 000 + 1 000

L'ancien UTXO de 100 000 satoshis est dépensé. Les deux nouvelles sorties de 60 000 et 39 000 satoshis deviennent de nouveaux UTXO, jusqu'à ce qu'elles soient dépensées à leur tour.

Conclusion générale
L'étude d'une transaction Bitcoin sur TestNet4 permet de comprendre le fonctionnement concret du transfert de valeur sur une blockchain.

Les inputs identifient les sorties antérieures utilisées, tandis que les outputs définissent les nouvelles sorties créées. La différence entre la somme des inputs et celle des outputs correspond aux frais. Les confirmations indiquent l'intégration de la transaction dans la chaîne de blocs et le degré de profondeur de son enregistrement.

Enfin, le modèle UTXO explique comment Bitcoin suit les unités de valeur disponibles et empêche qu'une même sortie soit dépensée deux fois.

TestNet4 constitue donc un environnement pratique pour examiner ces mécanismes sans engager de bitcoins ayant une valeur réelle.

Répartition des contributions
Chaque membre du groupe participe à la réalisation du projet à travers une contribution identifiable sur GitHub.

Les contributions sont suivies à travers les Issues, les branches, les commits et les Pull Requests du dépôt collectif.

Projet réalisé dans le cadre du Master FINTECH / Blockchain

Encadrant : Pr. A. ELBASRI
