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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565159"
---
# <a name="best-practices-for-coded-ui-tests"></a>Osvědčené postupy pro programové testy uživatelského rozhraní

Toto téma popisuje některá doporučení pro vývoj kódovaných testů uživatelského rozhraní.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>Osvědčené postupy

Použijte následující pokyny pro vytvoření flexibilního programového testu uživatelského rozhraní.

- Pokud je to možné, použijte Tvůrce programového **testu uživatelského rozhraní** .

- Neupravujte soubor *UIMap.Designer.cs* přímo. Pokud soubor upravíte, změny v souboru budou přepsány.

- Vytvořte svůj test jako sekvenci zaznamenaných metod. Další informace o tom, jak zaznamenat metodu, naleznete v tématu vytváření programových [testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md).

- Každá zaznamenaná metoda by měla fungovat na jedné stránce, formuláři nebo dialogovém okně. Vytvořte novou testovací metodu pro každou novou stránku, formulář nebo dialogové okno.

- Při vytváření metody použijte smysluplný název metody namísto výchozího názvu. Smysluplný název pomáhá identifikovat účel metody.

- Pokud je to možné, omezte každou zaznamenanou metodu na méně než 10 akcí. Tento přístup do modulárního prostředí usnadňuje nahrazení metody, pokud se změní uživatelské rozhraní.

- Vytvořte jednotlivé kontrolní výrazy pomocí **Tvůrce programového testu UI**, který automaticky přidá metodu assertion do souboru *UIMap.Designer.cs* .

- Pokud se změní uživatelské rozhraní (UI), znovu zaznamenejte testovací metody nebo metody kontrolního výrazu nebo znovu zaznamenejte ovlivněné části stávající testovací metody.

- Vytvořte samostatný soubor [UIMap](/previous-versions/dd580454(v=vs.140)) pro každý modul v testované aplikaci. Další informace najdete v tématu [testování velké aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md).

- V testované aplikaci použijte při vytváření ovládacích prvků uživatelského rozhraní smysluplné názvy. Použití smysluplných názvů poskytuje větší přehlednost a použitelnost pro automaticky vygenerované názvy ovládacích prvků.

- Pokud vytváříte kontrolní výrazy pomocí kódování pomocí rozhraní API, vytvořte metodu pro každý kontrolní výraz v části třídy [UIMap](/previous-versions/dd580454(v=vs.140)) , která je v souboru *UIMap.cs* . Chcete-li spustit kontrolní výraz, zavolejte tuto metodu z vaší zkušební metody.

- Pokud přímo kódujete pomocí rozhraní API, použijte vlastnosti a metody v třídách vygenerovaných v souboru *UIMap.Designer.cs* v kódu tak, jak můžete. Díky těmto třídám bude vaše práce snazší a spolehlivější a pomůžou vám zvýšit produktivitu.

Programové testy uživatelského rozhraní jsou automaticky přizpůsobeny mnoha změnám v uživatelském rozhraní. Pokud například prvek uživatelského rozhraní má změnu pozice nebo barvy, ve většině případů bude programový test UI stále najít správný prvek.

Během testovacího běhu jsou ovládací prvky uživatelského rozhraní umístěny pomocí testovací architektury pomocí sady vlastností hledání. Vlastnosti hledání jsou aplikovány na každou třídu ovládacího prvku v definicích vytvořených **tvůrcem programového testu UI** v souboru *UIMap.Designer.cs* . Vlastnosti hledání obsahují páry název-hodnota názvů vlastností a hodnot vlastností, které lze použít k identifikaci ovládacího prvku, například <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>a <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> vlastnosti ovládacího prvku. Pokud se vlastnosti hledání nezměnily, Programový test uživatelského rozhraní úspěšně najde ovládací prvek v uživatelském rozhraní. Pokud se změní vlastnosti hledání, Programový test UI má algoritmus inteligentního porovnávání, který používá heuristiky pro hledání ovládacích prvků a oken v uživatelském rozhraní. Po změně uživatelského rozhraní může být možné upravit vlastnosti hledání dříve identifikovaných prvků, aby bylo zajištěno, že budou nalezeny.

## <a name="if-your-user-interface-changes"></a>Pokud se změní vaše uživatelské rozhraní

Uživatelská rozhraní se často mění během vývoje. Tady je několik způsobů, jak snížit dopad těchto změn:

- Najděte zaznamenanou metodu, která odkazuje na tento ovládací prvek, a použijte Tvůrce programového **testu uživatelského rozhraní** k opakovanému nahrání akcí pro tuto metodu. Můžete použít stejný název pro metodu k přepsání existujících akcí.

- Má-li ovládací prvek kontrolní výraz, který již není platný:

  - Odstraňte metodu, která obsahuje kontrolní výraz.

  - Odeberte volání této metody z testovací metody.

  - Přidejte nový kontrolní výraz přetažením tlačítka křížového vlasů do ovládacího prvku uživatelského rozhraní, otevřete mapu uživatelského rozhraní a přidejte nový kontrolní výraz.

Další informace o tom, jak zaznamenat programové testy UI, naleznete v tématu [použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md).

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Pokud proces na pozadí musí být dokončen, aby mohl pokračovat test

Je možné, že budete muset počkat na dokončení procesu, aby bylo možné pokračovat v další akci uživatelského rozhraní. K tomu můžete použít <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> k čekání před pokračováním testu, jako v následujícím příkladu:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Viz také:

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Vytváření programových testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
