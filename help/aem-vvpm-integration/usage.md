---
title: Utilizzo integrazione Veeva Vault
description: Utilizzo integrazione Veeva Vault
exl-id: efff7af1-eb25-4a1d-b7ef-52e3336970ff
source-git-commit: 19949a48cfee0c17481e52f286a460e9d81d7ff0
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---

# Utilizzo dell’integrazione

## Procedura dettagliata

Il video seguente descrive l’utilizzo del connettore:

>[!VIDEO](https://video.tv.adobe.com/v/332137/?quality=12&learn=on)

## Configurazione

Questa guida ti guiderà attraverso l’attivazione del connettore.

>[!IMPORTANT]
>
>Per ogni sistema, questi passaggi devono essere eseguiti da un **amministratore** per ogni sistema.
>
>I passaggi descritti in questa documentazione ti guideranno attraverso la creazione di integrazioni/registrazioni che richiedono l’assegnazione di autorizzazioni e/o l’accesso come amministratore.  È tua responsabilità accertarti che questi passaggi siano conformi alle politiche aziendali prima di eseguire e di eseguirli con attenzione.
>

### Installare il pacchetto di integrazione

Riceverai l’accesso al pacchetto di integrazione AEM. Sono disponibili due opzioni per installare l’integrazione:

1. **Installazione del pacchetto**: diretta e meno coinvolta.
2. **Installazione POM** - Più avanzata, ma può essere utile quando si utilizza AEM Cloud Manager e si aggiorna l&#39;integrazione.

#### Installazione pacchetto

Per installare il pacchetto, scaricalo con il collegamento fornito nell’e-mail di onboarding. [Per istruzioni dettagliate sull&#39;installazione di un pacchetto AEM, fare clic qui.](https://experienceleague.adobe.com/docs/experience-manager-64/administering/contentmanagement/package-manager.html?lang=it&#installing-packages)

#### Installazione POM

Per includere il connettore nel POM, eseguire la procedura seguente. Sostituisci nome utente e password con quelli ricevuti nell’e-mail di onboarding.

1. Aggiungi quanto segue al file `.cloudmanager/maven/settings.xml` nel progetto o a `~/.m2/settings.xml` nel computer. Sostituisci `YOUR_USERNAME` con il nome utente e `YOUR_PASSWORD` con la password fornita nell&#39;e-mail di onboarding.

   >[!IMPORTANT]
   >
   >Se utilizzi Cloud Manager, l&#39;approccio sicuro consiste nel seguire i passaggi qui descritti per [archivi Maven protetti da password](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/create-application-project/setting-up-project.html?lang=it#password-protected-maven-repositories).
   >

   ```
   <settings>
       ...
       <servers>
           ...
           <server>
               <id>repo.ea.adobe.net</id>
               <username>YOUR_USERNAME</username>
               <password>YOUR_PASSWORD</password>
               <filePermissions>BucketOwnerFullControl</filePermissions>
               <configuration>
                 <wagonProvider>s3</wagonProvider>
               </configuration>
           </server>
           ...
       </servers>
       ...
   </settings>
   ```

2. Aggiungi quanto segue al file `pom.xml` del progetto:

   ```
   <project>
       ...
       <build>
           ...
           <extensions>
               ...
               <extension>
                   <groupId>com.allogy.maven.wagon</groupId>
                   <artifactId>maven-s3-wagon</artifactId>
                   <version>1.2.0</version>
               </extension>
               ...
           </extensions>
           ...
       </build>
       ...
       <repositories>
           ...
           <repository>
               <id>repo.ea.adobe.net</id>
               <url>s3://repo.ea.adobe.net/release</url>
               <releases>
                   <enabled>true</enabled>
               </releases>
           </repository>
           ...
       </repositories>
       ...
   </project>
   ```

3. Aggiungi quanto segue al file `all/pom.xml` del progetto. Sostituire `project.dependencies.dependency.version` con la versione appropriata e `project.build.plugins.plugin.configuration.embeddeds.embedded.target` con il percorso corretto.

   ```
   <project>
       ...
       <build>
           ...
           <plugins>
               ...
               <plugin>
                   <groupId>org.apache.jackrabbit</groupId>
                   <artifactId>filevault-package-maven-plugin</artifactId>
                   ...
                   <configuration>
                       ...
                       <embeddeds>
                           ...
                           <embedded>
                               <groupId>com.adobe.acs.aemveeva</groupId>
                               <artifactId>aem-veeva-connector.all</artifactId>
                               <type>zip</type>
                               <target>/apps/APP_NAME-packages/application/install</target>
                           </embedded>
                           ...
                       </embeddeds>
                   </configuration>
               </plugin>
               ...
           </plugins>
           ...
       </build>
       ...
       <dependencies>
           ...
           <dependency>
               <groupId>com.adobe.acs.aemveeva</groupId>
               <artifactId>aem-veeva-connector.all</artifactId>
               <version>1.0.5</version>
               <type>zip</type>
           </dependency>            
           ...
       </dependencies>
       ...
   </project>
   ```

### Configurazione cloud

Questa integrazione viene configurata creando una configurazione cloud nella cartella su cui funzionerà il connettore. Per creare una configurazione cloud, effettua le seguenti operazioni:

1. Passa alla configurazione cloud Veeva.

   ![Passa a configurazione cloud](assets/cloud-config-navigate.png)

2. Crea una nuova configurazione cloud Veeva nella cartella appropriata e popola il come descritto nelle sezioni successive.

   ![Crea configurazione cloud](assets/cloud-config-create.png)

#### Scheda Configurazione

Compila quanto segue nella scheda di configurazione:

![Scheda Configurazione](assets/configuration-tab.png)

1. Obbligatorio. Titolo per la configurazione del connettore Veeva Vault. Questo può essere un valore arbitrario. (esempio: `Veeva Vault Configuration`)
2. Obbligatorio. URL del dominio dell&#39;istanza Veeva (esempio: `https://my-instance.veevavault.com/`)
3. Obbligatorio. ClientID richiesto per chiamare l’API Veeva Vault. Può essere un valore arbitrario ed è utilizzato principalmente per il debug. (esempio: `adobe-aem-vvtechpartner`)
4. Obbligatorio. Nome utente di Veeva Vault. Vedi [Creazione utente Veeva](#veeva-user-creation).
5. Obbligatorio. Password di Veeva Vault. Vedi [Creazione utente Veeva](#veeva-user-creation).

#### Scheda I/O Adobe

Se il progetto deve generare PDF o immagini per le pagine, è necessaria questa scheda. Compila quanto segue nella scheda adobe io:

![Scheda I/O Adobe](assets/adobe-io-tab.png)

1. Obbligatorio. L’endpoint di I/O Adobe per la creazione di immagini PDF fornito nell’e-mail di onboarding. (esempio: `https://my-namespace.adobeioruntime.net/api/v1/web/aem-veeva-serverless-0.0.2/trigger-action.json`)
2. Obbligatorio. Nome dell&#39;azione per la generazione dell&#39;immagine della pagina. Il valore deve essere `aem-veeva-integration/get-image-async`.
3. Obbligatorio. Nome dell’azione per la generazione di immagini html. Il valore deve essere `aem-veeva-integration/get-pdf-async-new`.
4. Obbligatorio. L’endpoint di I/O Adobe per ottenere lo stato della generazione fornito nell’e-mail di onboarding.(esempio: `https://my-namespace.adobeioruntime.net/api/v1/web/aem-veeva-serverless-0.0.2/get-state-value`)
5. Obbligatorio. Nome utente AEM da utilizzare per l&#39;Adobe I/O. Vedi [Creazione utente AEM](#aem-user-creation).
6. Obbligatorio. Password AEM da utilizzare per Adobe IO. Vedi [Creazione utente AEM](#aem-user-creation).
7. Facoltativo. Il timeout predefinito prevede che la pagina risponda fino a un determinato intervallo di tempo dopo il quale il servizio AIO smette di tentare di ottenere una risposta. Il valore predefinito è `30000`.
8. Facoltativo. Il ritardo si verifica dopo che la pagina ha risposto con 200 per ritardare il rendering di tutte le immagini prima di acquisire una schermata. Il valore predefinito è `2000`.
9. Facoltativo. L’URL generato da Screenshot/PDF scadrà dopo il valore configurato in secondi.
10. Facoltativo. Il servizio di generazione di PDF/screenshot I/O Adobe è asincrono. Il servizio AEM chiama l’endpoint di stato AIO per ottenere screenshot/PDF. Questa proprietà deciderà in millisecondi la pausa tra in ogni chiamata di stato. Il valore predefinito è `10000`.
11. Facoltativo. Numero massimo di tentativi per la chiamata di stato all’Adobe IO per ottenere screenshot/PDF. Il valore predefinito è `10`.

#### Scheda Avanzate

Compila quanto segue nella scheda Avanzate:

![Scheda Avanzate](assets/advanced-tab.png)

1. Obbligatorio per la generazione di PDF/immagini. Pattern di nome file utilizzato per la creazione di PDF/immagini. `{name}` può essere impostato come modello. (esempio: `{name}-screenshot`)
2. Facoltativo. I tipi di dispositivi per i quali sono necessarie schermate di pagina diverse da Desktop. I tipi validi includono `Tab (iPad)` e `Mobile (iPhone X)`.
3. Facoltativo. Il valore del tipo di rappresentazione in Veeva che rappresenta la rappresentazione precedente. (esempio: `web_ready__c`)
4. Obbligatorio per la generazione di PDF/immagini. Tipo di schermata da creare. `PDF` o `Image`.
5. Obbligatorio per la generazione di PDF/immagini. Tipo di PDF da generare. `Print CSS Based PDF` o `Pixel Perfect Screenshot PDF`.
6. Obbligatorio per la generazione di PDF/immagini. Tipo di immagine da generare. `PNG` o `JPEG`.
7. Obbligatorio. Flusso di lavoro da eseguire dopo il trigger di approvazione di Veeva Vault.
8. Obbligatorio. Valore della proprietà Status che rappresenta Approvato. (esempio: `Approved for Distribution`)
9. Obbligatorio. Flusso di lavoro da eseguire dopo il trigger Rifiuto di Veeva Vault.
10. Obbligatorio. Valore della proprietà Status che rappresenta Rifiutato/Non approvato. (esempio: `Rejected`)
11. Facoltativo. Nome proprietà per ID documento in Veeva Vault. Il valore predefinito è `id`.
12. Facoltativo. Nome proprietà per stato in Veeva Vault. Il valore predefinito è `status__v`.
13. Facoltativo. Nome proprietà per Data modifica documento. Il valore predefinito è `version_modified_date__v`.
14. Facoltativo. Nome della proprietà per l&#39;URL della risorsa documento. Il valore predefinito sarà `external_id__v`. Se questo campo è già utilizzato, crea un campo diverso in Veeva e compila qui il nome del campo. Questo campo verrà utilizzato in Veeva per contenere il percorso della risorsa AEM. Questo è necessario per la sincronizzazione automatica dei metadati.
15. Facoltativo. Nome proprietà per numero di versione principale in Veeva Vault. Il valore predefinito è `major_version_number__v`.
16. Facoltativo. Nome della proprietà per il numero di versione secondario in Veeva Vault. Il valore predefinito è `minor_version_number__v`.
17. Facoltativo. Valore del tipo di relazione Veeva Vault. Tutte le risorse aggiunte alla pagina verranno rappresentate come correlate in base a questo valore. Il valore predefinito è `supporting_document__c`.

#### Scheda Pagina

Se sincronizzi le pagine, compila quanto segue nella scheda della pagina:

![Scheda Pagina](assets/page-tab.png)

1. Obbligatorio. Mappa una proprietà da AEM a Veeva.
a. Nome della proprietà AEM. Selezionabile tra le proprietà AEM. (esempio: `jcr:title`) `{name}` può essere modellato.
b. Il nome della proprietà Veeva immesso esattamente in esiste in Veeva. (esempio: `name__v`)\
   c. Tipo di proprietà. `Text` o `Multiline Text`.

2. Obbligatorio. Mappa una proprietà da Veeva a AEM.
a. Il nome della proprietà Veeva immesso esattamente in esiste in Veeva. (esempio: `name__v`)
b. Nome della proprietà AEM. Selezionabile tra le proprietà AEM. (esempio: `jcr:title`)
c. Tipo di proprietà. `Text` o `Multiline Text`.


#### Scheda Risorsa

Per sincronizzare le risorse, compila quanto segue nella scheda delle risorse:

![Scheda Risorsa](assets/asset-tab.png)

1. Obbligatorio. Mappa una proprietà da AEM a Veeva.
a. Nome della proprietà AEM. Selezionabile tra le proprietà AEM. (esempio: `/jcr:content/metadata/jcr:title`) `{name}` può essere modellato.
b. Il nome della proprietà Veeva immesso esattamente in esiste in Veeva. (esempio: `name__v`)
c. Tipo di proprietà. `Text` o `Multiline Text`.

2. Obbligatorio. Mappa una proprietà da Veeva a AEM.
a. Il nome della proprietà Veeva immesso esattamente in esiste in Veeva. (esempio: `name__v`)
b. Nome della proprietà AEM. Selezionabile tra le proprietà AEM. (esempio: `/jcr:content/metadata/jcr:title`)
c. Tipo di proprietà. `Text` o `Multiline Text`.

### Configurazione aggiuntiva

#### Creazione di utenti AEM

Durante la generazione di PDF/immagini, è necessario creare un utente AEM per ottenere pagine dall’AEM. Per creare e assegnare autorizzazioni di sola lettura a un utente, utilizzare i collegamenti seguenti:

Se si utilizza AEM 6.5.5+:

* [Creazione di un utente in AEM](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/setup-organize-users/adding-configuring-users.html?lang=it&#create-a-user)
* [Aggiunta di autorizzazioni a un utente in AEM](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=it&#permissions-in-aem)

Se si utilizzano Cloud Service AEM:

* [Gestione di utenti con Cloud Service AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=it&#accessing)

Le seguenti autorizzazioni sono necessarie per l’utente del servizio AEM sul contenuto che verrà convertito in PDF/Immagine e inviato a Veeva:

* Lettura

>[!IMPORTANT]
>
> Queste azioni devono essere eseguite come amministratore per ciascun sistema.
> Quando crei utenti e imposti autorizzazioni, devi rispettare gli standard di sicurezza delle organizzazioni.
>

#### Creazione utente Veeva

Per utilizzare questa integrazione, è necessario creare un utente in Veeva Vault. Per creare un utente, effettua le seguenti operazioni:

1. Passa a Amministratore -> Utenti e gruppi -> Utenti Vault -> Crea

   ![Passa all&#39;utente Veeva](assets/veeva-user-navigate.png)

2. Compila gli input richiesti. La configurazione più semplice consiste nell&#39;impostare `License Type` su `Full User` e `Security Profile` su `Vault Owner`. Al termine, salva.

   ![Crea Utente Veeva](assets/veeva-user-create.png)

Per i tipi di documenti Veeva specifici in uso sono necessarie le seguenti autorizzazioni:

* Creare/leggere documenti
* Crea/Leggi versioni
* Crea/aggiorna metadati
* Crea/aggiorna rappresentazioni

>[!IMPORTANT]
>
> Queste azioni devono essere eseguite come amministratore per ciascun sistema.
> Quando crei utenti e imposti autorizzazioni, devi rispettare gli standard di sicurezza delle organizzazioni.
>
