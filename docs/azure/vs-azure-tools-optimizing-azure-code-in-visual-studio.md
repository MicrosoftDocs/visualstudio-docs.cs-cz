---
title: Optimalizace kódu Azure
description: Přečtěte si, jak nástroje pro optimalizaci kódu Azure v Sadě Visual Studio pomáhají, aby byl váš kód robustnější a výkonnější.
author: ghogen
manager: jillfra
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: e42a746761b09e99e158ecef8e9054bc0049c03d
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489633"
---
# <a name="optimizing-your-azure-code"></a>Optimalizace kódu Azure
Když programujete aplikace, které používají Microsoft Azure, existují některé postupy kódování, které byste měli dodržovat, abyste se vyhnuli problémům s škálovatelností aplikací, chováním a výkonem v cloudovém prostředí. Společnost Microsoft poskytuje nástroj Azure Code Analysis, který rozpozná a identifikuje několik těchto běžně se vyskytujících problémů a pomůže vám je vyřešit. Nástroj si můžete stáhnout v sadě Visual Studio přes NuGet.

## <a name="azure-code-analysis-rules"></a>Pravidla analýzy kódu Azure
Nástroj Azure Code Analysis používá následující pravidla k automatickému označení kódu Azure, když zjistí známé problémy s dopadem na výkon. Zjištěné problémy se zobrazují jako upozornění nebo chyby kompilátoru. Opravy kódu nebo návrhy k vyřešení upozornění nebo chyby jsou často poskytovány prostřednictvím ikony žárovky.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Vyhněte se použití výchozího stavu relace (v procesu)
### <a name="id"></a>ID
AP0000

### <a name="description"></a>Popis
Pokud pro cloudové aplikace použijete výchozí (v procesu) režim stavu relace, můžete ztratit stav relace.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
Ve výchozím nastavení je režim stavu relace zadaný v souboru web.config v procesu. Pokud není v konfiguračním souboru zadána žádná položka, je režim stavu relace výchozí pro proces v procesu. Režim v procesu ukládá stav relace do paměti na webovém serveru. Při restartování instance nebo nové instance se používá pro vyrovnávání zatížení nebo podporu převzetí služeb při selhání, stav relace uložené v paměti na webovém serveru není uložen. Tato situace zabraňuje aplikace škálovatelné v cloudu.

ASP.NET stavu relace podporuje několik různých možností úložiště pro data stavu relace: InProc, StateServer, SQLServer, Vlastní a Vypnuto. Doporučujeme použít vlastní režim k hostování dat v externím úložišti stavu relace, jako je například [zprostředkovatel stavu relace Azure pro Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/).

