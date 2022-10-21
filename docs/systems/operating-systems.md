# Operating systems

## Linux system booting process

### Linux UEFI BIOS loading process

- SEC Phase : C’est la phase d’initialisation où rien n’est exécuté. Il s’agit
de vérifier le matériel.

- PEI Phase : elle prépare la plate-forme pour l’initialisation du système
principal dans la phase DXE.

- DXE Phase : Cette phase exécute des pilotes basée sur les ressources
découvertes et décrites dans la phase PEI.

- BDS : On localise le l’OS Boot Manager depuis les périphériques de
démarrage (USB, Disque locaux ou réseau). La partition EFI est trouvée
et le firmware shim est chargé, si sa signature numérique est valide.


## Windows system booting process

