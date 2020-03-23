---
title: Rozhraní API testu výkonu webu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e869bc46997ffb6ebecae2aa3e49c3cb6b2582fa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594328"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Postup: Použití rozhraní API pro testování výkonu webu

Můžete napsat kód pro vaše testy výkonu webu. Rozhraní API pro testování výkonu webu se používá k vytvoření kódovaných testů výkonu webu, modulů plug-in testů výkonu webu, modulů plug-in požadavků, požadavků, pravidel extrakce a ověřovacích pravidel. Třídy, které tvoří tyto typy jsou základní třídy v tomto rozhraní API. Ostatní typy v tomto rozhraní API <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest> <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>slouží <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>k <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>podpoře <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> vytváření , , , a objektů. Obor <xref:Microsoft.VisualStudio.TestTools.WebTesting> názvů slouží k vytvoření přizpůsobených testů výkonu webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pomocí rozhraní API pro testování výkonu webu můžete také programově vytvářet a ukládat deklarativní testy výkonu webu. Chcete-li to <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> provést, použijte třídy a. <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer>

> [!TIP]
> Pomocí prohlížeče objektů zkontrolujte <xref:Microsoft.VisualStudio.TestTools.WebTesting> obor názvů. Editory Visual C# i Visual Basic nabízejí podporu technologie IntelliSense pro kódování s třídami v oboru názvů.

Můžete také vytvořit moduly plug-in pro zátěžové testy. Další informace naleznete v [tématu Postup: Použití rozhraní API zátěžového testu](../test/how-to-use-the-load-test-api.md) a [postup: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Použití oboru názvů WebTesting

1. Otevřete webový výkon a zatížení testovací projekt, který obsahuje test výkonu webu.

2. Přidejte do testovacího řešení projekt knihovny tříd visual c# nebo visual basic.

3. Přidejte odkaz ve webovém výkonu a projektu zátěžového testu do projektu knihovny tříd.

4. Přidejte odkaz na knihovnu DLL Microsoft.VisualStudio.QualityTools.WebTestFramework v projektu knihovny tříd.

5. V souboru třídy, který je umístěn `using` v projektu <xref:Microsoft.VisualStudio.TestTools.WebTesting> knihovny tříd, přidejte příkaz pro obor názvů.

6. Vytvořte třídu, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> která implementuje rozhraní.

7. Sestavte projekt.

8. Přidejte nový modul plug-in testu výkonu webu pomocí Editoru testů výkonu webu:

    1. Na panelu nástrojů zvolte **Přidat modul plug-in webového testu.**

         Zobrazí se dialogové okno **Přidat modul plug-in Test webu.**

    2. V části **Vyberte modul plug-in**vyberte třídu zásuvných modulů test výkonu webu.

    3. V **podokně Vlastnosti vybraného modulu plug-in** nastavte počáteční hodnoty pro modul plug-in, které mají být používány za běhu.

        > [!NOTE]
        > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Vlastnosti modulu plug-in testu výkonu webu můžete také později upravit pomocí okna Vlastnosti.

    4. Vyberte **OK**.

9. Spusťte test výkonu webu.

     Příklad implementace aplikace <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>naleznete v [tématu How to: Create a web performance test plug-in](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postup: Použití rozhraní API zátěžového testu](../test/how-to-use-the-load-test-api.md)
- [Postup: Vytvoření modulu plug-in test výkonu webu](../test/how-to-create-a-web-performance-test-plug-in.md)
