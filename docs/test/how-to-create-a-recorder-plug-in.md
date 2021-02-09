---
title: Vytvoření zapisovače Plug-In pro testy výkonnosti webu
description: Zjistěte, jak vám WebTestRecorderPlugin umožňuje upravit zaznamenaný test výkonnosti webu po zvolení možnosti zastavit na panelu nástrojů zapisovače testu výkonnosti webu.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: da17af68f7aebe52ad208bf2b83d3221a0640be6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877977"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Postupy: Vytvoření modulu plug-in pro záznam

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>Umožňuje upravit zaznamenaný test výkonnosti webu. Tato změna probíhá po výběru možnosti **zastavit** na panelu nástrojů **zapisovače testu výkonu webu** , ale před uložením a předložením v Editor testu výkonnosti webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Modul plug-in zapisovače umožňuje provádět vlastní korelaci na dynamických parametrech. Díky integrované funkci korelace detekuje testy výkonnosti webu při dokončení nahrávání dynamických parametrů, nebo když použijete **možnost Povýšit dynamické parametry na parametry webového testu** na panelu nástrojů **Editor testu výkonnosti webu** . Integrovaná funkce detekce ale vždy nenajde všechny dynamické parametry. Například nenalezne ID relace, které obvykle získá hodnotu změněno mezi 5 až 30 minutami. Proto je nutné ručně provést proces korelace.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>Umožňuje psát kód pro vlastní modul plug-in. Tento modul plug-in může provést korelaci nebo upravit test výkonnosti webu mnoha způsoby před jeho uložením a předložením v Editor testu výkonnosti webu. Proto pokud určíte, že konkrétní Dynamická proměnná musí být korelace pro velké množství záznamů, můžete proces automatizovat.

Některé další způsoby, jak lze použít modul plug-in zapisovače, je pro přidání pravidel pro extrakci a ověřování, přidání parametrů kontextu nebo převod komentářů na transakce v testu výkonnosti webu.

Následující postupy popisují, jak vytvořit kód základní pro modul plug-in zapisovače, nasadit modul plug-in a spustit modul plug-in. Vzorový kód za postupy ukazuje, jak pomocí jazyka Visual C# vytvořit vlastní modul plug-in zapisovače korelace dynamického parametru.

## <a name="create-a-recorder-plug-in"></a>Vytvoření modulu plug-in rekordéru

### <a name="to-create-a-recorder-plug-in"></a>Vytvoření modulu plug-in zapisovače

1. Otevřete řešení, které obsahuje projekt webového výkonu a zátěžového testu s testem výkonnosti webu, pro který chcete vytvořit modul plug-in zapisovače.

2. Přidejte do řešení nový projekt **knihovny tříd** .

3. V **Průzkumník řešení** v nové složce projektu knihovny tříd klikněte pravým tlačítkem myši na složku **odkazy** a vyberte možnost **Přidat odkaz**.

    > [!TIP]
    > Příkladem nové složky projektu knihovny tříd je **RecorderPlugins**.

     Zobrazí se dialogové okno **Přidat odkaz** .

4. Vyberte kartu **.NET** .

5. Posuňte se dolů a vyberte **Microsoft. VisualStudio. QualityTools. WebTestFramework** a pak zvolte **OK**.

     Do složky **odkazy** v **Průzkumník řešení** se přidá **Microsoft. VisualStudio. QualityTools. WebTestFramework** .

6. Napište kód pro modul plug-in zapisovače. Nejprve vytvořte novou veřejnou třídu, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> .

7. Přepsat <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> metodu.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Argumenty události vám poskytnou dva objekty, se kterými bude pracovat: zaznamenaný výsledek a zaznamenaný test výkonnosti webu. To vám umožní iterovat výsledky hledání určitých hodnot a pak přejít na stejný požadavek v testu výkonnosti webu, aby se provedly úpravy. Test výkonnosti webu lze také změnit pouze v případě, že jste chtěli přidat kontextový parametr nebo parametrizovat části adresy URL.

    > [!NOTE]
    > Pokud upravíte test výkonnosti webu, budete také muset nastavit <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> vlastnost na hodnotu true: `e.RecordedWebTestModified = true;`

