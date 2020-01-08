---
title: Vytvoření modulu Plugin pro Test výkonnosti webu
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc2eeafa41b953f9d853c7ff435a6a9706ae73ca
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589107"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Postupy: vytvoření modulu Plugin pro test výkonnosti webu

Webového výkonu testy moduly plug-in umožňují izolovat a opakovaně používat kód mimo hlavní deklarativní příkazů v testu výkonnosti webu. Modul plug-in testu výkonnosti webu přizpůsobené nabízí způsob, jak volat nějaký kód při spuštění testu výkonnosti webu. Modul plug-in testu výkonnosti webu je spustit jednou pro každou iteraci testu. Kromě toho pokud přepíšete metodu PreRequest nebo PostRequest v modulu plug-in testu, tyto moduly plug-in požadavku se spustit před nebo po každého požadavku, v uvedeném pořadí.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete vytvořit test výkonnosti webu vlastní modul plug-in odvozením vlastních tříd z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> základní třídy.

Můžete použít vlastní web výkon testu moduly plug-in s testy výkonnosti webu, který jste nahráli, která umožňuje zapsat minimální část kódu a získat vyšší úroveň kontroly nad testy výkonu webu. Ale také můžete je s kódované testy webového výkonu. Další informace najdete v tématu [generování a spuštění programový test výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Můžete také vytvořit moduly plug-in zátěžového testu. Viz [Postupy: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Můžete vytvořit modul plug-in testu výkonnosti webu vlastní

1. Otevřete webový výkon a projekt zátěžového testu, který obsahuje test výkonnosti webu.

2. V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení a vyberte **přidat** a klikněte na tlačítko **nový projekt**.

3. Vytvořte nový projekt **knihovny tříd** .

   Nový projekt knihovny tříd je přidána do **Průzkumníka řešení** a nová třída se objeví v **Editor kódu**.

4. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** složku novou knihovnu tříd a vyberte **přidat odkaz**.

   **Přidat odkaz** se zobrazí dialogové okno.

5. Zvolte **.NET** kartu, posuňte se dolů a vyberte **Microsoft.VisualStudio.QualityTools.WebTestFramework**

6. Vyberte **OK**.

     Odkaz na **Microsoft.VisualStudio.QualityTools.WebTestFramework** se přidá do **odkaz** složky **Průzkumníka řešení**.

7. V **Průzkumníka řešení**, klikněte pravým tlačítkem na nejvyšší uzel webového výkonu a zatížení testovacího projektu, který obsahuje zátěžový test, ke kterému chcete přidat modul plug-in a vyberte test výkonnosti webu **přidat odkaz**.

8. **Zobrazí se dialogové okno Přidat odkaz**.

9. Zvolte **projekty** kartě a vyberte **projekt knihovny tříd**.

10. Vyberte **OK**.

11. V **Editor kódu**, psát kód modul plug-in. Nejprve vytvořte novou veřejnou třídu, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

12. Implementujte kód uvnitř jednoho nebo více obslužných rutin událostí. V následujícím oddílu s příklady naleznete ukázku implementace.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. Poté, co jste napsali kód, vytvořte nový projekt.

14. Otevřete test výkonnosti webu.

15. Chcete-li přidat modul plug-in testu výkonnosti webu, zvolte **přidat modul Plug-in pro Test webové** na panelu nástrojů.

     **Přidat modul webového testu Plug-in** se zobrazí dialogové okno.

16. V části **vyberte modul plug-in**vyberte modul plug-in třídu testu výkonu webu.

17. V **vlastnosti pro vybraný modul plug-in** podokno, nastavte počáteční hodnoty pro modul plug-in pro použití v době běhu.

    > [!NOTE]
    > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Modul plug-in vlastností testu výkonnosti webu můžete změnit taky později pomocí okna Vlastnosti.

18. Vyberte **OK**.

     Modul plug-in je přidán do **zásuvné moduly webového testu** složky.

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

Následující kód vytvoří přizpůsobené testu výkonnosti webu modulu plug-in, který přidá položku do <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> , která představuje iteraci testu.

Po spuštění testu výkonnosti webu se prostřednictvím tohoto modulu plug-in uvidíte přidanou položku s názvem **TestIteratnionNumber** v **kontextu** kartu **prohlížeče výsledků výkonnosti webu** .

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleRules
{
    [Description("This plugin can be used to set the ParseDependentsRequests property for each request")]
    public class SampleWebTestPlugin : WebTestPlugin
    {
        private bool m_parseDependents = true;

        public override void PreWebTest(object sender, PreWebTestEventArgs e)
        {
            // TODO: Add code to execute before the test.
        }

        public override void PostWebTest(object sender, PostWebTestEventArgs e)
        {
            // TODO: Add code to execute after the test.
        }

        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            // Code to execute before each request.
            // Set the ParseDependentsRequests value on the request
            e.Request.ParseDependentRequests = m_parseDependents;
        }

        // Properties for the plugin.
        [DefaultValue(true)]
        [Description("All requests will have their ParseDependentsRequests property set to this value")]
        public bool ParseDependents
        {
            get
            {
                return m_parseDependents;
            }
            set
            {
                m_parseDependents = value;
            }
        }
    }
}
```

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Vytvoření vlastního kódu a modulů Plugin pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: vytvoření modulu Plugin úrovni požadavků](../test/how-to-create-a-request-level-plug-in.md)
- [Kód vlastního pravidla extrakce pro test výkonnosti webu](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kód vlastního ověřovacího pravidla pro test výkonnosti webu](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Postupy: vytvoření modulu Plugin pro zátěžový test](../test/how-to-create-a-load-test-plug-in.md)
- [Generování a spuštění programový test výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
