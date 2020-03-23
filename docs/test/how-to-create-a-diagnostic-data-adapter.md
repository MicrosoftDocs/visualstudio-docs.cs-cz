---
title: 'Postupy: Vytvoření adaptéru diagnostických dat'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f196c3850c9413a7c68fd1fe67af50273915f249
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589172"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Postup: Vytvoření adaptéru diagnostických dat

Chcete-li vytvořit *adaptér diagnostických dat*, vytvořte knihovnu tříd pomocí sady Visual Studio a potom přidejte do knihovny tříd adaptéry diagnostická data, která poskytuje Visual Studio Enterprise. Odeslat všechny informace, které chcete jako <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> datový proud nebo soubor poskytované rozhraní, při zpracování události, které jsou vyvolány během spuštění testu. Datové proudy nebo soubory <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> odeslané do jsou uloženy jako přílohy k výsledkům testu po dokončení testu. Pokud vytvoříte chybu z těchto výsledků [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)]testu nebo při použití , soubory jsou také propojeny s chybou.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete vytvořit adaptér diagnostických dat, který ovlivňuje počítač, ve kterém jsou spuštěny testy, nebo počítač, který je součástí prostředí, které používáte ke spuštění testovací aplikace. Například shromažďování souborů v testovacím počítači, kde jsou spuštěny testy nebo shromažďování souborů v počítači sloužícím v roli webového serveru pro vaši aplikaci.

Adaptér diagnostických dat můžete poskytnout popisný název, který se zobrazí při vytváření nastavení testu pomocí Správce testů společnosti Microsoft nebo sady Visual Studio. Nastavení testu umožňuje definovat, která role počítače bude při spuštění testů spouštět konkrétní adaptéry diagnostických dat ve vašem prostředí. Adaptéry diagnostických dat můžete také nakonfigurovat při vytváření nastavení testu. Můžete například vytvořit adaptér diagnostických dat, který shromažďuje vlastní protokoly z webového serveru. Při vytváření nastavení testu můžete vybrat spuštění tohoto adaptéru diagnostických dat v počítači nebo počítačích, které provádějí tuto roli webového serveru, a můžete upravit konfiguraci nastavení testu tak, aby shromažďovala pouze poslední tři protokoly, které byly vytvořeny. Další informace o nastavení testu naleznete v [tématu Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

Události jsou vyvolány při spuštění testů tak, aby adaptér diagnostických dat můžete provádět úlohy v tomto okamžiku v testu.

> [!IMPORTANT]
> Tyto události mohou být vyvolány v různých vláknech, zejména pokud máte testy spuštěné na více počítačích. Proto je nutné znát možné problémy s podprocesem a neúmyslně poškodit interní data vlastního adaptéru. Ujistěte se, že adaptér diagnostických dat je bezpečný pro přístup z více vláken.

Následuje částečný seznam klíčových událostí, které můžete použít při vytváření adaptéru diagnostických dat. Úplný seznam událostí adaptéru diagnostických dat <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> naleznete v abstraktní třídě.

|Událost|Popis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Zahájení testovacího běhu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Konec zkušebního běhu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Začátek každého testu v testovacím běhu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Konec každého testu v testovacím běhu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Začátek každého kroku testu v testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Konec každého kroku testu v testu|

> [!NOTE]
> Po dokončení ručního testu nejsou do adaptéru diagnostických dat odeslány žádné další události shromažďování dat. Při opětovném spuštění testu bude mít nový identifikátor testovacího případu. Pokud uživatel resetuje test během testu <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> (který vyvolává událost) nebo změní výsledek kroku testu, není do adaptéru diagnostických dat odeslána žádná událost shromažďování dat, ale identifikátor testovacího případu zůstane stejný. Chcete-li zjistit, zda byl testovací případ resetován, je nutné sledovat identifikátor testovacího případu v adaptéru diagnostických dat.

Pomocí následujícího postupu vytvořte adaptér diagnostických dat, který shromažďuje datový soubor založený na informacích, které nakonfigurujete při vytváření nastavení testu.

Úplný příklad projektu adaptéru diagnostických dat, včetně vlastního editoru konfigurace, naleznete v [tématu Ukázkový projekt pro vytvoření adaptéru diagnostických dat](../test/quickstart-create-a-load-test-project.md).

## <a name="create-and-install-a-diagnostic-data-adapter"></a>Vytvoření a instalace adaptéru diagnostických dat

1. Vytvořte nový projekt **knihovny tříd.**

2. Přidejte sestavení **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

   1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **reference** a zvolte příkaz **Přidat odkaz.**

   2. Zvolte **soubor .NET** a vyhledejte **soubor Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

   3. Vyberte **OK**.

3. Přidejte sestavení **Microsoft.VisualStudio.QualityTools.Common**.

   1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **reference** a vyberte příkaz **Přidat odkaz.**

   2. Zvolte **/.NET**, vyhledejte **soubor Microsoft.VisualStudio.QualityTools.Common.dll**.

   3. Vyberte **OK**.

4. Do souboru třídy přidejte následující `using` direktivy:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Přidejte <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> do třídy adaptéru diagnostických dat, abyste jej identifikovali jako adaptér diagnostických dat a **nahradili společnost**, **produkt**a **verzi** příslušnými informacemi pro adaptér diagnostických dat:

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Přidejte <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> atribut do třídy a nahraďte parametry příslušnými informacemi pro adaptér diagnostických dat:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Tento popisný název se zobrazí v aktivitě nastavení testu.

   > [!NOTE]
   > Můžete také přidat <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> zadat `Type` vlastní konfigurační editor pro tento datový adaptér a volitelně určit soubor nápovědy, který se má použít pro editor.
   >
   > Můžete také použít <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> určit, že by měla být vždy povolena.

7. Třída adaptéru diagnostických dat <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> musí dědit z třídy následujícím způsobem:

   ```csharp
   public class MyDiagnosticDataAdapter : DataCollector
   ```

8. Přidejte místní proměnné takto:

   ```csharp
   private DataCollectionEvents dataEvents;
   private DataCollectionLogger dataLogger;
   private DataCollectionSink dataSink;
   private XmlElement configurationSettings;
   ```

9. Přidejte <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> metodu a **Dispose** metoda. V `Initialize` metodě inicializujete jímku dat, všechna konfigurační data z nastavení testu a zaregistrujete obslužné rutiny událostí, které chcete použít následujícím způsobem:

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

10. Ke shromažďování souboru protokolu generovaného během testu použijte následující kód obslužné rutiny události a soukromou metodu:

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

     Tyto soubory jsou připojeny k výsledkům testu. Pokud vytvoříte chybu z těchto výsledků [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)]testu nebo při použití , soubory jsou také připojeny k chybě.

     Pokud chcete ke shromažďování dat v testovacím nastavení použít vlastní editor, přečtěte si informace o [tom, jak vytvořit vlastní editor dat pro adaptér diagnostických dat](../test/quickstart-create-a-load-test-project.md).

