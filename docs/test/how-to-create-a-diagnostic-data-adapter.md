---
title: 'Postupy: Vytvoření adaptéru diagnostických dat'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 051f5ad7783271c2b0eea26bc3af5c0980f2c1fc
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068299"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Postupy: vytvoření adaptéru diagnostických dat

Chcete-li vytvořit *adaptér diagnostických dat*, vytvořte knihovnu třídy pomocí sady Visual Studio a potom přidat do knihovny tříd poskytuje Visual Studio Enterprise API adaptéru diagnostických dat. Veškeré informace, které chcete, aby jako datový proud nebo soubor, který chcete odeslat <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> poskytovaného rámcem, při zpracování událostí, které jsou aktivovány v průběhu testovacího běhu. Datové proudy nebo soubory odeslané <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> jsou uloženy jako přílohy k výsledkům testu po dokončení testu. Pokud vytvoříte chybu z těchto výsledků testování nebo při použití [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], soubory se také s chybou propojen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete vytvořit adaptér diagnostických dat, který má vliv na počítači, kde probíhají testy, nebo počítač, který je součástí prostředí, který používáte ke spuštění aplikace v rámci testu. Například shromažďování souborů na testovacím počítači, ve kterém jsou testy spustit nebo shromažďování souborů na počítač, který je v roli webového serveru pro vaši aplikaci.