8. Přidejte další kód podle toho, co chcete, aby se modul plug-in zapisovače spouštěl po výskytu záznamu webu. Můžete například přidat kód pro zpracování vlastní korelace, jak je znázorněno v následující ukázce. Můžete také vytvořit modul plug-in pro záznam věcí, jako je převod komentářů na transakce, nebo přidání ověřovacích pravidel do testu výkonnosti webu.

9. V nabídce **sestavení** klikněte na příkaz **sestavit \<class library project name>**.

V dalším kroku nasaďte modul plug-in zapisovače, aby se mohl zaregistrovat v aplikaci Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Nasazení modulu plug-in zapisovače

Po zkompilování modulu plug-in zapisovače umístěte výslednou knihovnu DLL do jednoho ze dvou umístění:

- *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ [verze] \\ [edice] \Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [verze] \WebTestPlugins*

> [!WARNING]
> Po zkopírování modulu plug-in zapisovače do jednoho ze dvou umístění je nutné restartovat sadu Visual Studio, aby byl modul plug-in zapisovače zaregistrován.

### <a name="execute-the-recorder-plug-in"></a>Spuštění modulu plug-in pro záznam

1. Vytvořte nový test výkonnosti webu.

     Zobrazí se dialogové okno **Povolit WebTestRecordPlugins** .

2. Zaškrtněte políčko pro modul plug-in zapisovače a zvolte **OK**.

     Po dokončení záznamu testu výkonnosti webu se spustí nový modul plug-in zapisovače.

    > [!WARNING]
    > Při spuštění testu výkonnosti webu nebo zátěžového testu, který používá modul plug-in, se může zobrazit chybová zpráva podobná následující:
    >
    > **Požadavek se nezdařil: výjimka v \<plug-in> události: nelze načíst soubor nebo sestavení \<"Plug-in name".dll file> , verze = \<n.n.n.n> , jazyková verze = neutrální, PublicKeyToken = null nebo jedna z jejích závislostí. Systém nemůže najít zadaný soubor.**
    >
    > To je způsobeno tím, že provedete změny kódu v některém z modulů plug-in a vytvoříte novou verzi knihovny DLL **(verze = 0.0.0.0)**, ale modul plug-in stále odkazuje na původní verzi modulu plug-in. Chcete-li tento problém vyřešit, postupujte podle následujících kroků:
    >
    > 1. V projektu webového výkonu a zátěžového testu se zobrazí upozornění v odkazech. Odeberte a znovu přidejte odkaz na knihovnu DLL modulu plug-in.
    > 2. Odeberte modul plug-in z testu nebo příslušné umístění a pak ho přidejte zpátky.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak vytvořit přizpůsobený modul plug-in zapisovače testu webového výkonu k provedení vlastní korelace dynamického parametru.

> [!NOTE]
> Úplný seznam vzorového kódu je umístěn v dolní části tohoto tématu.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Iterovat přes výsledek a najít první stránku s ReportSession

Tato část ukázky kódu projde každým zaznamenaným objektem a vyhledá tělo odpovědi pro ReportSession.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

### <a name="add-an-extraction-rule"></a>Přidat pravidlo pro extrakci

Teď, když se našla odpověď, je nutné přidat pravidlo extrakce. Tato část ukázky kódu vytvoří pravidlo pro extrakci pomocí <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> třídy a pak vyhledá správný požadavek v testu výkonnosti webu, aby přidal pravidlo extrakce do. Každý objekt výsledku má přidanou novou vlastnost nazvanou DeclarativeWebTestItemId, která je to, co se používá v kódu k získání správné žádosti z testu výkonnosti webu.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

### <a name="replace-query-string-parameters"></a>Nahradit parametry řetězce dotazu

Nyní kód vyhledá všechny parametry řetězce dotazu, které mají ReportSession jako název, a změní hodnotu na {{SessionId}}, jak je znázorněno v této části Ukázky kódu:

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Generování a spuštění programového testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
