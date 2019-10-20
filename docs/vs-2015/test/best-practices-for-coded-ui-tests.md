---
title: Osvědčené postupy pro programové testy uživatelského rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 41
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2dffebeaa0349c149e319d20794f8b065baa5647
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660691"
---
# <a name="best-practices-for-coded-ui-tests"></a>Doporučené postupy pro programové testy UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje osvědčené postupy, které je třeba provést při vývoji programových testů uživatelského rozhraní.

 **Požadavky**

- Visual Studio Enterprise

## <a name="best-practices"></a>Doporučené postupy
 Použijte následující pokyny pro vytvoření flexibilního programového testu uživatelského rozhraní.

- Pokud je to možné, použijte Tvůrce programového **testu uživatelského rozhraní** .

- Neupravujte soubor `UIMap.designer.cs` přímo. Pokud to uděláte, změny v souboru budou přepsány.

- Vytvořte svůj test jako sekvenci zaznamenaných metod. Další informace o tom, jak zaznamenat metodu, naleznete v tématu vytváření programových [testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

- Každá zaznamenaná metoda by měla fungovat na jedné stránce, formuláři nebo dialogovém okně. Vytvořte novou testovací metodu pro každou novou stránku, formulář nebo dialogové okno.

- Při vytváření metody použijte smysluplný název metody namísto výchozího názvu. Smysluplný název pomáhá identifikovat účel metody.

- Pokud je to možné, omezte každou zaznamenanou metodu na méně než 10 akcí. Tento přístup do modulárního prostředí usnadňuje nahrazení metody, pokud se změní uživatelské rozhraní.

- Vytvořte jednotlivé kontrolní výrazy pomocí **Tvůrce programového testu UI**, který automaticky přidá metodu assertion do souboru `UIMap.Designer.cs`.

- Pokud se změní uživatelské rozhraní (UI), znovu zaznamenejte testovací metody nebo metody kontrolního výrazu nebo znovu zaznamenejte ovlivněné části stávající testovací metody.

- Vytvořte samostatný soubor [UIMap](/previous-versions/dd580454(v=vs.140)) pro každý modul v testované aplikaci. Další informace najdete v tématu [testování velké aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md).

- V testované aplikaci použijte při vytváření ovládacích prvků uživatelského rozhraní smysluplné názvy. To poskytuje větší význam a použitelnost pro automaticky vygenerované názvy ovládacích prvků.

- Pokud vytváříte kontrolní výrazy pomocí kódování pomocí rozhraní API, vytvořte metodu pro každý kontrolní výraz v části třídy [UIMap](/previous-versions/dd580454(v=vs.140)) , která je v souboru `UIMap.cs`. Zavolejte tuto metodu z vaší zkušební metody pro provedení kontrolního výrazu.

- Pokud přímo kódujete pomocí rozhraní API, použijte vlastnosti a metody v třídách vygenerovaných v `UIMap.Designer.cs` souboru ve vašem kódu, co můžete. Díky těmto třídám bude vaše práce snazší a spolehlivější a pomůžou vám zvýšit produktivitu.

  Programové testy uživatelského rozhraní jsou automaticky přizpůsobeny mnoha změnám v uživatelském rozhraní. Pokud například prvek uživatelského rozhraní má změnu pozice nebo barvy, ve většině případů bude programový test UI stále najít správný prvek.

  Během testovacího běhu jsou ovládací prvky uživatelského rozhraní umístěny rozhraním pro testování pomocí sady vlastností hledání, které jsou použity na každou třídu ovládacího prvku v definicích vytvořených **tvůrcem programového testu uživatelského rozhraní** v souboru `UIMap.Designer.cs`. Vlastnosti hledání obsahují páry název-hodnota názvů vlastností a hodnot vlastností, které lze použít k identifikaci ovládacího prvku, například <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> a <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> vlastnosti ovládacího prvku. Pokud se vlastnosti hledání nezměnily, Programový test uživatelského rozhraní úspěšně najde ovládací prvek v uživatelském rozhraní. Pokud se změní vlastnosti hledání, Programový test UI má algoritmus inteligentního porovnávání, který v uživatelském rozhraní používá heuristiky k hledání ovládacích prvků a oken. Po změně uživatelského rozhraní může být možné upravit vlastnosti hledání dříve identifikovaných prvků, aby bylo zajištěno, že budou nalezeny.

## <a name="what-to-do-if-your-user-interface-changes"></a>Co dělat, když se změní uživatelské rozhraní
 Uživatelská rozhraní se často mění během vývoje. Tady je několik způsobů, jak snížit dopad těchto změn:

- Najděte zaznamenanou metodu, která odkazuje na tento ovládací prvek a pomocí Tvůrce programového **testu UI** znovu zaznamená akce pro tuto metodu. Můžete použít stejný název pro metodu k přepsání existujících akcí.

- Má-li ovládací prvek kontrolní výraz, který již není platný:

  - Odstraňte metodu, která obsahuje kontrolní výraz.

  - Odeberte volání této metody z testovací metody.

  - Přidejte nový kontrolní výraz přetažením tlačítka křížového vlasů do ovládacího prvku uživatelského rozhraní, otevřete mapu uživatelského rozhraní a přidejte nový kontrolní výraz.

  Další informace o tom, jak zaznamenat programové testy UI, naleznete v tématu [použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md).

## <a name="what-to-do-if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Co dělat v případě, že proces na pozadí musí být dokončen, aby mohl pokračovat test
 Je možné, že budete muset počkat na dokončení procesu, aby bylo možné pokračovat v další akci uživatelského rozhraní. K tomu můžete použít <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> k čekání před tím, než test pokračuje, jako v následující ukázce.

```
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
- [Vytváření programových testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
