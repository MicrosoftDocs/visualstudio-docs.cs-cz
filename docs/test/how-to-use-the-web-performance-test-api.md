---
title: Rozhraní API testu výkonnosti webu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d22c1962727d22af965c879de3ae5fea6d4e54af
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653301"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Postupy: použití rozhraní API testu výkonnosti webu

Můžete napsat kód pro testy výkonnosti webu. Rozhraní API testu výkonnosti webu slouží k vytváření programových testů výkonnosti webu, modulů plug-in testování výkonu webu, modulů plug-in požadavků, požadavků, pravidel pro extrakci a ověřovacích pravidel. Třídy, které tvoří tyto typy, jsou základní třídy v tomto rozhraní API. Další typy v tomto rozhraní API se používají k podpoře vytváření <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> a <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>ch objektů. Obor názvů <xref:Microsoft.VisualStudio.TestTools.WebTesting> slouží k vytváření přizpůsobených testů výkonnosti webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete také použít rozhraní API testu výkonnosti webu pro programové vytváření a ukládání deklarativních testů výkonnosti webu. K tomu použijte třídy <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> a <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer>.

> [!TIP]
> K prohlédnutí <xref:Microsoft.VisualStudio.TestTools.WebTesting> oboru názvů použijte prohlížeč objektů. Editory vizuálů C# i Visual Basic nabízejí podporu technologie IntelliSense pro kódování s třídami v oboru názvů.

Moduly plug-in lze vytvořit také pro zátěžové testy. Další informace naleznete v tématu [Postupy: použití rozhraní API zátěžového testu](../test/how-to-use-the-load-test-api.md) a [Postupy: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Použití oboru názvů webového testování

1. Otevřete projekt webového výkonu a zátěžového testu, který obsahuje test výkonnosti webu.

2. Přidejte do testovacího řešení projekt knihovny tříd Visual C# nebo Visual Basic.

3. Do projektu knihovny tříd přidejte odkaz v projektu testování výkonu webu a zátěžového testu.

4. Přidejte odkaz na knihovnu DLL Microsoft. VisualStudio. QualityTools. WebTestFramework v projektu knihovny tříd.

5. V souboru třídy, který je umístěn v projektu knihovny tříd, přidejte příkaz `using` pro obor názvů <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

6. Vytvořte třídu, která implementuje rozhraní <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

7. Sestavte projekt.

8. Přidejte nový modul plug-in testu výkonnosti webu pomocí Editor testu výkonnosti webu:

    1. Na panelu nástrojů vyberte možnost **Přidat modul plug-in webového testu** .

         Zobrazí se dialogové okno **Přidat modul plug-in webového testu** .

    2. V části **Vybrat modul plug-in**vyberte třídu modulu plug-in test výkonnosti webu.

    3. V podokně **vlastnosti pro vybraný modul plug-in** nastavte počáteční hodnoty pro modul plug-in, které se použijí v době běhu.

        > [!NOTE]
        > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Vlastnosti modulu plug-in testu výkonnosti webu lze také upravit později pomocí okno Vlastnosti.

    4. Klikněte na **tlačítko OK**.

9. Spusťte test výkonnosti webu.

     Příklad implementace <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> naleznete v tématu [How to: Create a test Performance test](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Vytvoření vlastního kódu a modulů plug-in pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: použití rozhraní API zátěžového testu](../test/how-to-use-the-load-test-api.md)
- [Postupy: Vytvoření modulu plug-in testu výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md)