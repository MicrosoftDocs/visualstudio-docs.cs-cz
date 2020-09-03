---
title: Vytvoření modulu plug-in testu výkonnosti webu
ms.date: 10/03/2016
ms.topic: how-to
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c9651f4003647e18ba52e916aeb21e176274de5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287932"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Postupy: Vytvoření modulu plug-in testu výkonnosti webu

Moduly plug-in testů výkonnosti webu umožňují izolovat a znovu použít kód mimo hlavní deklarativní příkazy v testu výkonnosti webu. Přizpůsobený modul plug-in testu výkonnosti webu nabízí způsob, jak volat nějaký kód při spuštění testu výkonnosti webu. Modul plug-in testu výkonnosti webu je spuštěn jednou pro každou iteraci testu. Kromě toho, pokud přepíšete metody požadavků nebo PostRequest v modulu plug-in test, tyto moduly plug-in se spustí před nebo po každém požadavku.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Přizpůsobený modul plug-in testu výkonnosti webu můžete vytvořit odvozením vlastní třídy ze <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> základní třídy.

Můžete použít vlastní moduly plug-in testu výkonnosti webu s testy webového výkonu, které jste nahráli, což vám umožní napsat minimální množství kódu, abyste získali větší úroveň kontroly nad testy výkonnosti webu. Můžete je však také použít s kódovanými testy výkonnosti webu. Další informace naleznete v tématu [generování a spuštění kódovaného testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Můžete také vytvořit moduly plug-in zátěžového testu. Viz [Postupy: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Vytvoření vlastního modulu plug-in testu výkonnosti webu

1. Otevřete projekt webového výkonu a zátěžového testu, který obsahuje test výkonnosti webu.

2. V **Průzkumník řešení**klikněte pravým tlačítkem na řešení a vyberte **Přidat** a pak zvolte **Nový projekt**.

3. Vytvořte nový projekt **knihovny tříd** .

   Nový projekt knihovny tříd je přidán do **Průzkumník řešení** a nová třída se zobrazí v **editoru kódu**.

4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **odkazy** v nové knihovně tříd a vyberte možnost **Přidat odkaz**.

   Zobrazí se dialogové okno **Přidat odkaz** .

5. Zvolte kartu **.NET** , přejděte dolů a vyberte **Microsoft. VisualStudio. QualityTools. WebTestFramework.**

6. Vyberte **OK**.

     Odkaz na **Microsoft. VisualStudio. QualityTools. WebTestFramework** se přidá do **referenční** složky v **Průzkumník řešení**.

7. V **Průzkumník řešení**klikněte pravým tlačítkem myši na nejvyšší uzel projektu webového výkonu a zátěžového testu, který obsahuje zátěžový test, ke kterému chcete přidat modul plug-in testu výkonnosti webu, a vyberte možnost **Přidat odkaz**.

8. **Zobrazí se dialogové okno Přidat odkaz**.

9. Zvolte kartu **projekty** a vyberte **projekt knihovny tříd**.

10. Vyberte **OK**.

11. V **editoru kódu**napište kód modulu plug-in. Nejprve vytvořte novou veřejnou třídu, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> .

12. Implementujte kód uvnitř jedné nebo více obslužných rutin událostí. V následujícím oddílu s příklady naleznete ukázku implementace.

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

15. Chcete-li přidat modul plug-in testu výkonnosti webu, vyberte možnost **Přidat modul plug-in webového testu** na panelu nástrojů.

     Zobrazí se dialogové okno **Přidat modul plug-in webového testu** .

16. V části **Vybrat modul plug-in**vyberte třídu modulu plug-in test výkonnosti webu.

17. V podokně **vlastnosti pro vybraný modul plug-in** nastavte počáteční hodnoty pro modul plug-in, které se použijí v době běhu.

    > [!NOTE]
    > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Vlastnosti modulu plug-in testu výkonnosti webu lze také změnit později pomocí okno Vlastnosti.

18. Vyberte **OK**.

     Modul plug-in se přidá do složky **moduly plug-in webového testu** .

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

Následující kód vytvoří přizpůsobený modul plug-in testu výkonnosti webu, který přidá položku do <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> , která představuje iteraci testu.

Po spuštění testu výkonnosti webu můžete pomocí tohoto modulu plug-in zobrazit přidanou položku s názvem **TestIteratnionNumber** na kartě **kontext** v **prohlížeči výsledků výkonu webu**.

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

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: Vytvoření modulu plug-in na úrovni požadavků](../test/how-to-create-a-request-level-plug-in.md)
- [Kód vlastní pravidlo extrakce pro test výkonnosti webu](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kódování vlastního ověřovacího pravidla pro test výkonnosti webu](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Postupy: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md)
- [Generování a spuštění programového testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
