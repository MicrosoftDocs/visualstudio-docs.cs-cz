---
title: 'Postupy: Vytvoření adaptéru diagnostických dat'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1940cda15d1ac5515e25b1e1e997f13a32d6e53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653688"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Postupy: vytvoření adaptéru diagnostických dat

Pro vytvoření *adaptéru diagnostických dat*můžete vytvořit knihovnu tříd pomocí sady Visual Studio a poté přidat rozhraní API adaptéru diagnostických dat poskytovaná Visual Studio Enterprise do knihovny tříd. Odešlete všechny informace, které chcete použít jako datový proud nebo soubor do <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> poskytovaných rozhraním, při zpracování událostí, které jsou vyvolány během testovacího běhu. Datové proudy nebo soubory odeslané do <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> jsou uloženy jako přílohy výsledků testu po dokončení testu. Pokud vytvoříte chybu z těchto výsledků testu nebo používáte [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], jsou soubory také propojeny s chybou.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete vytvořit adaptér diagnostických dat, který má vliv na počítač, ve kterém jsou testy spuštěny, nebo na počítač, který je součástí prostředí, které používáte ke spuštění testované aplikace. Například shromažďování souborů na testovacím počítači, kde jsou testy spuštěny, nebo shromažďování souborů v počítači, který obsluhuje roli webového serveru pro vaši aplikaci.

