---
title: API testu výkonnosti webu
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594328"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Postupy: použití API testu výkonnosti webu

Můžete napsat kód pro testy výkonu webu. Test webového výkonu rozhraní API slouží k vytvoření kódované testy webového výkonu, webového výkonu test modulů plug-in, požadavek moduly plug-in, požadavky, pravidla pro extrakci a pravidel ověřování. Třídy, které tvoří tyto typy jsou základní třídy v tomto rozhraní API. Další typy v tomto rozhraní API se používá pro podporu vytváření <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>, a <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> objekty. Můžete použít <xref:Microsoft.VisualStudio.TestTools.WebTesting> obor názvů umožní vytvořit vlastní testy výkonnosti webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete také použít API výkonnostních testů webu prostřednictvím kódu programu vytvořit a uložit deklarativní webové testy výkonu. Chcete-li to provést, použijte <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> a <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer> třídy.

> [!TIP]
> Ke kontrole použijte prohlížeč objektů <xref:Microsoft.VisualStudio.TestTools.WebTesting> oboru názvů. Editory Visual C# i Visual Basic nabízí podporu technologie IntelliSense pro kódování s třídami v oboru názvů.

Můžete také vytvořit moduly plug-in pro zátěžové testy. Další informace najdete v tématu [postupy: použití rozhraní API zátěžového testu](../test/how-to-use-the-load-test-api.md) a [postupy: vytvoření modulu Plugin pro zátěžový test](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Používání oboru názvů WebTesting

1. Otevřete webový výkon a projekt zátěžového testu, který obsahuje test výkonnosti webu.

2. Přidejte Visual C# nebo Visual Basic projekt knihovny tříd pro vaše řešení pro testování.

3. Přidáte odkaz v projektu webového výkonu a zátěžový test do projektu knihovny tříd.

4. V projektu knihovny tříd přidejte odkaz na knihovnu DLL Microsoft.VisualStudio.QualityTools.WebTestFramework.

5. V souboru třídy, který se nachází v projektu knihovny tříd, přidejte `using` příkaz pro <xref:Microsoft.VisualStudio.TestTools.WebTesting> oboru názvů.

6. Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> rozhraní.

7. Sestavte projekt.

8. Přidáte nový test výkonnosti webu modulu plug-in pomocí editoru testu výkonnosti webu:

    1. Zvolte **přidat modul webového testu Plug-in** na panelu nástrojů.

         **Přidat modul webového testu Plug-in** se zobrazí dialogové okno.

    2. V části **vyberte modul plug-in**vyberte modul plug-in třídu testu výkonu webu.

    3. V **vlastnosti pro vybraný modul plug-in** podokno, nastavte počáteční hodnoty pro modul plug-in pro použití v době běhu.

        > [!NOTE]
        > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Modul plug-in vlastností testu výkonnosti webu můžete upravit i později pomocí okna Vlastnosti.

    4. Vyberte **OK**.

9. Spuštění testu výkonnosti webu.

     Pro příklad implementace <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, naleznete v tématu [postupy: vytvoření modulu Plugin pro test výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Vytvoření vlastního kódu a modulů Plugin pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: použití rozhraní API zátěžového testu](../test/how-to-use-the-load-test-api.md)
- [Postupy: vytvoření modulu Plugin pro test výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md)
