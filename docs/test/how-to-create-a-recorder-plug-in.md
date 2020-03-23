---
title: Vytvoření modulu plug-in rekordéru pro testy výkonu webu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e32faa4525edc79da3d759d67ad2b5676f38fc2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589141"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Postup: Vytvoření modulu plug-in rekordéru

Umožňuje <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> upravit test zaznamenaného výkonu webu. Ke změně dojde po výběru **možnosti Zastavit** na panelu nástrojů **Zapisovač výkonu na webu,** ale před uložením a zobrazením testu v editoru testů výkonu webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Modul plug-in rekordéru umožňuje provádět vlastní korelaci dynamických parametrů. Díky vestavěné funkcionality korelace testy výkonu webu detekují dynamické parametry ve webovém záznamu po dokončení nebo při použití **funkce Zvýšit dynamické parametry na parametry testu webu** na panelu nástrojů Editor u **webového testu výkonu.** Vestavěná funkce zjišťování však ne vždy najde všechny dynamické parametry. Například nenajde ID relace, která obvykle získá jeho hodnota změněna mezi 5 až 30 minut. Proto je nutné ručně provést proces korelace.

Umožňuje <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> psát kód pro vlastní plug-in. Tento modul plug-in může provádět korelace nebo upravit test výkonu webu mnoha způsoby před jeho uložením a prezentovány v editoru webových testů výkonu. Proto pokud zjistíte, že konkrétní dynamická proměnná musí být korelována pro mnoho nahrávek, můžete proces automatizovat.

Některé další způsoby, které lze použít modul plug-in rekordéru, jsou pro přidání pravidel extrakce a ověření, přidání parametrů kontextu nebo převod komentářů na transakce v testu výkonu webu.

Následující postupy popisují, jak vytvořit základní kód pro modul plug-in rekordéru, nasadit modul plug-in a spustit modul plug-in. Ukázkový kód následující postupy ukazuje, jak pomocí visual c# vytvořit vlastní modul plug-in relační parametr záznamník.

## <a name="create-a-recorder-plug-in"></a>Vytvoření modulu plug-in rekordéru

### <a name="to-create-a-recorder-plug-in"></a>Vytvoření modulu plug-in rekordéru

1. Otevřete řešení, které obsahuje webový výkon a zatížení testovací projekt s testem výkonu webu, pro který chcete vytvořit modul plug-in rekordéru.

2. Přidejte do řešení nový projekt **knihovny tříd.**

3. V **Průzkumníku řešení**klikněte v nové složce projektu **knihovny** tříd pravým tlačítkem myši na složku Reference a vyberte **přidat odkaz**.

    > [!TIP]
    > Příkladem nové složky projektu knihovny tříd je **RecorderPlugins**.

     Zobrazí se dialogové okno **Přidat odkaz.**

4. Vyberte kartu **.NET.**

5. Posuňte se dolů a vyberte **Microsoft.VisualStudio.QualityTools.WebTestFramework** a pak zvolte **OK**.

     **Rozhraní Microsoft.VisualStudio.QualityTools.WebTestFramework** je přidáno do složky **Reference v** **Průzkumníku řešení**.

6. Napište kód pro zásuvný modul rekordéru. Nejprve vytvořte novou veřejnou <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>třídu, která je odvozena od .

7. Přepsat metodu. <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Argumenty události vám dva objekty pracovat s: zaznamenaný výsledek a zaznamenané test výkonu webu. To vám umožní iterate prostřednictvím výsledku hledá určité hodnoty a pak přejít na stejný požadavek v testu výkonu webu provést změny. Můžete také upravit test výkonu webu, pokud chcete přidat parametr kontextu nebo parametrizovat části adresy URL.

    > [!NOTE]
    > Pokud změníte test výkonu webu, budete také <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> muset nastavit vlastnost na hodnotu true:`e.RecordedWebTestModified = true;`

8. Přidejte další kód podle toho, co chcete, aby se modul plug-in rekordéru provedl po nahrávání webu. Můžete například přidat kód pro zpracování vlastní korelace, jak je znázorněno v následující ukázce. Můžete také vytvořit modul plug-in rekordéru pro takové věci, jako je převod komentářů na transakce nebo přidání ověřovacích pravidel do testu výkonu webu.

9. V nabídce **Build** zvolte **Build \<class library název projektu>**.

Dále nasaďte modul plug-in rekordéru, aby se mohl zaregistrovat v sadě Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Nasazení modulu plug-in rekordéru

Po kompilaci modulu plug-in rekordéru umístěte výslednou dll na jedno ze dvou umístění:

- *%ProgramFiles(x86)%\Microsoft Visual\\Studio\\[verze] [edice]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [verze]\WebTestPlugins*

> [!WARNING]
> Po zkopírování modulu plug-in rekordéru do jednoho ze dvou umístění je nutné restartovat aplikaci Visual Studio, aby byl modul plug-in rekordéru zaregistrován.

### <a name="execute-the-recorder-plug-in"></a>Spusťte modul plug-in rekordéru

1. Vytvořte nový test výkonu webu.

     Zobrazí se dialogové okno **Povolit webtestrecordplugins.**

2. Zaškrtněte políčko pro zásuvný modul rekordéru a zvolte **OK**.

     Po dokončení webového testu výkonu bude proveden nový modul plug-in rekordéru.

    > [!WARNING]
    > Při spuštění testu výkonu webu nebo zátěžového testu, který používá váš modul plug-in, se může zobrazit chyba podobná následující:
    >
    > **Požadavek se \<nezdařil: Výjimka v akci> modulu plug-in: Nelze načíst soubor nebo sestavení '\<"Název modulu plug-in".dll soubor>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null nebo jednu z jeho závislostí. Systém nemůže najít zadaný soubor.**
    >
    > To je způsobeno, pokud provedete změny kódu některého z modulů plug-in a vytvoříte novou verzi dll **(Version = 0.0.0.0)**, ale modul plug-in stále odkazuje na původní verzi modulu plug-in. Chcete-li tento problém vyřešit, postupujte takto:
    >
    > 1. Ve vašem projektu výkonu webu a zátěžového testu se zobrazí upozornění v odkazech. Odeberte a znovu přidejte odkaz na datovou dll modulu plug-in.
    > 2. Odeberte modul plug-in z testu nebo příslušného umístění a přidejte jej zpět.

## <a name="example"></a>Příklad

Tato ukázka ukazuje, jak vytvořit vlastní webový test výkonu zapisovač e-dohánění modulu plug-in k provedení vlastní dynamické parametrkorelace.

> [!NOTE]
> Úplný seznam ukázkového kódu je umístěn v dolní části tohoto tématu.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Iterate prostřednictvím výsledku najít první stránku s ReportSession

Tato část ukázky kódu iteruje přes každý zaznamenaný objekt a prohledává tělo odpovědi pro ReportSession.

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

### <a name="add-an-extraction-rule"></a>Přidání pravidla extrakce

Nyní, když byla nalezena odpověď, je třeba přidat pravidlo extrakce. Tato část ukázky kódu vytvoří pravidlo <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> extrakce pomocí třídy a potom najde správný požadavek v testu výkonu webu přidat pravidlo extrakce. Každý výsledek objektu má novou vlastnost přidáns názvem DeclarativeWebTestItemId což je co se používá v kódu získat správný požadavek z testu výkonu webu.

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

Nyní kód vyhledá všechny parametry řetězce dotazu, které mají ReportSession jako název a změnit hodnotu {{SessionId}}, jak je znázorněno v této části ukázky kódu:

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
