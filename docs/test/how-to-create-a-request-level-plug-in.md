---
title: Vytvoření modulu plug-in na úrovni požadavků pro testy výkonnosti webu
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03de870da2cd75c8a254010db682903f314cc10d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287971"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Postupy: Vytvoření modulu plug-in na úrovni požadavků

*Požadavky* jsou deklarativní příkazy, které představují testy výkonnosti webu. Moduly plug-in testu výkonnosti webu umožňují izolovat a znovu použít kód mimo hlavní deklarativní příkazy v testu výkonnosti webu. Můžete vytvářet moduly plug-in a přidávat je do jednotlivých požadavků a také do testu výkonnosti webu, který ho obsahuje. Přizpůsobený  *modul plug-in pro žádosti* nabízí způsob volání kódu jako konkrétní požadavek, který je spuštěn v testu výkonnosti webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Každý modul plug-in žádosti o test výkonnosti webu má metodu předzpracování a metodu PostRequest. Po připojení modulu plug-in žádosti k konkrétnímu požadavku HTTP se událost před vyžádáním aktivuje před vydáním žádosti a PostRequest se vyvolal po přijetí odpovědi.

Můžete vytvořit přizpůsobený modul plug-in žádosti o test výkonnosti webu odvozením vlastní třídy ze <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> základní třídy.

Můžete použít vlastní moduly plug-in žádosti o test výkonnosti webu s testy webového výkonu, které jste si poznamenali. Přizpůsobený modul plug-in žádosti o test výkonnosti webu vám umožní napsat minimální množství kódu, abyste dosáhli vyšší úrovně kontroly nad testy výkonnosti webu. Můžete je však také použít s kódovanými testy výkonnosti webu. Viz [vygenerování a spuštění kódovaného testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>Vytvoření modulu plug-in na úrovni požadavků

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na řešení, vyberte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

2. Vytvořte nový projekt **knihovny tříd** .

3. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **odkazy** v nové knihovně tříd a vyberte možnost **Přidat odkaz**.

     Zobrazí se dialogové okno **Přidat odkaz** .

4. Zvolte kartu **.NET** , posuňte se dolů, vyberte **Microsoft. VisualStudio. QualityTools. WebTestFramework** a pak zvolte **OK** .

     Odkaz na **Microsoft. VisualStudio. QualityTools. WebTestFramework** se přidá do **referenční** složky v **Průzkumník řešení**.

5. V **Průzkumník řešení**klikněte pravým tlačítkem myši na nejvyšší uzel projektu testování výkonu webu a zátěžového testu, který obsahuje zátěžový test, ke kterému chcete přidat modul plug-in test výkonnosti webu. Vyberte **Přidat odkaz**.

     **Zobrazí se dialogové okno Přidat odkaz**.

6. Zvolte kartu **projekty** , vyberte **projekt knihovny tříd** a pak zvolte **OK** .

7. V **editoru kódu**napište kód modulu plug-in. Nejprve vytvořte novou veřejnou třídu, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> .

8. Implementujte kód uvnitř jedné nebo obou <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> obslužných rutin událostí a. V následujícím oddílu s příklady naleznete ukázku implementace.

9. Poté, co jste napsali kód, vytvořte nový projekt.

10. Otevřete test výkonnosti webu, do kterého chcete přidat modul plug-in žádosti.

11. Klikněte pravým tlačítkem na žádost, do které chcete přidat modul plug-in žádosti, a vyberte **Přidat modul plug-in žádosti**.

     Zobrazí se dialogové okno **Přidat modul požadavku webového testu** .

12. V části **Vyberte modul plug-in**vyberte nový modul plug-in.

13. V podokně **vlastnosti pro vybraný modul plug-in** nastavte počáteční hodnoty pro modul plug-in, které se použijí v době běhu.

    > [!NOTE]
    > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Vlastnosti modulu plug-in testu výkonnosti webu lze také změnit později pomocí okno Vlastnosti.

14. Vyberte **OK**.

     Modul plug-in se přidá do složky **modulů plug-in žádosti** , která je podřízenou složkou požadavku HTTP.

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

Pomocí následujícího kódu lze vytvořit přizpůsobený modul plug-in testu výkonnosti webu, který zobrazí dvě dialogová okna. V jednom dialogovém okně se zobrazí adresa URL, která je přidružená k žádosti, ke které připojíte doplněk žádosti. Druhý dialog zobrazí název počítače pro agenta.

> [!NOTE]
> Následující kód vyžaduje přidání odkazu na System.Windows.Forms.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Kód vlastní pravidlo extrakce pro test výkonnosti webu](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kódování vlastního ověřovacího pravidla pro test výkonnosti webu](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Postupy: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md)
- [Generování a spuštění programového testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
