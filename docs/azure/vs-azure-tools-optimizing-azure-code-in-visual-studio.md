---
title: Optimalizace kódu Azure
description: Přečtěte si, jak nástroje pro optimalizaci kódu Azure v aplikaci Visual Studio pomůžou zajistit robustnější a lepší výkon kódu.
author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: b7a20b4ae57ee5cf1127441bc43dea021c170188
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844031"
---
# <a name="optimizing-your-azure-code"></a>Optimalizace kódu Azure
Při programování aplikací, které používají Microsoft Azure, je třeba dodržovat některé postupy kódování, které vám pomohou zabránit problémům s škálovatelností aplikace, chováním a výkonem v cloudovém prostředí. Microsoft poskytuje nástroj pro analýzu kódu Azure, který rozpozná a identifikuje několik těchto běžně zjištěných problémů a pomůže vám je vyřešit. Nástroj si můžete stáhnout v aplikaci Visual Studio prostřednictvím NuGet.

## <a name="azure-code-analysis-rules"></a>Pravidla analýzy kódu Azure
Nástroj Analýza kódu Azure používá následující pravidla k automatickému označení kódu Azure při hledání známých problémů s dopadem na výkon. Zjištěné problémy se zobrazí jako upozornění nebo chyby kompilátoru. Opravy kódu nebo návrhy pro vyřešení upozornění nebo chyby jsou často k dispozici prostřednictvím ikony žárovky.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Nepoužívejte výchozí režim stavu relace (v procesu).
### <a name="id"></a>ID
AP0000

### <a name="description"></a>Description
Pokud pro cloudové aplikace použijete výchozí režim stavu relace (v rámci procesu), můžete ztratit stav relace.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Ve výchozím nastavení je režim stavu relace určený v souboru web.config v procesu. V případě, že v konfiguračním souboru není zadána žádná položka, nastaví se v režimu stavu relace v procesu. V režimu v procesu je uložen stav relace v paměti na webovém serveru. Když je instance restartována nebo se pro vyrovnávání zatížení nebo převzetí služeb při selhání používá nová instance, stav relace uložený v paměti na webovém serveru se neuloží. Tato situace zabrání škálovatelné aplikaci v cloudu.

Stav relace ASP.NET podporuje několik různých možností úložiště pro data stavu relace: InProc, StateServer, SQLServer, Custom a off. Pro hostování dat v externím úložišti stavu relace, jako je třeba [zprostředkovatel stavu relací Azure pro Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/), se doporučuje použít vlastní režim.

### <a name="solution"></a>Řešení
Jedním z doporučených řešení je uložení stavu relace ve spravované službě cache Service. Naučte se používat [zprostředkovatele stavu relace Azure pro Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) k uložení stavu relace. Stav relace můžete také uložit na jiných místech, abyste zajistili škálovatelnost aplikace v cloudu. Pokud se chcete dozvědět víc o alternativních řešeních, přečtěte si [režimy stavu relace](/previous-versions/ms178586(v=vs.140)).

## <a name="run-method-should-not-be-async"></a>Metoda Run by neměla být asynchronní.
### <a name="id"></a>ID
AP1000

### <a name="description"></a>Description
Vytvořte asynchronní metody (například [await](/dotnet/csharp/language-reference/operators/await)) mimo metodu [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) a potom zavolejte asynchronní metody z rutiny [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)). Deklarace metody [[Run ()](/previous-versions/azure/reference/ee772746(v=azure.100))](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) jako Async způsobí, že role pracovního procesu vstoupí do smyčky restart.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Volání asynchronních metod uvnitř metody [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) způsobí, že běhové prostředí cloudové služby recykluje roli pracovního procesu. Když se spustí role pracovního procesu, provede se všechny provádění programu uvnitř metody [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) . Ukončení metody Run způsobí restartování role pracovního procesu. Když modul runtime role pracovního procesu narazí na asynchronní metodu, odešle všechny operace za asynchronní metodou a pak se vrátí. Tím dojde k ukončení role pracovního procesu z metody Run a k restartování. V další iteraci spuštění role pracovního procesu znovu narazí na asynchronní metodu a restartuje se, což způsobí, že se role pracovního procesu znovu zacykluje.

