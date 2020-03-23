---
title: Vytvoření modulu plug-in na úrovni požadavků pro testy výkonu webu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6e57f92a3f45983321a866f3524974ea99dba82
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589143"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Postup: Vytvoření modulu plug-in na úrovni požadavku

*Požadavky* jsou deklarativní příkazy, které představují testy výkonu webu. Moduly plug-in testu výkonu webu umožňují izolovat a znovu použít kód mimo hlavní deklarativní příkazy v testu výkonu webu. Můžete vytvořit moduly plug-in a přidat je do individuálního požadavku a také do testu výkonu webu, který jej obsahuje. Přizpůsobený *modul plug-in požadavku* nabízí způsob, jak volat kód jako konkrétní požadavek je spuštěn v testu výkonu webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Každý modul plug-in požadavku na test výkonu webu má metodu PreRequest a metodu PostRequest. Po připojení požadavku plug-in na konkrétní požadavek http, preRequest událost bude aktivována před žádost je vydána a PostRequest aktivována po přijetí odpovědi.

Můžete vytvořit vlastní webové test výkonu požadavek plug-in odvozením <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> vlastní třídy ze základní třídy.

S nahranými testy výkonu webu můžete použít vlastní moduly plug-in testů výkonnosti webu. Přizpůsobené webové test výkonu test plug-iny umožňují napsat minimální množství kódu k dosažení větší úroveň kontroly nad testy výkonu webu. Můžete je však také použít s kódované testy výkonu webu. Viz [Generovat a spustit kódovaný test výkonu webu](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>Vytvoření modulu plug-in na úrovni požadavku

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na řešení, vyberte **Přidat** a pak zvolte **Nový projekt**.

2. Vytvořte nový projekt **knihovny tříd.**

3. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na složku **Reference** v nové knihovně tříd a vyberte příkaz **Přidat odkaz**.

     Zobrazí se dialogové okno **Přidat odkaz.**

4. Zvolte kartu **.NET,** posuňte se dolů, vyberte **Microsoft.VisualStudio.QualityTools.WebTestFramework** a pak zvolte **OK**

     Odkaz na **Microsoft.VisualStudio.QualityTools.WebTestFramework** je přidán do složky **Reference** v **Průzkumníku řešení**.

5. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na horní uzel webového výkonu a zatížení testovací projekt, který obsahuje zátěžový test, do kterého chcete přidat webový test výkonu test test test plug-in. Vyberte **Přidat odkaz**.

     Zobrazí se **dialogové okno Přidat odkaz**.

6. Zvolte kartu **Projekty,** vyberte **Projekt knihovny tříd** a pak zvolte **OK** .

7. V **Editoru kódu**napište kód svého modulu plug-in. Nejprve vytvořte novou veřejnou <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>třídu, která je odvozena od .

8. Implementujte kód uvnitř jednoho <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> nebo obou obslužných rutin a událostí. V následujícím oddílu s příklady naleznete ukázku implementace.

9. Poté, co jste napsali kód, vytvořte nový projekt.

10. Otevřete test výkonu webu, do kterého chcete přidat modul plug-in požadavku.

11. Klikněte pravým tlačítkem myši na požadavek, ke kterému chcete přidat modul plug-in požadavku, a vyberte **přidat modul plug-in požadavku**.

     Zobrazí se dialogové okno **Přidat zásuvný modul požadavku webového testu.**

12. V části **Vyberte modul plug-in**vyberte nový modul plug-in.

13. V **podokně Vlastnosti vybraného modulu plug-in** nastavte počáteční hodnoty pro modul plug-in, které mají být používány za běhu.

    > [!NOTE]
    > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Můžete také změnit vlastnosti modulu plug-in test výkonu webu později pomocí okna Vlastnosti.

14. Vyberte **OK**.

     Modul plug-in je přidán do složky **Požadavku modulů plug-in,** což je podřízená složka požadavku HTTP.

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

Následující kód můžete použít k vytvoření přizpůsobeného modulu plug-in testu výkonu webu, který zobrazuje dvě dialogová okna. V jednom dialogovém okně se zobrazí adresa URL přidružená k požadavku, ke kterému připojujete doplněk požadavku. Ve druhém dialogovém okně se zobrazí název počítače agenta.

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
- [Kód vlastního pravidla extrakce pro test výkonu webu](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kód vlastního ověřovacího pravidla pro test výkonu webu](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Postup: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md)
- [Generování a spuštění programového testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
