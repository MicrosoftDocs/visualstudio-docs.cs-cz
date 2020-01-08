---
title: Zapisovačem vytvořit modul Plug-In pro testy výkonnosti webu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e32faa4525edc79da3d759d67ad2b5676f38fc2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589141"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Postupy: vytvoření modulu Plugin rekordéru

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> Umožňuje upravovat test výkonnosti webu zaznamenané. Změna nastane po zvolení **Zastavit** v **rekordéru testu výkonnosti webu** nástrojů, ale před test uložením a zobrazením v editoru testu výkonnosti webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Modul plug-in rekordéru umožňuje provádění vlastní korelace dynamických parametrů. S funkcí vestavěné korelace testy výkonnosti webu rozpoznávají dynamické parametry na webu nahrávání po dokončení nebo při použití **povýšit dynamické parametry na parametry webového testu** na **Web Editor testu výkonnosti** nástrojů. Nicméně integrovaná v detekce funkce nenajde vždy všechny dynamické parametry. Například nenajde ID relace, které obvykle svou hodnotu mění mezi 5 až 30 minut. Proto budete muset ručně provést proces korelace.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> Umožňuje napsat kód pro vlastní modul plug-in. Tento modul plug-in může provádět korelaci nebo změnu testu výkonnosti webu mnoha způsoby před uložením a zobrazením v editoru testu výkonnosti webu. Proto pokud zjistíte, že konkrétní Dynamická proměnná musí být korelována pro mnoho vašich nahrávek, můžete automatizovat proces.

Je několik způsobů, mohou používat modul plug-in rekordéru je pro přidávání extrakčních a ověřovacích pravidel, přidání parametrů kontextu nebo převod komentářů k transakci ve výkonnosti testu.

Následující postupy popisují, jak vytvořit základní kód pro rekordér modul plug-in, jak nasadit doplněk a spustit. Následující postupy ukázkový kód ukazuje, jak pomocí Visual C# vytvořit modul plug-in záznamníku korelace dynamického parametru vlastní.

## <a name="create-a-recorder-plug-in"></a>Vytvoření modulu plug-in rekordéru

### <a name="to-create-a-recorder-plug-in"></a>Můžete vytvořit modul plug-in rekordéru

1. Otevřete řešení, která obsahuje webový výkon a projekt zátěžového testu pomocí testu výkonnosti webu, pro kterou chcete vytvořit modul plug-in rekordéru.

2. Přidejte do řešení nový projekt **knihovny tříd** .

3. V **Průzkumníku řešení**, v nová knihovně tříd projektové složky, klikněte pravým tlačítkem **odkazy** a pak zvolte položku **přidat odkaz**.

    > [!TIP]
    > Příklad nové složky projektu knihovny třídy je **RecorderPlugins**.

     **Přidat odkaz** se zobrazí dialogové okno.

4. Vyberte **.NET** kartu.

5. Přejděte dolů a vyberte možnost **Microsoft.VisualStudio.QualityTools.WebTestFramework** a klikněte na tlačítko **OK**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** se přidá **odkazy** složky **Průzkumníku řešení**.

6. Napište kód pro modul plug-in rekordéru. Nejprve vytvořte novou veřejnou třídu, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

7. Přepsat <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> metody.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Argumenty události vám poskytne pro práci s dva objekty: zaznamenané výsledky a zaznamenaného testu výkonnosti. To vám umožní iterovat hledání pro určité hodnoty a pak skočit na stejný požadavek v testu výkonnosti webu k provádění změn výsledku. Test výkonnosti webu můžete upravit také pouze pokud byste chtěli přidat parametr context nebo parametrizovat části adresy URL.

    > [!NOTE]
    > Pokud změníte test webového výkonu, budete také muset nastavit <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> vlastnost na hodnotu true: `e.RecordedWebTestModified = true;`