### <a name="solution"></a>Řešení
Všechny asynchronní operace umístěte mimo metodu [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) . Pak zavolejte refaktored Async v rámci metody Run, jako je například RunAsync (). čekejte. Tento problém můžete vyřešit pomocí nástroje Azure Code Analysis.

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

## <a name="use-service-bus-shared-access-signature-authentication"></a>Použít ověřování pomocí Service Bus sdíleného přístupového podpisu
### <a name="id"></a>ID
AP2000

### <a name="description"></a>Description
Pro ověřování použijte sdílený přístupový podpis (SAS). Access Control Service (ACS) se pro ověřování Service Bus nepoužívá.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Pro zvýšení zabezpečení Azure Active Directory nahrazuje ověřování ACS pomocí ověřování SAS. Další informace o plánu přechodu najdete v tématu [Azure Active Directory budoucnosti služby ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) .

### <a name="solution"></a>Řešení
Ve svých aplikacích použijte ověřování pomocí SAS. Následující příklad ukazuje, jak použít existující token SAS pro přístup k oboru názvů nebo entitě služby Service Bus.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Další informace najdete v následujících tématech.

* Přehled najdete v tématu [ověřování pomocí sdíleného přístupového podpisu s Service Bus](/azure/service-bus-messaging/service-bus-sas) .
* [Jak používat ověřování pomocí sdíleného přístupového podpisu s Service Bus](/azure/service-bus-messaging/service-bus-sas)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Zvažte použití metody-Message, abyste se vyhnuli přijetí smyčky.
### <a name="id"></a>ID
AP2002

### <a name="description"></a>Description
Aby nedocházelo k tomu **, že volání metody "** Receive", je lepším řešením pro příjem zpráv než volání metody **Receive** . Pokud však musíte použít metodu **Receive** a zadáte nevýchozí dobu čekání serveru, ujistěte se, že doba čekání serveru je delší než jedna minuta.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Při volání **metody**"klient spustí interní čerpadlo zpráv, které se neustále dotazuje na frontu nebo odběr. Toto čerpadlo zpráv obsahuje nekonečnou smyčku, která vydává volání pro příjem zpráv. Pokud vyprší časový limit volání, vydá nové volání. Interval časového limitu je určen hodnotou vlastnosti [OperationTimeout](/dotnet/api/microsoft.servicebus.messaging.messagingfactorysettings) [MessagingFactory](/dotnet/api/microsoft.servicebus.messaging.messagingfactory), která je používána.

Výhodou použití rutiny **informování** v porovnání s **příjmem** je, že uživatelé nemusejí provádět ruční dotazování na zprávy, zpracovávat výjimky, zpracovávat paralelní zpracování více zpráv a doplňovat zprávy.

Pokud zavoláte **Receive** bez použití výchozí hodnoty, ujistěte se, že hodnota *ServerWaitTime* je větší než jedna minuta. Nastavení *ServerWaitTime* na více než jednu minutu zabraňuje serveru v vypršení časového limitu před úplným přijetím zprávy.

