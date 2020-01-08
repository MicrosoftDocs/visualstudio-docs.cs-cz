---
title: Vytvoření modulu Plugin pro testy výkonnosti webu úrovni požadavků
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589143"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Postupy: vytvoření modulu Plugin úrovni požadavků

*Požadavky* jsou deklarativní příkazů, které tvoří testů výkonnosti webu. Webového výkonu test moduly plug-in umožňují izolovat a opakovaně používat kód mimo hlavní deklarativní příkazů v testu výkonnosti webu. Můžete vytvořit moduly plug-in a přidat je do jednotlivý požadavek a jde o test výkonnosti webu, který jej obsahuje. Přizpůsobené *modul požadavku* nabízí způsob, jak volat kód při spuštění konkrétního požadavku v testu výkonnosti webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Každý požadavek testu výkonnosti webu modulu plug-in má PreRequest metodu a metodu PostRequest. Po připojení doplněk požadavku na požadavek http konkrétní PreRequest událost aktivuje předtím, než je vydala požadavek a PostRequest aktivována po přijetí odpovědi.

Vytvoříte vlastní webový požadavek testu výkonu modulu plug-in odvozením vlastních tříd z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> základní třídy.

Přizpůsobená webová výkonu testovací požadavek modulů plug-in můžete použít s testy výkonnosti webu, který jste nahráli. Přizpůsobená webová výkonu testovací požadavek moduly plug-in umožňuje zapsat minimální část kódu k dosažení vyšší úroveň kontroly nad testy výkonu webu. Ale také můžete je s kódované testy webového výkonu. Zobrazit [generování a spuštění programový test výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>K vytvoření modulu Plugin úrovni požadavků

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení, vyberte **přidat** a klikněte na tlačítko **nový projekt**.

2. Vytvořte nový projekt **knihovny tříd** .

3. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** složku novou knihovnu tříd a vyberte **přidat odkaz**.

     **Přidat odkaz** se zobrazí dialogové okno.

4. Zvolte **.NET** kartu, posuňte se dolů a vyberte **Microsoft.VisualStudio.QualityTools.WebTestFramework** a klikněte na tlačítko **OK**

     Odkaz na **Microsoft.VisualStudio.QualityTools.WebTestFramework** se přidá do **odkaz** složky **Průzkumníka řešení**.

5. V **Průzkumníka řešení**, klikněte pravým tlačítkem na nejvyšší uzel webového výkonu a zatížení testovacího projektu, který obsahuje zátěžový test, ke kterému chcete přidat test výkonu webu testovací požadavek modulu plug-in. Vyberte **přidat odkaz na**.

     **Zobrazí se dialogové okno Přidat odkaz**.

6. Zvolte **projekty** kartu, vyberte **projekt knihovny tříd** a klikněte na tlačítko **OK** .

7. V **Editor kódu**, psát kód modul plug-in. Nejprve vytvořte novou veřejnou třídu, která je odvozena z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

8. Implementovat kód uvnitř jeden nebo oba <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> a <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> obslužných rutin událostí. V následujícím oddílu s příklady naleznete ukázku implementace.

9. Poté, co jste napsali kód, vytvořte nový projekt.

10. Otevřete test výkonnosti webu, ke kterému chcete přidat modul požadavku.

11. Klikněte pravým tlačítkem na žádost, ke kterému chcete přidat žádost modulu plug-in a vyberte **přidat modul Plug-in požadavek**.

     **Přidat webového testu požadavku modul Plug-in** se zobrazí dialogové okno.

12. V části **vyberte modul plug-in**, vyberte nového modulu plug-in.

13. V **vlastnosti pro vybraný modul plug-in** podokno, nastavte počáteční hodnoty pro modul plug-in pro použití v době běhu.

    > [!NOTE]
    > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Modul plug-in vlastností testu výkonnosti webu můžete změnit taky později pomocí okna Vlastnosti.

14. Vyberte **OK**.

     Modul plug-in je přidán do **moduly Plugin požadavku** složce, která je podřízená složka požadavku HTTP.

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

Následující kód slouží k vytvoření vlastní testu výkonnosti webu modulu plug-in, který zobrazí dvě dialogových oknech. Zobrazí se dialogové jednu adresu URL, který je spojen s požadavkem, ke kterému připojíte – v požadavku. Druhý dialogu zobrazí název počítače pro agenta.

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

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Vytvoření vlastního kódu a modulů Plugin pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Kód vlastního pravidla extrakce pro test výkonnosti webu](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kód vlastního ověřovacího pravidla pro test výkonnosti webu](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Postupy: vytvoření modulu Plugin pro zátěžový test](../test/how-to-create-a-load-test-plug-in.md)
- [Generování a spuštění programový test výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
