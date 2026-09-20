# rp-files

## Scopo

L'unica astrazione di file dell'ecosistema: qualsiasi modulo che abbia bisogno di
"file" viene qui invece di creare una propria tabella di nomi e percorsi.
Mantiene metadati, raccolte ed elenchi di chunk; i byte stessi risiedono nello
storage a blocchi, raggiungibile tramite un client del servizio di storage.

## Modello mentale

File = record (nome, estensione, raccolta, proprietario) + elenco ordinato di riferimenti ai chunk
 nello storage a blocchi. Classificazione (`detectType`), materializzazione
e persistenza operano sui metadati — i byte vengono caricati solo quando realmente necessario
(staging del modello, servizio di download).

## Valore nell'ecosistema

Il punto di ingresso dell'acquisizione dei file:

- File, chunk, raccolte e metadati dietro un'unica API; i byte dei chunk sono delegati allo storage a blocchi.
- Qualsiasi dominio collega un id di file opaco alla propria entità invece di copiare i byte.

## Non obiettivi

- Non storage a blocchi grezzo — i byte dei chunk risiedono nel block store.
- Non decompressione di archivi o conversione di modelli.
## Confine di responsabilità

Possiede record di file, raccolte e ciclo di vita degli elenchi di chunk; non possiede
dettagli implementativi dell'object storage né trasformazioni di byte.

## Dipendenze dirette dei moduli

- Nessuna — i byte dei chunk passano tramite un client del servizio di storage, che è una chiamata
  di trasporto come quella effettuata da qualsiasi consumer esterno, non un collegamento modulo-a-modulo.
  rp-files mantiene nomi, raccolte e l'elenco dei chunk; non memorizza dati.

## Appartenenza alla soluzione

- `requests`

## Fonte

`modules/repositories/data/rp-files`