### <a name="solution"></a>Řešení
Pro doporučené použití se podívejte na následující příklady kódu. Další podrobnosti najdete v tématu [Metoda QueueClient.-Message (Microsoft. ServiceBus. Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) a [QueueClient. Receive (Microsoft. ServiceBus. Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient).

Pokud chcete zlepšit výkon infrastruktury zasílání zpráv Azure, přečtěte si Úvod do modelu návrhu [asynchronního zasílání zpráv](/previous-versions/msp-n-p/dn589781(v=pandp.10)).

Následuje příklad použití zprávy- **Message** k přijetí zpráv.

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

Následuje příklad použití **příjmu** s výchozím časem čekání serveru.

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

Následuje příklad použití **příjmu** s nevýchozí dobou čekání serveru.

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

## <a name="consider-using-asynchronous-service-bus-methods"></a>Zvažte použití asynchronních Service Bus metod
### <a name="id"></a>ID
AP2003

### <a name="description"></a>Description
Pomocí asynchronních Service Bus metod můžete zlepšit výkon pomocí zprostředkovaných zpráv.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Použití asynchronních metod umožňuje souběžný program aplikace, protože provádění jednotlivých volání neblokuje hlavní vlákno. Při použití metod Service Bus zasílání zpráv se při provádění operace (odeslání, přijetí, odstranění atd.) bere v chodu čas. Tato doba zahrnuje zpracování operace službou Service Bus kromě latence žádosti a odpovědi. Chcete-li zvýšit počet operací v čase, operace musí být spuštěny souběžně. Další informace najdete v tématu [osvědčené postupy pro zlepšení výkonu pomocí Service Bus](/previous-versions/azure/hh528527(v=azure.100))zprostředkovaných zpráv.

### <a name="solution"></a>Řešení
Informace o použití doporučené asynchronní metody naleznete v tématu [Třída QueueClient (Microsoft. ServiceBus. Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) .

Pokud chcete zlepšit výkon infrastruktury zasílání zpráv Azure, přečtěte si Úvod do modelu návrhu [asynchronního zasílání zpráv](/previous-versions/msp-n-p/dn589781(v=pandp.10)).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Zvažte dělení Service Bus front a tématům.
### <a name="id"></a>ID
AP2004

### <a name="description"></a>Description
Rozdělení Service Bus front a témat na oddíly pro lepší výkon pomocí Service Bus zasílání zpráv.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Dělení Service Bus fronty a témata zvyšují propustnost a dostupnost služeb, protože celková propustnost dělené fronty nebo tématu již není omezena výkonem jediného zprostředkovatele zpráv nebo úložiště pro zasílání zpráv. Kromě toho dočasný výpadek úložiště pro zasílání zpráv nevyřadí dělenou frontu nebo téma jako nedostupné. Další informace najdete v tématu [dělení entit zasílání zpráv](/previous-versions/azure/dn520246(v=azure.100)).

### <a name="solution"></a>Řešení
Následující fragment kódu ukazuje, jak vytvořit oddíly entit zasílání zpráv.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Další informace najdete v tématu [dělené a neService Bus fronty a témata | Microsoft Azure blog](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) a podívejte se na ukázku [fronty rozdělené na oddíly Microsoft Azure Service Bus](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) .

## <a name="do-not-set-sharedaccessstarttime"></a>Nenastavit SharedAccessStartTime
### <a name="id"></a>ID
AP3001

### <a name="description"></a>Description
Nepoužívejte SharedAccessStartTimeset k aktuálnímu času pro okamžité spuštění zásad sdíleného přístupu. Tuto vlastnost musíte nastavit jenom v případě, že chcete zásady sdíleného přístupu spustit později.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Synchronizace hodin způsobí mírné rozdíly mezi datovými centry. Například byste logicky poznamenali, že nastavení času spuštění zásad SAS úložiště jako aktuální čas pomocí hodnoty DateTime. Now nebo podobná metoda způsobí, že se zásada SAS projeví okamžitě. Mírné rozdíly mezi datovými centry ale můžou způsobit problémy, protože některá časová období můžou být trochu pozdější než čas spuštění, a to i s ostatními před ním. V důsledku toho mohou zásady SAS vypršet rychle (nebo dokonce okamžitě), pokud je doba života zásad nastavena příliš krátká.

Další informace o použití sdíleného přístupového podpisu v Azure Storage najdete v tématu [Úvod do tabulky SAS (sdílený přístupový podpis), zařazení do fronty a aktualizace do objektu BLOB SAS-Microsoft Azure Storage týmu domů-MSDN websites](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Řešení
Odeberte příkaz, který nastaví počáteční čas zásad sdíleného přístupu. Nástroj Analýza kódu Azure poskytuje opravu tohoto problému. Další informace o správě zabezpečení najdete ve [vzorovém vzoru osobního](/previous-versions/msp-n-p/dn568102(v=pandp.10))vzoru.

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

### <a name="description"></a>Description
Mezi datovými centry v datových centrech v různých umístěních může být až pět minut, protože podmínka se označuje jako "hodinový posun". Pokud chcete zabránit vypršení platnosti tokenu zásad SAS před tím, než bylo plánováno, nastavte čas vypršení platnosti na více než pět minut.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Datová centra v různých umístěních po celém světě se synchronizují pomocí hodinového signálu. Vzhledem k tomu, že časová signalizace cestuje k různým umístěním, může existovat časová odchylka mezi datovými centry v různých geografických umístěních, i když je vše natrvalo synchronizované. Tento časový rozdíl může mít vliv na počáteční čas a interval vypršení platnosti zásad sdíleného přístupu. Proto pokud chcete zajistit, aby se zásady sdíleného přístupu projevily okamžitě, nezadávejte čas spuštění. Kromě toho se ujistěte, že doba vypršení platnosti je delší než 5 minut, aby nedocházelo k počátečnímu vypršení časového limitu

Další informace o použití sdíleného přístupového podpisu ve službě Azure Storage najdete v tématu [Úvod do tabulky SAS (sdílený přístupový podpis), zařazení do fronty a aktualizace do objektu BLOB SAS-Microsoft Azure Storage blogové Blogy domů-MSDN websites](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Řešení
Další informace o správě zabezpečení najdete v článku [vzor návrhu osobního Key Pattern](/previous-versions/msp-n-p/dn568102(v=pandp.10)).

Následuje příklad, který neurčuje čas spuštění zásady sdíleného přístupu.

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

Tady je příklad zadání času spuštění zásady sdíleného přístupu s dobou trvání platnosti zásady delší než pět minut.

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

Další informace najdete v tématu [Konfigurace anonymního veřejného přístupu pro čtení pro kontejnery a objekty blob](/azure/storage/blobs/anonymous-read-access-configure?tabs=portal).

## <a name="use-cloudconfigurationmanager"></a>Použití CloudConfigurationManager
### <a name="id"></a>ID
AP4000

### <a name="description"></a>Description
Použití třídy [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) pro projekty, jako je například web Azure a Azure Mobile Services, nezavádí běhové problémy. Jako osvědčený postup je ale vhodné použít cloudové[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) jako jednotný způsob správy konfigurací pro všechny cloudové aplikace Azure.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
CloudConfigurationManager přečte konfigurační soubor, který je vhodný pro prostředí aplikace.

[CloudConfigurationManager](/previous-versions/azure/)

### <a name="solution"></a>Řešení
Refaktorujte kód pro použití [třídy CloudConfigurationManager](/previous-versions/azure/reference/mt634650(v=azure.100)). Oprava kódu pro tento problém je poskytována nástrojem analýza kódu Azure.

Následující fragment kódu ukazuje opravu kódu pro tento problém. Nahrazení

`var settings = ConfigurationManager.AppSettings["mySettings"];`

with

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Tady je příklad, jak uložit nastavení konfigurace do souboru App.config nebo Web.config. Přidejte nastavení do oddílu appSettings konfiguračního souboru. Následuje Web.config soubor pro předchozí příklad kódu.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Nepoužívejte pevně zakódované připojovací řetězce
### <a name="id"></a>ID
AP4001

### <a name="description"></a>Description
Pokud používáte pevně zakódované připojovací řetězce a potřebujete je aktualizovat později, budete muset provést změny zdrojového kódu a aplikaci znovu zkompilovat. Pokud však vaše připojovací řetězce ukládáte do konfiguračního souboru, můžete je později změnit, stačí aktualizovat konfigurační soubor.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Pevně zakódování připojovacích řetězců je špatný postup, protože zavádí problémy, když je potřeba rychle změnit připojovací řetězce. Kromě toho, pokud je nutné projekt vrátit se změnami do správy zdrojového kódu, pevně zakódované připojovací řetězce zavádějí slabá místa zabezpečení, protože řetězce lze zobrazit ve zdrojovém kódu.

### <a name="solution"></a>Řešení
Připojovací řetězce ukládejte do konfiguračních souborů nebo prostředí Azure.

* U samostatných aplikací použijte app.config k uložení nastavení připojovacího řetězce.
* Pro webové aplikace hostované službou IIS použijte web.config k ukládání připojovacích řetězců.
* Pro aplikace ASP.NET vNext použijte k ukládání připojovacích řetězců configuration.js.

Informace o použití konfiguračních souborů, jako jsou web.config nebo app.config, najdete v článku [pokyny pro konfiguraci webové konfigurace ASP.NET](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations). Informace o tom, jak proměnné prostředí Azure fungují, najdete v tématu [weby Azure: jak fungují řetězce aplikace a připojovací řetězce](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Informace o ukládání připojovacího řetězce ve správě zdrojového kódu naleznete v tématu [zamezení vkládání citlivých informací, jako jsou připojovací řetězce v souborech, které jsou uloženy v úložišti zdrojového kódu](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Použít konfigurační soubor diagnostiky
### <a name="id"></a>ID
AP5000

### <a name="description"></a>Description
Namísto konfigurace nastavení diagnostiky ve vašem kódu, jako je například pomocí programovacího rozhraní API Microsoft. WindowsAzure. Diagnostics, byste měli v souboru Diagnostics. wadcfg nakonfigurovat nastavení diagnostiky. (Nebo, Diagnostics. wadcfgx, pokud používáte sadu Azure SDK 2,5). Tímto způsobem můžete změnit nastavení diagnostiky, aniž by bylo nutné znovu kompilovat kód.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Před sadou Azure SDK 2,5 (využívající diagnostiku Azure Diagnostics 1,3) Azure Diagnostics (WAD) můžete nakonfigurovat pomocí několika různých metod: Přidání je do objektu BLOB konfigurace v úložišti, a to pomocí imperativního kódu, deklarativní konfigurace nebo výchozí konfigurace. Upřednostňovaným způsobem konfigurace diagnostiky je však použít konfigurační soubor XML (Diagnostics. wadcfg nebo Diagnostics. wadcfgx pro sadu SDK 2,5 a novější) v projektu aplikace. V tomto přístupu soubor Diagnostics. wadcfg kompletně definuje konfiguraci a dá se aktualizovat a znovu nasadit v. Kombinování použití konfiguračního souboru Diagnostics. wadcfg pomocí programových metod nastavení konfigurací pomocí tříd [DiagnosticMonitor](/previous-versions/azure/reference/ee758597(v=azure.100))nebo [RoleInstanceDiagnosticManager](/previous-versions/azure/reference/ee773157(v=azure.100))může vést k nejasnostem. Další informace najdete v tématu [inicializace nebo změna konfigurace Azure Diagnostics](/previous-versions/azure/hh411537(v=azure.100)) .

Od verze WAD 1,3 (zahrnuté v sadě Azure SDK 2,5) už není možné ke konfiguraci diagnostiky použít kód. V důsledku toho můžete tuto konfiguraci zadat jenom při použití nebo aktualizaci diagnostického rozšíření.

### <a name="solution"></a>Řešení
Pomocí návrháře konfigurace diagnostiky přesuňte nastavení diagnostiky do konfiguračního souboru diagnostiky (Diagnostics. wadcfg nebo Diagnostics. wadcfgx pro sadu SDK 2,5 a novější). Doporučuje se také nainstalovat [sadu Azure SDK 2,5](https://social.msdn.microsoft.com/Forums/en-US/home) a použít nejnovější diagnostické funkce.

1. V místní nabídce pro roli, kterou chcete konfigurovat, zvolte Vlastnosti a pak zvolte kartu konfigurace.
2. V části **Diagnostika** se ujistěte, že je zaškrtnuté políčko **Povolit diagnostiku** .
3. Klikněte na tlačítko **Konfigurovat** .

   ![Přístup k možnosti Povolit diagnostiku](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Další informace najdete v tématu [Konfigurace diagnostiky pro Azure Cloud Services a Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) .

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Vyhněte se deklarování objektů DbContext jako statických
### <a name="id"></a>ID
AP6000

### <a name="description"></a>Description
Chcete-li ušetřit paměť, vyhněte se deklaraci objektů DBContext jako statických.

Sdílejte své nápady a zpětnou vazbu na [základě názoru analýzy kódu Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Důvod
Objekty DBContext uchovávají výsledky dotazu z každého volání. Statické objekty DBContext nejsou uvolněny, dokud nebude doména aplikace uvolněna. Proto statický objekt DBContext může využívat velké množství paměti.

### <a name="solution"></a>Řešení
Deklarujte DBContext jako místní proměnnou nebo nestatickou instanci pole, použijte ji pro úkol a pak ji umožněte po použití odstranit.

Následující příklad třídy kontroleru MVC ukazuje, jak použít objekt DBContext.

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
Další informace o optimalizaci a řešení potíží s aplikacemi Azure najdete v tématu [řešení potíží s webovou aplikací v Azure App Service pomocí sady Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