### <a name="solution"></a>Řešení
Jedním z doporučených řešení je uložení stavu relace ve službě spravované mezipaměti. Přečtěte si, jak použít [zprostředkovatele stavu relace Azure pro Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) k uložení stavu relace. Můžete také uložit stav relace na jiných místech, abyste zajistili, že vaše aplikace je škálovatelná v cloudu. Další informace o alternativních řešeních naleznete v [části Režimy stavu relace](https://msdn.microsoft.com/library/ms178586).

## <a name="run-method-should-not-be-async"></a>Spustit metodu by neměla být asynchronní
### <a name="id"></a>ID
AP1000

### <a name="description"></a>Popis
Vytvořte asynchronní metody [(například await)](https://msdn.microsoft.com/library/hh156528.aspx)mimo [metodu Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) a potom volejte asynchronní metody z [Run().](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Deklarování [[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metoda jako asynchronní způsobí, že role pracovního procesu zadat restart smyčky.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
Volání asynchronních metod uvnitř metody [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) způsobí, že modul runtime cloudové služby recykluje roli pracovního procesu. Při spuštění role pracovního procesu probíhá veškeré spuštění programu uvnitř metody [Run().](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Ukončení [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Metoda způsobí restartování role pracovního procesu. Když modul runtime role pracovního procesu narazí na asynchronní metodu, odešle všechny operace po asynchronní metodě a poté vrátí. To způsobí, že role pracovního procesu ukončit z [[[[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metoda a restartování. V další iteraci provádění role pracovního procesu znovu zasáhne asynchronní metodu a restartuje se, což způsobí, že role pracovního procesu bude také znovu recyklovat.

### <a name="solution"></a>Řešení
Umístěte všechny asynchronní operace mimo [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metoda. Potom volání refaktorované asynchronní metody z vnitřní [[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metoda, jako je například RunAsync().wait. Nástroj Analýza kódu Azure vám může pomoci tento problém vyřešit.

Následující fragment kódu ukazuje opravu kódu pro tento problém:

```csharp
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("https://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Použití ověřování sdíleného přístupového podpisu služby Service Bus
### <a name="id"></a>ID
AP2000

### <a name="description"></a>Popis
Pro ověřování použijte sdílený přístupový podpis (SAS). Služba řízení přístupu (ACS) se již zastaralá pro ověřování sběrnice.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
Z důvodu rozšířeného zabezpečení nahrazuje služba Azure Active Directory ověřování služby ACS ověřováním SAS. Informace o plánu přechodu najdete [v tématu Azure Active Directory je budoucnost služby ACS.](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/)

### <a name="solution"></a>Řešení
Ve svých aplikacích používejte ověřování SAS. Následující příklad ukazuje, jak použít existující token SAS pro přístup k oboru názvů nebo entitě služby Service Bus.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Další informace naleznete v následujících tématech.

* Přehled najdete v tématu [Ověřování podpisů sdíleného přístupu pomocí služby Service Bus.](https://msdn.microsoft.com/library/dn170477.aspx)
* [Použití ověřování podpisu sdíleného přístupu se službou Service Bus](https://msdn.microsoft.com/library/dn205161.aspx)
* Ukázkový projekt najdete v tématu [Použití ověřování sdíleného přístupového podpisu (SAS) s předplatným služby Service Bus](https://code.msdn.microsoft.com/windowsapps/Shared-Access-Signature-0a88adf8)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Zvažte použití metody OnMessage, abyste se vyhnuli "přijímací smyčce"
### <a name="id"></a>ID
AP2002

### <a name="description"></a>Popis
Chcete-li se vyhnout vstupu do "přijímat smyčky", volání **OnMessage** metoda je lepší řešení pro příjem zpráv, než volání **Receive** metoda. Pokud je však nutné použít metodu **Receive** a zadáte dobu čekání serveru, která není výchozí, ujistěte se, že čekací doba serveru je delší než jedna minuta.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
Při volání **OnMessage**klient spustí interní zprávu čerpadlo, které neustále dotazuje fronty nebo odběr. Tato zpráva čerpadlo obsahuje nekonečnou smyčku, která vydává volání přijímat zprávy. Pokud je časový rozsah volání, vydá nový hovor. Časový interval je určen hodnotou [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) vlastnost [MessagingFactory,](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)která je používána.

Výhodou použití **OnMessage** ve srovnání s **Receive** je, že uživatelé nemusí ručně dotazování na zprávy, zpracovávat výjimky, zpracovávat více zpráv paralelně a dokončit zprávy.

Pokud voláte **Receive** bez použití jeho výchozí hodnoty, ujistěte se, že hodnota *ServerWaitTime* je delší než jedna minuta. Nastavení *služby ServerWaitTime* na více než jednu minutu zabrání serveru v vypršení časového limitu před úplné přijetí zprávy.

### <a name="solution"></a>Řešení
Naleznete v následujících příkladech kódu pro doporučená použití. Další podrobnosti naleznete v [tématech QueueClient.OnMessage Method (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx) a [QueueClient.Receive Method (Microsoft.ServiceBus.Messaging).](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx)

Pokud chcete zlepšit výkon infrastruktury zasílání zpráv Azure, podívejte se na návrhový vzor [Asynchronní messaging Primer](https://msdn.microsoft.com/library/dn589781.aspx).

Následuje příklad použití **OnMessage** pro příjem zpráv.

```csharp
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is received, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

Následuje příklad použití **receive** s výchozí dobu čekání serveru.

```csharp
string connectionString =
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)
{
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

Následuje příklad použití **receive** s nevýchozí čekací dobou serveru.

```csharp
while (true)
{
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```

## <a name="consider-using-asynchronous-service-bus-methods"></a>Zvažte použití asynchronních metod sběrnice Service Bus
### <a name="id"></a>ID
AP2003

### <a name="description"></a>Popis
Pomocí asynchronních metod service bus můžete zlepšit výkon pomocí zprostředkovaného zasílání zpráv.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
Použití asynchronních metod umožňuje souběžnost aplikačního programu, protože spuštění každého volání neblokuje hlavní vlákno. Při použití service bus zasílání zpráv metody, provádění operace (odeslat, přijmout, odstranit, atd.) nějakou dobu trvá. Tento čas zahrnuje zpracování operace službou Service Bus kromě latence požadavku a odpovědi. Chcete-li zvýšit počet operací za čas, operace musí provádět souběžně. Další informace naleznete [v doporučených postupech pro zlepšení výkonu pomocí služby Service Bus brokered Messaging](https://msdn.microsoft.com/library/azure/hh528527.aspx).

### <a name="solution"></a>Řešení
Informace o použití doporučené asynchronní metody naleznete v části Třída klienta [QueueClient (Microsoft.ServiceBus.Messaging).](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx)

Pokud chcete zlepšit výkon infrastruktury zasílání zpráv Azure, podívejte se na návrhový vzor [Asynchronní messaging Primer](https://msdn.microsoft.com/library/dn589781.aspx).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Zvažte rozdělení front a témat služby Service Bus
### <a name="id"></a>ID
AP2004

### <a name="description"></a>Popis
Fronty a témata sběrnice oddílů pro lepší výkon se zasíláním zpráv service bus.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
Dělení fronty service bus a témata zvyšuje propustnost výkonu a dostupnost služeb, protože celková propustnost rozdělené fronty nebo tématu již není omezena výkonem jednoho zprostředkovatele zpráv nebo úložiště zpráv. Dočasný výpadek úložiště zpráv navíc neznepřístupní rozdělenou frontu nebo téma. Další informace naleznete [v tématu Partitioning Messaging Entitiing .](https://msdn.microsoft.com/library/azure/dn520246.aspx)

### <a name="solution"></a>Řešení
Následující fragment kódu ukazuje, jak rozdělit entity zasílání zpráv.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Další informace naleznete v tématu [Partitioned Service Bus Fronty a témata | Blog Microsoft Azure](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) a podívejte se na ukázku [fronty rozdělené na příčku služby Microsoft Azure Service Bus.](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f)

## <a name="do-not-set-sharedaccessstarttime"></a>Nenastavovat soubor SharedAccessStartTime
### <a name="id"></a>ID
AP3001

### <a name="description"></a>Popis
Měli byste se vyhnout použití SharedAccessStartTimeset na aktuální čas okamžitě spustit zásady sdíleného přístupu. Tuto vlastnost je třeba nastavit pouze v případě, že chcete později spustit zásady sdíleného přístupu.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
Synchronizace hodin způsobuje mírný časový rozdíl mezi datovými centry. Například byste logicky uvažovat nastavení počáteční čas zásady úložiště SAS jako aktuální čas pomocí DateTime.Now nebo podobná metoda způsobí, že zásady SAS se projeví okamžitě. Však mírné časové rozdíly mezi datovými centry může způsobit problémy s tím, protože některé časy datového centra může být o něco později než čas zahájení, zatímco jiní před ním. V důsledku toho může platnost zásad SAS rychle (nebo dokonce okamžitě), pokud je životnost zásad nastavena příliš krátkou.

Další pokyny k používání sdíleného přístupového podpisu v úložišti Azure najdete v [tématu Zavedení tabulky SAS (sdílený přístupový podpis), SAS fronty a aktualizace na blob SAS – blog týmu úložiště Microsoft Azure – domov webu – blogy MSDN](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Řešení
Odeberte příkaz, který nastavuje čas zahájení zásad y sdíleného přístupu. Nástroj Analýza kódu Azure poskytuje opravu tohoto problému. Další informace o správě zabezpečení naleznete v návrhovém vzoru [Vzor klíče pro valet .](https://msdn.microsoft.com/library/dn568102.aspx)

Následující fragment kódu ukazuje opravu kódu pro tento problém.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Doba vypršení platnosti zásad sdíleného přístupu musí být delší než pět minut.
### <a name="id"></a>ID
AP3002

### <a name="description"></a>Popis
Může existovat až pětiminutový rozdíl v hodinách mezi datovými centry na různých místech z důvodu stavu známého jako "zkosení hodin". Chcete-li zabránit vypršení platnosti tokenu zásad SAS dříve, než bylo plánováno, nastavte dobu vypršení platnosti na více než pět minut.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
Datová centra na různých místech po celém světě se synchronizují pomocí hodinového signálu. Vzhledem k tomu, že trvá čas, než se hodinový signál dostane do různých umístění, může existovat časová odchylka mezi datovými centry v různých zeměpisných umístěních, i když vše je údajně synchronizováno. Tento časový rozdíl může ovlivnit čas zahájení zásad sdíleného přístupu a interval vypršení platnosti. Chcete-li tedy zajistit, aby se zásady sdíleného přístupu projevily okamžitě, nezadávejte čas zahájení. Kromě toho se ujistěte, že doba vypršení platnosti je více než 5 minut, aby se zabránilo předčasnému vypršení časového ochazu.

Další informace o používání sdíleného přístupového podpisu v úložišti Azure najdete [v tématu Zavedení tabulky SAS (sdílený přístupový podpis), SAS fronty a aktualizace na blob SAS – blog týmu úložiště Microsoft Azure – domov webu – blogy MSDN](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Řešení
Další informace o správě zabezpečení naleznete v návrhovém vzoru [Vzor klíče pro valet .](https://msdn.microsoft.com/library/dn568102.aspx)

Následuje příklad neurčení času zahájení zásad sdíleného přístupu.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Následuje příklad určení času zahájení zásad sdíleného přístupu s dobou vypršení platnosti zásad delší než pět minut.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Další informace naleznete v [tématu Vytvoření a použití sdíleného přístupového podpisu](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>Použití cloudconfigurationmanageru
### <a name="id"></a>ID
AP4000

### <a name="description"></a>Popis
Použití [třídy ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) pro projekty, jako je web Azure a mobilní služby Azure, nezavede problémy s časem. Jako osvědčený postup je však vhodné použít Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) jako jednotný způsob správy konfigurací pro všechny aplikace Azure Cloud.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
CloudConfigurationManager přečte konfigurační soubor odpovídající aplikačnímu prostředí.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Řešení
Refaktorujte kód tak, aby používal [třídu CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx). Oprava kódu pro tento problém je poskytována nástrojem Azure Code Analysis.

Následující fragment kódu ukazuje opravu kódu pro tento problém. Nahradit

`var settings = ConfigurationManager.AppSettings["mySettings"];`

with

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Tady je příklad uložení nastavení konfigurace do souboru App.config nebo Web.config. Přidejte nastavení do části appSettings konfiguračního souboru. Následuje soubor Web.config pro předchozí příklad kódu.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Vyhněte se použití pevně zakódovaných připojovacích řetězců
### <a name="id"></a>ID
AP4001

### <a name="description"></a>Popis
Pokud používáte pevně zakódované připojovací řetězce a potřebujete je později aktualizovat, budete muset provést změny zdrojového kódu a znovu zkompilovat aplikaci. Pokud však připojovací řetězce uložíte do konfiguračního souboru, můžete je později změnit pouhou aktualizací konfiguračního souboru.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
Pevné kódování připojovacířetězce je špatná praxe, protože zavádí problémy, když spojovací řetězce je třeba změnit rychle. Kromě toho pokud projekt potřebuje vrácení se změnami do správy zdrojového kódu, pevně zakódované připojovací řetězce zavádějí chyby zabezpečení, protože řetězce lze zobrazit ve zdrojovém kódu.

### <a name="solution"></a>Řešení
Uklápěte připojovací řetězce do konfiguračních souborů nebo prostředí Azure.

* U samostatných aplikací můžete pomocí souboru app.config uložit nastavení připojovacího řetězce.
* Pro webové aplikace hostované službou IIS použijte web.config k ukládání připojovacích řetězců.
* Pro ASP.NET vNext aplikace, použijte configuration.json pro ukládání připojovacích řetězců.

Informace o použití konfiguračních souborů, jako je web.config nebo app.config, naleznete [v tématu ASP.NET Pokyny pro konfiguraci webu](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations). Informace o tom, jak proměnné prostředí Azure fungují, najdete [v tématu Azure Web Sites: Jak fungují řetězce aplikací a připojovací řetězce](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Informace o ukládání připojovacího řetězce do správy zdrojového kódu naleznete v [tématu vyhněte se vkládání citlivých informací, jako jsou připojovací řetězce, do souborů, které jsou uloženy v úložišti zdrojového kódu](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Použití konfiguračního souboru diagnostiky
### <a name="id"></a>ID
AP5000

### <a name="description"></a>Popis
Namísto konfigurace nastavení diagnostiky v kódu, například pomocí rozhraní API pro programování Microsoft.WindowsAzure.Diagnostics, byste měli nakonfigurovat nastavení diagnostiky v souboru diagnostics.wadcfg. (Nebo diagnostics.wadcfgx pokud používáte Azure SDK 2.5). Tímto způsobem můžete změnit nastavení diagnostiky bez nutnosti překompilovat kód.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
Před Azure SDK 2.5 (který používá Diagnostika Azure 1.3), Azure Diagnostics (WAD) lze nakonfigurovat pomocí několika různých metod: přidání do objektu blob konfigurace v úložišti, pomocí imperativní kód, deklarativní konfigurace nebo výchozí konfigurace. Upřednostňovaným způsobem konfigurace diagnostiky je však použití konfiguračního souboru XML (diagnostics.wadcfg nebo diagnostics.wadcfgx pro sdchartu 2.5 a novější) v projektu aplikace. V tomto přístupu soubor diagnostics.wadcfg zcela definuje konfiguraci a lze aktualizovat a znovu nasadit podle vůle. Míchání použití konfiguračního souboru diagnostics.wadcfg s programovými metodami nastavení konfigurací pomocí tříd [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)nebo [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)může vést k nejasnostem. Další informace najdete [v tématu Inicializovat nebo změnit konfiguraci diagnostiky Azure.](https://msdn.microsoft.com/library/azure/hh411537.aspx)

Počínaje WAD 1.3 (součástí sady Azure SDK 2.5) už není možné ke konfiguraci diagnostiky použít kód. V důsledku toho můžete poskytnout pouze konfiguraci při použití nebo aktualizaci rozšíření diagnostiky.

### <a name="solution"></a>Řešení
Pomocí návrháře konfigurace diagnostiky přesuňte nastavení diagnostiky do konfiguračního souboru diagnostiky (diagnostics.wadcfg nebo diagnostics.wadcfgx pro sdchartu 2.5 a novější). Doporučujeme také nainstalovat [azure sdcharti 2.5](https://social.msdn.microsoft.com/Forums/en-US/home) a používat nejnovější diagnostické funkce.

1. V místní nabídce role, kterou chcete konfigurovat, zvolte Vlastnosti a pak zvolte kartu Konfigurace.
2. V části **Diagnostika** zkontrolujte, zda je zaškrtnuté políčko **Povolit diagnostiku.**
3. Zvolte tlačítko **Konfigurovat.**

   ![Přístup k možnosti Povolit diagnostiku](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Další informace [najdete v tématu Konfigurace diagnostiky pro cloudové služby Azure a virtuální počítače.](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Vyhněte se deklarování objektů DbContext jako statických
### <a name="id"></a>ID
AP6000

### <a name="description"></a>Popis
Chcete-li uložit paměť, vyhněte se deklarování DBContext objekty jako statické.

O své nápady a zpětnou vazbu se podělte na [webu Azure Code Analysis .](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Důvod
DBContext objekty obsahovat výsledky dotazu z každého volání. Statické DBContext objekty nejsou uvolněny, dokud je uvolněna doména aplikace. Proto statické DBContext objekt umůže spotřebovat velké množství paměti.

### <a name="solution"></a>Řešení
Deklarovat DBContext jako pole místní proměnné nebo nestatické instance, použijte jej pro úlohu a nechte ji po použití zlikvidovat.

Následující příklad MVC controller třída ukazuje, jak používat DBContext objektu.

```csharp
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>Další kroky
Další informace o optimalizaci a řešení potíží s aplikacemi Azure najdete [v tématu Poradce při potížích s webovou aplikací ve službě Azure App Service pomocí Visual Studia](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
