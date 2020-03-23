---
title: Vytvoření modulu plug-in test výkonu webu
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589107"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Postup: Vytvoření modulu plug-in test výkonu webu

Moduly plug-in testů výkonu webu umožňují izolovat a znovu použít kód mimo hlavní deklarativní příkazy v testu výkonu webu. Přizpůsobený modul plug-in testu výkonu webu nabízí způsob, jak volat nějaký kód při spuštění testu výkonu webu. Modul plug-in testu výkonu webu je spuštěn jednou pro každou iteraci testu. Kromě toho pokud přepíšete metody PreRequest nebo PostRequest v testovacím modulu plug-in, budou tyto moduly plug-in požadavku spuštěny před nebo po každém požadavku.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete vytvořit vlastní webové sledování výkonu test plug-in odvozením <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> vlastní třídy ze základní třídy.

Můžete použít vlastní webové test výkonu moduly plug-in s webové testy výkonu, které jste zaznamenali, což umožňuje napsat minimální množství kódu získat větší úroveň kontroly nad testy výkonu webu. Můžete je však také použít s kódované testy výkonu webu. Další informace naleznete v [tématu Generování a spuštění kódovaného testu výkonu webu](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Můžete také vytvořit moduly plug-in zátěžového testu. Viz [Postup: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Vytvoření vlastního modulu plug-in testu výkonu webu

1. Otevřete webový výkon a zatížení testovací projekt, který obsahuje test výkonu webu.

2. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na řešení a vyberte **Přidat** a pak zvolte **Nový projekt**.

3. Vytvořte nový projekt **knihovny tříd.**

   Nový projekt knihovny tříd je přidán do **Průzkumníka řešení** a nová třída se zobrazí v **Editoru kódu**.

4. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na složku **Reference** v nové knihovně tříd a vyberte příkaz **Přidat odkaz**.

   Zobrazí se dialogové okno **Přidat odkaz.**

5. Zvolte kartu **.NET,** posuňte se dolů a vyberte **Microsoft.VisualStudio.QualityTools.WebTestFramework.**

6. Vyberte **OK**.

     Odkaz na **Microsoft.VisualStudio.QualityTools.WebTestFramework** je přidán do složky **Reference** v **Průzkumníku řešení**.

7. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na horní uzel webového výkonu a projektu zátěžového testu, který obsahuje zátěžový test, do kterého chcete přidat modul plug-in test výkonu webu, a vyberte **přidat odkaz**.

8. Zobrazí se **dialogové okno Přidat odkaz**.

9. Zvolte kartu **Projekty** a vyberte **projekt knihovny tříd**.

10. Vyberte **OK**.

11. V **Editoru kódu**napište kód svého modulu plug-in. Nejprve vytvořte novou veřejnou <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>třídu, která je odvozena od .

12. Implementujte kód uvnitř jedné nebo více obslužných rutin události. V následujícím oddílu s příklady naleznete ukázku implementace.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. Poté, co jste napsali kód, vytvořte nový projekt.

14. Otevřete test výkonu webu.

15. Chcete-li přidat modul plug-in test výkonu webu, zvolte **Přidat modul plug-in webového testu** na panelu nástrojů.

     Zobrazí se dialogové okno **Přidat modul plug-in Test webu.**

16. V části **Vyberte modul plug-in**vyberte třídu zásuvných modulů test výkonu webu.

17. V **podokně Vlastnosti vybraného modulu plug-in** nastavte počáteční hodnoty pro modul plug-in, které mají být používány za běhu.

    > [!NOTE]
    > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Můžete také změnit vlastnosti modulu plug-in test výkonu webu později pomocí okna Vlastnosti.

18. Vyberte **OK**.

     Modul plug-in je přidán do složky **modulů plug-in webového testu.**

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

Následující kód vytvoří vlastní webový test výkonu plug-in, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> který přidá položku, která představuje iteraci testu.

Po spuštění testu výkonu webu můžete pomocí tohoto modulu plug-in zobrazit přidanou položku s názvem **TestIteratnionNumber** na kartě **Kontext** v **prohlížeči výsledků webu**.

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
- [Postup: Vytvoření modulu plug-in na úrovni požadavku](../test/how-to-create-a-request-level-plug-in.md)
- [Kód vlastního pravidla extrakce pro test výkonu webu](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kód vlastního ověřovacího pravidla pro test výkonu webu](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Postup: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md)
- [Generování a spuštění programového testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
