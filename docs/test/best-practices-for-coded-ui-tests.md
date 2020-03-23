---
title: Doporučené postupy pro programové testy UI
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e71029a185d1b3fea1812b2a4b1cf7bf20effff8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565159"
---
# <a name="best-practices-for-coded-ui-tests"></a>Doporučené postupy pro kódované testy rozhraní

Toto téma popisuje některá doporučení pro vývoj kódovaných testů ui.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>Osvědčené postupy

Pomocí následujících pokynů vytvořte flexibilní kódovaný test ui.

- Pokud je to možné, používejte **tvůrce testů kódovaného ui.**

- Neupravujte soubor *UIMap.designer.cs* přímo. Pokud soubor upravíte, změny v souboru budou přepsány.

- Vytvořte test jako posloupnost zaznamenaných metod. Další informace o tom, jak zaznamenat metodu, naleznete [v tématu Vytváření kódovaných testů ui](../test/use-ui-automation-to-test-your-code.md).

- Každá zaznamenaná metoda by měla fungovat na jedné stránce, formuláři nebo dialogovém okně. Vytvořte novou testovací metodu pro každou novou stránku, formulář nebo dialogové okno.

- Při vytváření metody použijte místo výchozího názvu smysluplný název metody. Smysluplný název pomáhá identifikovat účel metody.

- Pokud je to možné, omezte každou zaznamenanou metodu na méně než 10 akcí. Tento modulární přístup usnadňuje nahrazení metody, pokud se změní ui.

- Vytvořte každý kontrolní výraz pomocí **Tvůrce testovaného ui coded**, který automaticky přidá metodu assertion do *souboru UIMap.Designer.cs.*

- Pokud se změní uživatelské rozhraní (UI), znovu zaznamenejte zkušební metody nebo metody kontrolního výrazu nebo znovu zaznamenejte ovlivněné části existující zkušební metody.

- Vytvořte samostatný soubor [UIMap](/previous-versions/dd580454(v=vs.140)) pro každý modul v testovce aplikace. Další informace naleznete [v tématu Testování velké aplikace s více mapami ui](../test/testing-a-large-application-with-multiple-ui-maps.md).

- V testovce aplikace použijte smysluplné názvy při vytváření ovládacích prvků ui. Použití smysluplné názvy dává větší jasnost a použitelnost automaticky generované názvy ovládacích prvků.

- Pokud vytváříte kontrolní výrazy kódováním pomocí rozhraní API, vytvořte metodu pro každý kontrolní výraz v části třídy [UIMap,](/previous-versions/dd580454(v=vs.140)) která je v *souboru UIMap.cs.* Chcete-li spustit kontrolní výraz, volání této metody z testovací metody.

- Pokud jste přímo kódování s rozhraním API, použijte vlastnosti a metody ve třídách generovaných v *souboru UIMap.Designer.cs* v kódu, stejně jako je to možné. Tyto třídy vám usnadní práci, budou spolehlivější a pomohou vám zvýšit produktivitu.

Programové testy uživatelského rozhraní se automaticky přizpůsobí mnoha změnám v uživatelském rozhraní. Pokud například prvek ui změnil pozici nebo barvu, většinu času kódované ho testu ui stále najde správný prvek.

Během testovacího běhu jsou ovládací prvky ui umístěny pomocí testovacího rámce pomocí sady vlastností hledání. Vlastnosti hledání jsou použity pro každou třídu ovládacího prvku v definicích vytvořených **Tvůrcem testovaných ui v** *UIMap.Designer.cs* souboru. Vlastnosti hledání obsahují dvojice názvů a hodnot názvů vlastností a hodnot vlastností, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A> <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>které <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> lze použít k identifikaci ovládacího prvku, například , a vlastnosti ovládacího prvku. Pokud jsou vlastnosti hledání beze změny, kódovaný test ui úspěšně najde ovládací prvek v unovém rozhraní. Pokud se změní vlastnosti hledání, kódované testy ui mají inteligentní shodu algoritmus, který používá heuristiky najít ovládací prvky a okna v ui. Pokud se uživatelské rozhraní změní, můžete upravit vlastnosti hledání dříve identifikovaných prvků a ujistěte se, že jsou nalezeny.

## <a name="if-your-user-interface-changes"></a>Pokud se uživatelské rozhraní změní

Uživatelská rozhraní se často mění během vývoje. Zde je několik způsobů, jak snížit účinek těchto změn:

- Najděte zaznamenanou metodu, která odkazuje na tento ovládací prvek, a pomocí **tvůrce testů programového ui** znovu zaznamenejte akce pro tuto metodu. Pro metodu můžete použít stejný název k přepsání existujících akcí.

- Pokud ovládací prvek má kontrolní výraz, který již není platný:

  - Odstraňte metodu, která obsahuje kontrolní výraz.

  - Odeberte volání této metody z testovací metody.

  - Přidejte nový kontrolní výraz přetažením nitkového kříže do ovládacího prvku ui, otevřete mapu ui a přidejte nový kontrolní výraz.

Další informace o tom, jak zaznamenat kódované testy uživatelského rozhraní, naleznete [v tématu Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md).

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Pokud je třeba dokončit proces na pozadí, než může test pokračovat

Možná budete muset počkat, dokud proces neskončí, než budete moci pokračovat v další akci ui. Chcete-li to <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> provést, můžete počkat, než test pokračuje, jako v následujícím příkladu:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Viz také

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Vytváření kódovaných testů ui](../test/use-ui-automation-to-test-your-code.md)
- [Testování velké aplikace s více mapami ui](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Podporované konfigurace a platformy pro kódované testy a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