Adaptéru diagnostických dat můžete dát popisný název, který se zobrazí při vytváření nastavení testu pomocí Microsoft Test Manager nebo pomocí sady Visual Studio. Nastavení testu umožňují definovat, která role počítače spustí konkrétní adaptéry diagnostických dat ve vašem prostředí při spuštění testů. Adaptéry diagnostických dat můžete také nakonfigurovat při vytváření nastavení testu. Můžete například vytvořit adaptér diagnostických dat, který shromáždí vlastní protokoly z webového serveru. Při vytváření nastavení testu můžete zvolit spuštění tohoto adaptéru diagnostických dat na počítači nebo počítačích, které provádějí tuto roli webového serveru, a můžete upravit konfiguraci pro nastavení testu tak, aby shromáždila pouze poslední tři protokoly, které byly vytvořeny. Další informace o nastaveních testu naleznete v tématu [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

Události jsou vyvolány při spuštění testů, aby adaptér diagnostických dat mohl provádět úlohy v tomto okamžiku v testu.

> [!IMPORTANT]
> Tyto události mohou být vyvolány v různých vláknech, zejména v případě, že máte testy spuštěné na více počítačích. Proto je třeba znát možné problémy s vlákny a neúmyslně poškodit interní data vlastního adaptéru. Ujistěte se, že váš adaptér diagnostických dat je bezpečný pro přístup z více vláken.

Následuje částečný seznam klíčových událostí, které můžete použít při vytváření adaptéru diagnostických dat. Úplný seznam událostí adaptéru diagnostických dat naleznete v tématu abstraktní <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> třídy.

|Událost|Popis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Začátek testovacího běhu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Konec testovacího běhu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Začátek každého testu v testovacím běhu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Konec každého testu v testovacím běhu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Začátek každého testovacího kroku v testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Konec každého testovacího kroku v testu|

> [!NOTE]
> Po dokončení manuálního testu nejsou do adaptéru diagnostických dat odesílány žádné další události shromažďování dat. Při opakovaném spuštění testu bude mít nový identifikátor testovacího případu. Pokud uživatel obnoví test v průběhu testu (což vyvolá událost <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset>) nebo změní výsledek testovacího kroku, není odeslána žádná událost shromažďování dat do adaptéru diagnostických dat, ale identifikátor testovacího případu zůstává stejný. Chcete-li určit, zda byl testovací případ resetován, je nutné sledovat identifikátor testovacího případu v adaptéru diagnostických dat.

Pomocí následujícího postupu můžete vytvořit adaptér diagnostických dat, který shromažďuje datový soubor založený na informacích, které nakonfigurujete při vytváření nastavení testu.

Úplný příklad projektu s diagnostickými daty, včetně vlastního editoru konfigurace, najdete v tématu [vzorový projekt pro vytvoření adaptéru diagnostických dat](../test/quickstart-create-a-load-test-project.md).

## <a name="create-and-install-a-diagnostic-data-adapter"></a>Vytvoření a instalace adaptéru diagnostických dat

1. Vytvořte nový projekt **knihovny tříd** .

2. Přidejte sestavení **Microsoft. VisualStudio. QualityTools. ExecutionCommon**.

   1. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy** a vyberte příkaz **Přidat odkaz** .

   2. Vyberte **.NET** a vyhledejte **Microsoft. VisualStudio. QualityTools. ExecutionCommon. dll**.

   3. Klikněte na **tlačítko OK**.

3. Přidejte sestavení **Microsoft. VisualStudio. QualityTools. Common**.

   1. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy** a vyberte příkaz **Přidat odkaz** .

   2. Vyberte **/.NET**, vyhledejte **Microsoft. VisualStudio. QualityTools. Common. dll**.

   3. Klikněte na **tlačítko OK**.

4. Do souboru třídy přidejte následující direktivy `using`:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Přidejte <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> do třídy pro adaptér diagnostických dat, abyste ho identifikovali jako adaptér diagnostických dat a nahradili **Společnost**, **produkt**a **verzi** odpovídajícími informacemi pro adaptér diagnostických dat:

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Přidejte atribut <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> do třídy a nahraďte parametry odpovídajícími informacemi pro adaptér diagnostických dat:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Tento popisný název se zobrazí v aktivitě nastavení testu.

   > [!NOTE]
   > Můžete také přidat <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> pro určení `Type` vlastního editoru konfigurace pro tento datový adaptér a volitelně zadat soubor s nápovědu pro použití v editoru.
   >
   > @No__t_0 můžete použít také k určení toho, že by měl být vždy povolen.

7. Třída adaptéru diagnostických dat musí dědit z třídy <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> následujícím způsobem:

   ```csharp
   public class MyDiagnosticDataAdapter : DataCollector
   ```

8. Přidejte místní proměnné následujícím způsobem:

   ```csharp
   private DataCollectionEvents dataEvents;
   private DataCollectionLogger dataLogger;
   private DataCollectionSink dataSink;
   private XmlElement configurationSettings;
   ```

9. Přidejte metodu <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> a metodu **Dispose** . V metodě `Initialize` inicializujete datovou jímku, všechna konfigurační data z nastavení testu a zaregistrujete obslužné rutiny událostí, které chcete použít, následujícím způsobem:

    ```csharp
    public override void Initialize(
        XmlElement configurationElement,
        DataCollectionEvents events,
        DataCollectionSink sink,
        DataCollectionLogger logger,
        DataCollectionEnvironmentContext environmentContext)
    {
           dataEvents = events;  // The test events
           dataLogger = logger;  // The error and warning log
           dataSink = sink;      // Saves collected data
           // Configuration from the test settings
           configurationSettings = configurationElement;

           // Register common events for the data collector
           // Not all of the events are used in this class
        dataEvents.SessionStart +=
            new EventHandler<SessionStartEventArgs>(OnSessionStart);
        dataEvents.SessionEnd +=
            new EventHandler<SessionEndEventArgs>(OnSessionEnd);
        dataEvents.TestCaseStart +=
            new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
        dataEvents.TestCaseEnd +=
            new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
    }

    public override void Dispose(bool disposing)
    {
        if (disposing)
        {
            // Unregister the registered events
            dataEvents.SessionStart -=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd -=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart -=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd -=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
        }
    }
    ```

10. Použijte následující kód obslužné rutiny události a soukromou metodu ke shromáždění souboru protokolu vygenerovaného během testu:

    ```csharp
    public void OnTestCaseEnd(sender, TestCaseEndEventArgs e)
    {
        // Get any files to be collected that are
        // configured in your test settings
        List<string> files = getFilesToCollect();

        // For each of the files, send the file to the data sink
        // which will attach it to the test results or to a bug
        foreach (string file in files)
        {
            dataSink.SendFileAsync(e.Context, file, false);
        }
    }

    // A private method that returns the file names
    private List<string> getFilesToCollect()
    {
        // Get a namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                configurationSettings.OwnerDocument.NameTable);
        nsmgr.AddNamespace("ns",
            "http://MyCompany/schemas/MyDataCollector/1.0");

        // Find all of the "File" elements under our configuration
        XmlNodeList files =
            configurationSettings.SelectNodes(
                "//ns:MyDataCollector/ns:File");

        // Build the list of files to collect from the
        // "FullPath" attributes of the "File" nodes.
        List<string> result = new List<string>();
        foreach (XmlNode fileNode in files)
        {
            XmlAttribute pathAttribute =
                fileNode.Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result.Add(pathAttribute.Value);
            }
        }

        return result;
    }
    ```

     Tyto soubory jsou připojeny k výsledkům testu. Pokud vytvoříte chybu z těchto výsledků testu nebo používáte [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], jsou soubory také připojeny k chybě.

     Pokud chcete použít vlastní editor ke shromáždění dat pro použití v nastavení testu, přečtěte si téma [Postup: Vytvoření vlastního editoru dat pro adaptér diagnostických dat](../test/quickstart-create-a-load-test-project.md).

11. Chcete-li shromáždit soubor protokolu po dokončení testu na základě toho, co uživatel nakonfiguroval v nastavení testu, je nutné vytvořit soubor *App. config* a přidat jej do řešení. Tento soubor má následující formát a musí obsahovat identifikátor URI pro adaptér diagnostických dat k jeho identifikaci. Nahraďte reálné hodnoty položky "společnost/NázevVýrobku/verze".

    > [!NOTE]
    > Pokud nepotřebujete konfigurovat žádné informace pro adaptér diagnostických dat, nemusíte vytvářet konfigurační soubor.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <section name="DataCollectorConfiguration" type="Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationSection, Microsoft.VisualStudio.QualityTools.ExecutionCommon, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a "/>
      </configSections>
      <DataCollectorConfiguration xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010">
        <DataCollector typeUri="datacollector://MyCompany/MyProduct/1.0">
          <DefaultConfiguration>
            <!-- Your default config settings -->
            <Binaries>
              <Binary FullPath="C:\Example\Example.dll"/>
              <Binary FullPath="\\Server2\Example2.dll"/>
            </Binaries>
            <Symbols>
              <Symbol FullPath="\\ExampleServer\ExampleSymbol.pdb"/>
            </Symbols>
          </DefaultConfiguration>
        </DataCollector>
      </DataCollectorConfiguration>
    </configuration>
    ```

    > [!NOTE]
    > Výchozí prvek konfigurace může obsahovat všechna data, která požadujete. Pokud uživatel nekonfiguruje adaptér diagnostických dat v nastaveních testu, pak výchozí data budou předána adaptéru diagnostických dat při jeho spuštění. Vzhledem k tomu, že kód XML, který přidáte do oddílu `<DefaultConfigurations>`, pravděpodobně není součástí deklarovaného schématu, můžete ignorovat všechny chyby XML, které generuje.
    >
    > Existují další příklady konfiguračních souborů v následující cestě na základě instalačního adresáře: *Program Files\Microsoft Visual Studio 10.0 \ Common7\IDE\PrivateAssemblies\DataCollectors*.

     Další informace o tom, jak nakonfigurovat nastavení testu tak, aby používalo prostředí při spuštění testů, najdete v tématu [shromažďování diagnostických dat v ručních testech (Azure test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

     Další informace o instalaci konfiguračního souboru najdete v tématu [Postup: Instalace vlastního adaptéru diagnostických dat.](../test/quickstart-create-a-load-test-project.md)

12. Sestavte řešení pro vytvoření sestavení adaptéru diagnostických dat.

13. Informace o instalaci vlastního editoru najdete v tématu [Postup: Instalace vlastního adaptéru diagnostických dat](../test/quickstart-create-a-load-test-project.md).

14. Další informace o tom, jak nakonfigurovat nastavení testu tak, aby používalo prostředí při spuštění testů, najdete v tématu [shromažďování diagnostických dat v ručních testech (Azure test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

15. Chcete-li vybrat adaptér diagnostických dat, musíte nejprve vybrat existující nastavení testu nebo vytvořit nový z Microsoft Test Manager nebo Visual Studio. Adaptér se zobrazí na kartě **data a diagnostika** v nastavení testu s popisným názvem, který jste přiřadili ke třídě.

16. Nastavte nastavení těchto testů na aktivní. Další informace o nastaveních testu naleznete v tématu [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

17. Spusťte testy pomocí nastavení testu s vybraným adaptérem diagnostických dat.

    Datový soubor, který jste zadali, je připojen k vašim výsledkům testu.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Shromažďovat diagnostická data v ručních testech (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Shromažďovat diagnostická data při testování (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Postupy: Vytvoření vlastního editoru dat pro adaptér diagnostických dat](../test/quickstart-create-a-load-test-project.md)
