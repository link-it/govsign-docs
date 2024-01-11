# Inviare una richiesta di firma

Ogni richiesta di firma è sempre collegata a un dossier e viene inviata al cittadino attraverso l'AppIO. All'interno dell'applicazione, il cittadino può consultare i documenti contenuti nella richiesta, visualizzare le firme previste, selezionare quelle desiderate e infine applicarle.

Per procedere alla creazione di una richiesta di firma sono necessari:

* Il codice fiscale del firmatario
* Il riferimento al dossier
* I documenti da firmare in formato PDF

È inoltre possibile specificare una data entro la quale il cittadino può completare il processo di firma (di default entro 3 mesi) e decidere se notificare la richiesta tramite un messaggio sull'AppIO.

{% hint style="info" %}
**Chi può creare una richiesta di firma?**

Affinché sia possibile creare una richiesta di firma, l'utente deve essere dotato del ruolo di _Request Editor_ per il dossier correlato alla richiesta che si intende creare.
{% endhint %}

Una volta create, le richieste di firma non possono più essere modificate, ma solo cancellate ed eventualmente ricreate. Le richieste vengono create in stato _**Draft**_ ed elaborate dal sistema fino alla loro pubblicazione, scarto o cancellazione.&#x20;

## Tramite applicazione web

Accedendo alla console di gestione è possibile creare una richiesta di firma accedendo al menù corrispondente e selezionando il pulsante **"Crea richiesta"**. Nella form conseguente è necessario inserire almeno i dati obbligatori.

{% hint style="info" %}
La console verifica a-priori che il firmatario disponga dell'AppIO necessaria alla firma. Un simbolo grafico a fianco del dato indica l'esito della verifica e la form potrà essere sottomessa solo in caso di esito positivo.
{% endhint %}

Completando la form si viene indirizzati alla pagina di dettaglio della richiesta appena creata potendo da qua monitorarne la lavorazione.

{% hint style="warning" %}
I tempi di pubblicazione dipendono dalla frequenza di esecuzione dei batch di elaborazione e dal carico del sistema.
{% endhint %}

## Tramite servizi REST

La creazione di una richiesta di firma si articola in tre fasi:

1. Verifica che il firmatario disponga dell'AppIO
2. Upload dei documenti PDF
3. Creazione della richiesta di firma

La verifica che il firmatario disponga dell'AppIO è opzionale ed evita che la successiva richiesta venga scartata per questo motivo.

{% swagger src="../.gitbook/assets/openapi (2).yaml" path="/utils/find-signer" method="post" %}
[openapi (2).yaml](<../.gitbook/assets/openapi (2).yaml>)
{% endswagger %}

Ciascun documento PDF previsto dal dossier deve essere poi caricato su sistema ed acquisito l'identificativo da utilizzare nella successiva richiesta di firma:

{% swagger src="../.gitbook/assets/openapi (2).yaml" path="/documents" method="post" %}
[openapi (2).yaml](<../.gitbook/assets/openapi (2).yaml>)
{% endswagger %}

Deve essere infine creata la richiesta di firma indicando la lista dei documenti caricati in precedenza. E' possibile in questa fase fornire dei metadati diversi da quelli previsti dal dossier, una data di scadenza della richiesta di firma e specificare se inviare un messaggio al firmatario in occasione della pubblicazione:

{% swagger src="../.gitbook/assets/openapi (2).yaml" path="/signature-requests" method="post" %}
[openapi (2).yaml](<../.gitbook/assets/openapi (2).yaml>)
{% endswagger %}
