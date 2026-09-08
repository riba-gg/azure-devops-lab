# Consegna UD02 — Laboratorio autonomo

## Requisito e piano

* requisito interpretato: Creare un ambiente isolato e temporaneo per lo sviluppo, separato dagli altri laboratori e facilmente eliminabile come singola unità.
* risorse previste: Resource Group, VNet (`10.30.0.0/16`), Subnet (`10.30.10.0/24`) e Storage Account (`StorageV2`, `Standard_LRS`, HTTPS obbligatorio, TLS 1.2, accesso blob pubblico disabilitato).
* nomi e tag scelti: `rg-cea-ud02-auto-<suffisso>`, `vnet-cea-auto`, `snet-workload`, `stceaauto<suffisso>`. Tag: `course=cloud-engineer-academy`, `unit=UD02`, `environment=dev`, `scenario=autonomous`, `deleteAfter`.
* verifiche preliminari: Controllo dello stato della sottoscrizione con `az account show` e recupero della località dal file di variabili condiviso.

## Svolgimento

* **Creazione RG e Rete**: Eseguito `az group create` e `az network vnet create` con i prefissi IP richiesti.
* **Creazione Storage**: Provisioning dello Storage Account con HTTPS obbligatorio, TLS 1.2 e accesso pubblico disabilitato tramite CLI.
* **Verifica Portale**: Controllo incrociato tramite Azure Portal per confermare la presenza delle risorse e dei tag associati.

## Diagnosi

* errore o anomalia analizzata: Conflitto iniziale sul nome dello storage account e configurazione incompleta dell'accesso pubblico da portale.
* ipotesi: Nome non unico a livello globale e opzioni di sicurezza non intercettate correttamente nella GUI.
* controllo: Verifica dei comandi CLI e dei messaggi di errore di Azure.
* correzione: Introduzione del suffisso casuale basato su hash e aggiornamento forzato dei parametri di sicurezza via CLI/portale.
* verifica successiva: Configurazione corretta confermata dai comandi `az network vnet show` e `az storage account show`.

## Cleanup e consegna

* risorse eliminate: Resource Group e tutte le risorse al suo interno.
* controllo finale: `az group exists` restituito con valore `false`.
* hash abbreviato e messaggio del commit: `git commit -m "Completa lo scenario Azure autonomo"`