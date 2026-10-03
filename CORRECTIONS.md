# Corrections empreintes - 03/10/2026

## Modifications apportées au PCB

### 1. D1 ↔ D2 échangées
- **Problème** : D1 avait l'empreinte de la LED RGB, D2 avait celle de la diode
- **Correction** : références échangées
  - D1 = Diode_SMD:D_SMB (diode de protection)
  - D2 = LED_SMD:LED_Avago_PLCC6_3x2.8mm (LED RGB)
- **Note** : les noms de nets contiennent encore "D1" (ex: Net-(D1-RA)) car ils viennent du schéma. À renommer dans le schéma si besoin.

### 2. U4 → U6
- **Problème** : le PDF des consignes nomme le régulateur 5V "U6", le schéma utilisait "U4"
- **Correction** : U4 renommé en U6 (empreinte SOT-223 inchangée, correcte)

### 3. SW1 → BP1, SW2 → BP2
- **Problème** : le PDF nomme les boutons "BP1/BP2", le schéma utilisait "SW1/SW2"
- **Correction** : renommés (empreinte alcoswitch inchangée, correcte)

### 4. Q1 : NON CORRIGÉ ⚠️
- **Problème** : le schéma donne 3 nets à Q1 (+3.3V, /LED1, Net-(J4-Pin_2)) mais le phototransistor SFH3711 n'a que 2 pads
- **Action requise** : corriger le schéma (symbole et câblage de Q1) avant de router
- L'empreinte SOT-23 actuelle est conservée pour ne pas casser les connexions

### 5. F1 : non modifié
- L'empreinte `Fuse:Fuse_1812_4532Metric` a les bons pads (2 pads, /DCIN et /DCIN_F)
- Le PDF demande `Fusible1812:Fuse_1812` — les pads sont équivalents, pas bloquant pour le routage

## Fichiers
- `rKESSOULI.kicad_pcb` : PCB avec corrections ci-dessus, placement et routage d'origine conservés
- `rKESSOULI.kicad_sch` : schéma d'origine (non modifié — Q1 à corriger)
- `rKESSOULI.kicad_pro` : configuration projet

## Pour la suite
1. Corriger Q1 dans le schéma (symbole phototransistor à 2 pins)
2. Mettre à jour le PCB depuis le schéma
3. Vérifier la parité schéma/PCB
4. Router (les 6 nets critiques : +3.3V, +5V, /V_LAMPE, /LED1, /LED2, Net-(J4-Pin_2))
