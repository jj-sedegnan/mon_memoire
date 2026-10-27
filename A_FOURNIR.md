# Informations à fournir pour finaliser le mémoire

Inventaire au 28 octobre 2026 (après figement du chapitre 3 en protocole).
État des marqueurs dans les sources :
**57 `\acompleter`, 35 `\amesurer`, 10 blocs `\preuves`**. Aucune valeur ci-dessous
ne peut être inventée : chaque entrée doit correspondre à un document, une
mesure ou une information réellement obtenus.

**Fait acté : le laboratoire n'a pas été monté et aucun test n'a été exécuté.**
Le chapitre 3 est donc un protocole expérimental complet et reproductible :
les 35 cellules « à mesurer » ne seront remplies que si le protocole est joué
avant le dépôt. Si tel n'est pas le cas, elles doivent rester telles quelles :
le mémoire est scientifiquement défendable en l'état, car il n'affirme aucune
mesure.

Légende des priorités : **P0 = bloquant pour le dépôt** · P1 = requis pour un
chapitre 3 complet · P2 = qualité/harmonisation.

---

## A. Éléments administratifs et personnels (P0)

| # | Information | Fichier / emplacement |
|---|---|---|
| A1 | Date de soutenance | `main.tex` (`\dateSoutenance`) |
| A2 | Encadrant IFRI et tuteur de stage : nom, prénom, fonction | `main.tex` (`\encadrants`) |
| A3 | Jury : président, examinateur, rapporteur (nom, grade, entité) | `main.tex` (`\jurys`) |
| A4 | Texte de la dédicace | `0-dedicace.tex` |
| A5 | Remerciements personnels (direction IFRI, jury, famille) | `1-remerciements.tex` |
| A6 | Noms et fonctions exacts : cheffe CSI, chef UGRIM, collègues | `1-remerciements.tex` |
| A7 | Durée et dates du stage, date de début et modalités d'intégration | `3-introduction.tex`, `1-partie/1-fichier.tex` |
| A8 | Part exacte de vos tâches au sein de l'UGRIM | `1-partie/1-fichier.tex` |
| A9 | Autorisation de stage signée (périmètre, découverte réseau, interdiction d'intrusion, anonymisation) | annexe H |
| A10 | Accords de citation : rapport Kaho 2026, schéma d'architecture interne | `biblio.bib` (clés `kaho2026`, `archi`) |

## B. Données de l'audit réseau et entretiens avec le service (P0/P1)

| # | Information | Fichier / emplacement |
|---|---|---|
| B1 | Sorties Nmap brutes (`nmap -sn`, `nmap -sV` sur les 7 ports) | annexe E |
| B2 | Tableau de synthèse constructeur / nombre d'hôtes (extrait du scan) | `2-partie/1-fichier.tex` |
| B3 | Modèle exact du switch fédérateur Dell et support du port miroir | `2-partie/1-fichier.tex` |
| B4 | État et périmètre des travaux de segmentation par VLAN en cours | `2-partie/1-fichier.tex` |
| B5 | État actuel de la fusion CNHU-HKM / HIA de Cotonou | `1-partie/1-fichier.tex` |
| B6 | Correspondance CSI / « cellule informatique » du décret, effectifs et parc géré | `1-partie/1-fichier.tex` |
| B7 | Inventaire par zone fonctionnelle, type d'équipement, criticité | `2-partie/1-fichier.tex` |
| B8 | Flux métiers réels (SIH, imagerie, messagerie) et ports applicatifs DICOM/HL7 | `2-partie/1-fichier.tex`, matrice de flux (annexe F) |
| B9 | Validation des cotations EBIOS (R1 à R4) par le tuteur | `2-partie/1-fichier.tex` |
| B10 | Confirmation du besoin exprimé par le tuteur à l'origine du sujet | `1-partie/1-fichier.tex` |
| B11 | Schémas réseau validés par le service (avant/après, idéalement vectoriels) | annexe G |
| B12 | Nombre de semaines effectives et dates des 5 phases (journal de bord) | `2-partie/1-fichier.tex`, annexe A |

## C. Preuves expérimentales du laboratoire (P0/P1) — chemin critique

Si le laboratoire n'a pas été exécuté, ces éléments ne peuvent pas exister : le
chapitre 3 reste alors un **protocole proposé** (déjà formulé comme tel) et le
tableau de résultats doit conserver ses 35 mentions « à mesurer ».

| # | Information / preuve | Fichier / emplacement |
|---|---|---|
| C1 | Version d'Ubuntu Server, RAM et cœurs de l'hôte | `3-partie/1-fichier.tex` |
| C2 | Outil de topologie retenu : GNS3 **ou** EVE-NG | `3-partie/1-fichier.tex` |
| C3 | Version d'OPNsense et mode de partitionnement ZFS | `3-partie/1-fichier.tex` |
| C4 | Ressources (vCPU/RAM) des 6 machines virtuelles | `3-partie/1-fichier.tex`, tableau `tab:vms` |
| C5 | Durcissement commutateur effectivement activé | `3-partie/1-fichier.tex` |
| C6 | Résultat de `egrep -c '(vmx|svm)' /proc/cpuinfo` et `virsh list --all` | bloc preuve § virtualisation |
| C7 | Configurations exportées : OPNsense `config.xml`, Suricata, pont réseau | annexe C |
| C8 | Résultat de `suricata -T` (code retour et sortie) et variables d'adresses | règle/commandes ch. 3 |
| C9 | Pour S1–S7, états A/B/C : commande, sortie, alerte `eve.json` horodatée, blocage IPS | tableau `tab:resultats` (35 cellules), annexe E |
| C10 | Faux positifs avant/après réglage, règles désactivées et justification | § réglage IDS |
| C11 | Mesure de latence/débit avant et après activation IPS | § passage en IPS |
| C12 | Tableau de bord Wazuh : alerte Suricata visible, réponse active si utilisée | § Wazuh |
| C13 | Journal des incidents d'exécution futurs (message d'erreur exact, cause, solution, temps perdu) — les difficultés *anticipées* et leurs mitigations sont déjà rédigées | § difficultés anticipées |
| C14 | Estimation des moyens matériels et humains pour le déploiement | § recommandations |

**Déjà traité sans donnée (ne plus fournir) :** le cadre d'interprétation des
indicateurs, les difficultés anticipées et leurs mitigations, les phrases de
statut des résumés FR/EN, de la conclusion générale et de la conclusion du
chapitre 3 sont rédigés et indiquent explicitement que l'évaluation n'a pas
été exécutée.

---

## Ordre de traitement recommandé

1. **A1–A10** : débloquables immédiatement par vos soins (1 jour).
2. **B1–B12** : à partir des archives de stage et d'un entretien tuteur (1 jour).
3. **C1–C15** : exécuter le protocole du chapitre 3 et collecter les preuves ;
   c'est le seul lot qui dépend de manipulations réelles.
4. Après livraison de chaque lot, les marqueurs correspondants sont remplacés
   par les valeurs réelles et supprimés ; le compteur de marqueurs doit tomber
   à zéro avant le dépôt.
