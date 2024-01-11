# Creare un dossier

Un dossier è un contenitore che identifica l'**insieme dei metadati dei documenti** da firmare all'interno di una richiesta di firma. Ti consente di raggruppare le richieste di firma per tipologia di contratto.&#x20;

Ciascun dossier rappresenta un **caso d’uso specifico**. Ad esempio, potresti creare un dossier per i documenti delle borse di studio, denominato “_**Richiesta Borsa di studio”**_, e un altro _**“Contratto di assunzione”**_ per i contratti di collaborazione. In questo modo, è possibile creare le richieste di firma verso gli utenti riutilizzando lo stesso dossier.&#x20;

## Creare un dossier

{% hint style="info" %}
**Chi può creare i dossier?**

Affinché sia possibile creare un dossier, l'utente deve essere dotato del ruolo di _Dossier Editor_ nell'organizzazione correlata al dossier che si intende creare.
{% endhint %}

Per creare un Dossier devono essere individuati:

* Un titolo di massimo 75 caratteri, es “_**Contratto 150 ore”**_
* Un codice di riferimento, es “_**DPT-XII-CON-150h”**_
* Una email di assistenza per gli utenti firmatari (opzionale)
* Una email a cui notificare l'avvenuta firma (opzionale)
* I metadati di ciascun documento da firmare:
  * Un titolo di massimo 60 caratteri, es “_**Contratto”**_
  * Opzionalmente l'elenco delle firme previste e la loro posizione all'interno del documento.

Le informazioni presenti nei metadati dei documenti possono essere soggette a modifiche durante una richiesta di firma. È fortemente consigliabile progettare i documenti PDF destinati alla firma in modo tale che i metadati rimangano invariati, riducendo così la necessità di modificarli nelle richieste successive.

{% hint style="info" %}
**Cosa accade se non si specificano le firme previste?**

In questo caso l’utente potrà inserire **una sola firma digitale su tutto il documento** che però **non avrà alcun corrispettivo grafico** (firma trasparente).
{% endhint %}

{% swagger src="../.gitbook/assets/openapi (2).yaml" path="/dossiers" method="post" %}
[openapi (2).yaml](<../.gitbook/assets/openapi (2).yaml>)
{% endswagger %}

## Creare una nuova versione

Non è possibile modificare un dossier, ma è possibile crearne una nuova versione mantenedo il medesimo "Codice di riferimento".&#x20;