8. Přidejte další kód podle toho, co jste má modul plug-in rekordéru provést po výskytu nahrávání webu. Můžete například přidat kód pro zpracování vlastní korelace, jak je znázorněno v následující ukázce. Můžete také vytvořit rekordéru modulu plug-in pro takové věci jako převod komentářů k transakci nebo přidání pravidel ověřování do webového testu.

9. Na **sestavení** nabídce zvolte **sestavení \<název projektu knihovny tříd >** .

V dalším kroku nasaďte modul plug-in zapisovače, aby se mohl zaregistrovat v aplikaci Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Nasazení modulu plug-in rekordéru

Po kompilaci modulu plug-in rekordéru, umístěte výslednou knihovnu DLL jedním ze dvou umístění:

- *% ProgramFiles (x86) %\Microsoft Visual Studio\\[verze]\\\Common7\IDE\PrivateAssemblies\WebTestPlugins [verze]*

- *\WebTestPlugins %USERPROFILE%\Documents\Visual studio [verze]*

> [!WARNING]
> Po zkopírování modulu plug-in rekordéru do jednoho ze dvou umístění, musíte restartovat Visual Studio k registraci modulu plug-in rekordéru.

### <a name="execute-the-recorder-plug-in"></a>Spuštění modulu plug-in pro záznam

1. Vytvoření nového testu výkonnosti webu.

     **Povolit WebTestRecordPlugins** zobrazí dialogové okno.

2. Zaškrtněte políčko pro doplněk rekordéru a zvolte **OK**.

     Po dokončení nahrávání testu výkonnosti webu bude spuštěn nový modul plug-in rekordéru.

    > [!WARNING]
    > Vám může se objevit chyba podobná následující při spuštění testu výkonnosti webu nebo zátěžového testu, který používá modul plug-in:
    >
    > **Požadavek se nezdařil: výjimka v \<modul plug-in > události: Nepodařilo se načíst soubor nebo sestavení '\<'. soubor dll >, verze =\<n. n. n. n >, Culture = neutral, PublicKeyToken = null nebo jedna z jeho závislostí. Systém nemůže najít zadaný soubor.**
    >
    > Důvodem je-li změnit kód na některý z modulů plug-in a vytvořit novou verzi knihovny DLL **(verze = 0.0.0.0)** , ale modul plug-in stále odkazuje původní verzi modulu plug-in. Chcete-li tento problém, postupujte podle těchto kroků:
    >
    > 1. Webový výkon a projekt zátěžového testu zobrazí se v odkazech zobrazí upozornění. Odeberte a znovu přidejte odkaz na knihovnu DLL Doplňku.
    > 2. Odeberte doplněk z vašeho testu nebo vhodného místa a znovu ho přidejte.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak vytvořit přizpůsobené záznamníku testu výkonnosti modulu plug-in pro provedení vlastní korelace dynamického parametru.

> [!NOTE]
> Úplný seznam vzorového kódu je umístěn v dolní části tohoto tématu.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Procházením skrze výsledek vyhledáte první stránku s ReportSession

Tato část ukázkového kódu prochází každý zaznamenaný objekt a hledá tělo odpovědi pro ReportSession.

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

### <a name="add-an-extraction-rule"></a>Přidání pravidla pro extrakci

Teď, když byla nalezena odpověď, musíte přidat pravidla pro extrakci. Tato část ukázkového kódu vytváří pravidlo extrakce používající <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> třídy a následně vyhledá správný požadavek v testu výkonnosti webu pro přidání pravidla extrakce. Každý objekt výsledku má přidánu novou vlastnost nazvanou DeclarativeWebTestItemId, která je, co se používá v kódu, chcete-li získat správnou žádost testu webového výkonu.

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

### <a name="replace-query-string-parameters"></a>Nahraďte parametry řetězce dotazu

Nyní kód najde všechny dotaz parametry řetězce, které mají název ReportSession a změňte hodnotu na {{Id_relace}}, jak je znázorněno v této části Ukázky kódu:

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

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Vytvoření vlastního kódu a modulů Plugin pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Generování a spuštění programový test výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