11. Chcete-li shromáždit soubor protokolu po dokončení testu na základě toho, co uživatel nakonfiguroval v nastavení testu, musíte vytvořit soubor *App.config* a přidat jej do řešení. Tento soubor má následující formát a musí obsahovat identifikátor URI pro adaptér diagnostických dat k jeho identifikaci. Nahraďte reálné hodnoty "Společnost/ProductName/Version".

    > [!NOTE]
    > Pokud nepotřebujete konfigurovat žádné informace pro adaptér diagnostických dat, není nutné vytvářet konfigurační soubor.

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
    > Výchozí konfigurační prvek může obsahovat všechna data, která požadujete. Pokud uživatel nenakonfiguruje adaptér diagnostických dat v nastavení testu, budou výchozí data předána adaptéru diagnostických dat při jeho spuštění. Vzhledem k tomu, `<DefaultConfigurations>` že xml, který přidáte do oddílu, pravděpodobně nebude součástí deklarovaného schématu, můžete ignorovat všechny chyby XML, které generuje.
    >
    > Další příklady konfiguračních souborů jsou v následující cestě založené na instalačním adresáři: *Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*.

     Další informace o tom, jak nakonfigurovat nastavení testu pro použití prostředí při spuštění testů, naleznete [v tématu Shromažďování diagnostických dat v ručních testech (Plány testů Azure).](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)

     Další informace o instalaci konfiguračního souboru naleznete v [tématu Postup: Instalace vlastního adaptéru diagnostických dat](../test/quickstart-create-a-load-test-project.md)

12. Sestavte si řešení a vytvořte sestavení adaptéru diagnostických dat.

13. Informace o instalaci vlastního editoru naleznete v [tématu Postup: Instalace vlastního adaptéru diagnostických dat](../test/quickstart-create-a-load-test-project.md).

14. Další informace o tom, jak nakonfigurovat nastavení testu pro použití prostředí při spuštění testů, naleznete [v tématu Shromažďování diagnostických dat v ručních testech (Plány testů Azure).](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)

15. Chcete-li vybrat adaptér diagnostických dat, musíte nejprve vybrat existující nastavení testu nebo vytvořit nové z Microsoft Test Manager nebo Visual Studio. Adaptér se zobrazí na kartě **Data a diagnostika** nastavení testu s popisným názvem, který jste přiřadili třídě.

16. Nastavte tato nastavení testu tak, aby byla aktivní. Další informace o nastavení testu naleznete v [tématu Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

17. Spusťte testy pomocí nastavení testu s vybraným adaptérem diagnostických dat.

    Zadaný datový soubor je připojen k výsledkům testu.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Shromažďování diagnostických dat v ručních testech (plány testů Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Shromažďování diagnostických dat během testování (plány testů Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Postup: Vytvoření vlastního editoru dat pro adaptér diagnostických dat](../test/quickstart-create-a-load-test-project.md)