Adaptér diagnostických dat můžete dát popisný název, který se zobrazí při vytvoření nastavení testu pomocí nástroje Microsoft Test Manager nebo pomocí sady Visual Studio. Test nastavení umožňují definovat, které role počítače budou spouštět určité adaptéry diagnostických dat ve vašem prostředí při spuštění testů. Můžete také nakonfigurovat adaptéry diagnostických dat při vytvoření nastavení testu. Můžete například vytvořit adaptér diagnostických dat, který shromažďuje vlastní protokoly z webového serveru. Když vytvoříte nastavení testu, můžete vybrat spustit tento adaptér diagnostických dat na počítači nebo počítačích, které provádějí tuto roli webového serveru a můžete upravovat konfiguraci pro vaše nastavení testu k získání pouze posledních tří protokolů, které byly vytvořeny. Další informace o nastaveních testu naleznete v tématu [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

Události jsou vyvolány při spuštění testů tak, aby adaptér diagnostických dat můžete v tomto okamžiku provádět úlohy v testu.

> [!IMPORTANT]
> Tyto události mohou být vyvolány v různých vláknech, zvláště když máte testy spuštěné ve více počítačích. Proto musíte znát možné problémy s tvorbou vláken a nikoli neúmyslně poškodit vnitřní data vlastního adaptéru. Ujistěte se, že váš adaptér diagnostických dat je bezpečné pro vlákna.

Následuje částečný seznam klíčových událostí, které můžete použít při vytváření adaptéru diagnostických dat. Úplný seznam diagnostických dat adaptéru událostí naleznete v abstraktní <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> třídy.

|Událost|Popis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Začátek vašeho spuštění testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Konec vašeho spuštění testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Začátek každého testu v testovacím běhu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Konec každého testu v testovacím běhu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Začátek každého kroku testu v testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Konec každého kroku testu v testu|

> [!NOTE]
> Po dokončení manuálního testu adaptér diagnostických dat jsou odesílány žádné další události kolekce. Když se znovu spustí test, bude mít nový identifikátor testovacího případu. Pokud uživatel obnoví test při zkoušce (která vyvolává <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> událostí), nebo změny testovací krok výsledek, žádná událost kolekce dat je odeslána do adaptéru diagnostických dat, ale identifikátor testovacího případu zůstává stejný. K určení, zda byla obnovena testovacího případu, musíte sledovat identifikátor testovacího případu v adaptéru diagnostických dat.

Pomocí následujícího postupu vytvořte adaptér diagnostických dat, který shromažďuje datový soubor, který je založen na informacích, které konfigurujete při vytvoření nastavení testu.

Kompletní příklad diagnostických dat adaptéru projektu, včetně vlastního konfiguračního editoru, najdete v části [ukázkový projekt pro vytvoření adaptéru diagnostických dat](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

##  <a name="create-and-install-a-diagnostic-data-adapter"></a>Vytvoření a instalace adaptéru diagnostických dat

### <a name="to-create-and-install-a-diagnostic-data-adapter"></a>Vytvoření a instalace adaptéru diagnostických dat

1. Vytvořte novou knihovnu tříd.

   1.  Na **souboru** nabídce zvolte **nový**a pak na **nový projekt**.

   2.  Z **typy projektů**, vyberte jazyk, který chcete použít.

   3.  Z **instalované šablony sady Visual Studio**vyberte **knihovny tříd**.

   4.  Zadejte název pro adaptér diagnostických dat.

   5.  Zvolte **OK**.

2. Přidat sestavení **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

   1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** a zvolte **přidat odkaz** příkazu.

   2.  Zvolte **.NET** a vyhledejte **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

   3.  Zvolte **OK**.

3. Přidat sestavení **Microsoft.VisualStudio.QualityTools.Common**.

   1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** a vyberte **přidat odkaz** příkazu.

   2.  Zvolte **/.NET**, vyhledejte **Microsoft.VisualStudio.QualityTools.Common.dll**.

   3.  Zvolte **OK**.

4. Přidejte následující `using` příkazy do souboru třídy:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Přidat <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> do třídy pro adaptér diagnostických dat k jeho identifikaci jako adaptéru diagnostických dat, nahrazení **společnosti**, **produktu**, a **verze** s odpovídajícími informacemi pro adaptér diagnostických dat:

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Přidat <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> atribut třídy, nahraďte parametry s odpovídajícími informacemi pro adaptér diagnostických dat:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Tento popisný název se zobrazí v aktivitě nastavení testu.

   > [!NOTE]
   > Můžete také přidat <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> zadat `Type` z editoru vlastní konfigurace pro tento datový adaptér a volitelně zadat soubor nápovědy pro použití v editoru.
   >
   > Můžete také použít <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> k určení, že je vždy povolena.

7. Vaše třída adaptéru diagnostických dat musí dědit z <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> třídy následujícím způsobem:

   ```csharp
   public class MyDiagnosticDataAdapter : DataCollector
   ```

8. Přidejte lokální proměnné následujícím způsobem:

   ```csharp
   private DataCollectionEvents dataEvents;
   private DataCollectionLogger dataLogger;
   private DataCollectionSink dataSink;
   private XmlElement configurationSettings;
   ```

9. Přidat <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> metoda a **Dispose** metoda. V `Initialize` metody inicializujete jímky dat, všechna konfigurační data z nastavení testu a registrujete obslužné rutiny událostí, které chcete použít následujícím způsobem:

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

10. Použijte následující kód obslužné rutiny události a soukromou metodu k získání souboru protokolu generovaného během testu:

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

     Tyto soubory jsou připojeny k výsledkům testu. Pokud vytvoříte chybu z těchto výsledků testování nebo při použití [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], jsou soubory také připojeny k chybě.

     Pokud chcete použít vlastní editor pro shromažďování dat pro použití v nastaveních testu naleznete v části [postupy: vytvoření vlastního editoru dat pro adaptér diagnostických dat](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md).

11. Pokud chcete získat soubor protokolu po dokončení testu založené na to, co uživatel nakonfiguroval v nastavení testu, musíte vytvořit *App.config* a přidejte ji do vašeho řešení. Tento soubor má následující formát a musí obsahovat identifikátor URI pro adaptér diagnostických dat pro jeho rozpoznání. Nahraďte skutečné hodnoty "společnost/NázevProduktu/verze".

    > [!NOTE]
    > Pokud nepotřebujete konfigurovat žádné informace pro adaptér diagnostických dat, není potřeba vytvořit konfigurační soubor.

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
    > Prvek výchozí konfigurační může obsahovat libovolná data, která požadujete. Pokud uživatel nenakonfiguruje adaptér diagnostických dat v nastaveních testu, pak výchozí data budou předána adaptéru diagnostických dat, po spuštění. Protože XML, které přidáte do `<DefaultConfigurations>` oddíl není pravděpodobně součástí deklarovaného schématu, můžete ignorovat všechny chyby XML generuje.
    >
    > Existují jiné příklady konfiguračních souborů v následující cestě podle instalačního adresáře: *Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*.

     Další informace o tom, jak nakonfigurovat nastavení testu pro použití prostředí při spuštění testů, naleznete v tématu [shromažďování diagnostických dat v manuálních testů (testovací plány Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

     Další informace o instalaci konfiguračního souboru najdete v tématu [postupy: instalace vlastního adaptéru diagnostických dat](../test/how-to-install-a-custom-diagnostic-data-adapter.md)

12. Sestavte řešení k vytvoření sestavení adaptéru diagnostických dat.

13. Informace o instalaci vlastního editoru naleznete v tématu [postupy: instalace vlastního adaptéru diagnostických dat](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

14. Další informace o tom, jak nakonfigurovat nastavení testu pro použití prostředí při spuštění testů, naleznete v tématu [shromažďování diagnostických dat v manuálních testů (testovací plány Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

15. Pokud chcete vybrat adaptér diagnostických dat, musíte nejprve vybrat existující nastavení testu nebo vytvořit nový štítek z Microsoft Test Manager nebo Visual Studio. Adaptér se zobrazí na **dat a diagnostiky** karty ve vašem nastavení testu s popisným názvem, který jste přiřadili do třídy.

16. Nastavte toto jako aktivní nastavení testu. Další informace o nastaveních testu naleznete v tématu [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

17. Spusťte testy pomocí nastavení testu společně s výběrem adaptéru diagnostiky dat vybrali.

    K výsledkům testů je připojen datový soubor, který jste zadali.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Shromažďování diagnostických údajů pomocí nastavení testů](../test/collect-diagnostic-information-using-test-settings.md)
- [Shromažďování diagnostických dat v manuálních testů (Azure testovací plány)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Shromažďování diagnostických dat při testování (Azure testovací plány)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Postupy: vytvoření vlastního editoru dat pro adaptér diagnostických dat](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)