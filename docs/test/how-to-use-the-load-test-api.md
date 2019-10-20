---
title: Rozhraní API zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 571abf14b1e17d85e21667c0ef0dbc3894b3ae76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653320"
---
# <a name="how-to-use-the-load-test-api"></a>Postupy: použití rozhraní API zátěžového testu

Visual Studio podporuje moduly plug-in zátěžového testu, které mohou řídit nebo zdokonalit zátěžový test. Moduly plug-in zátěžového testu jsou uživatelsky definované třídy, které implementují rozhraní <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> nacházející se v oboru názvů <xref:Microsoft.VisualStudio.TestTools.LoadTesting>. Moduly plug-in zátěžového testu umožňují vlastní ovládací prvek zátěžového testu, jako je například přerušení zátěžového testu při splnění čítače nebo prahové hodnoty chyby. Použijte vlastnosti třídy <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> pro získání nebo nastavení parametrů zátěžového testu z uživatelsky definovaného kódu. Pro připojení delegátů k oznámením, když je spuštěn zátěžový test, použijte události třídy <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest>.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> K prohlédnutí <xref:Microsoft.VisualStudio.TestTools.LoadTesting> oboru názvů použijte prohlížeč objektů. Editory vizuálů C# i Visual Basic nabízejí podporu technologie IntelliSense pro kódování s třídami v oboru názvů.

Můžete také vytvořit moduly plug-in pro testy výkonnosti webu. Další informace najdete v tématu [Postupy: Vytvoření modulu plug-in testu výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md) a [Postup: Vytvoření modulu plug-in na úrovni požadavků](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Použití oboru názvů LoadTesting

1. Otevřete projekt webového výkonu a zátěžového testu, který obsahuje zátěžový test.

2. Přidejte do testovacího řešení projekt knihovny tříd Visual C# nebo Visual Basic.

3. Do projektu knihovny tříd přidejte odkaz v projektu testování výkonu webu a zátěžového testu.

4. Přidejte odkaz na knihovnu DLL Microsoft. VisualStudio. QualityTools. LoadTestFramework v projektu knihovny tříd.

5. V souboru třídy, který se nachází v projektu knihovny tříd, přidejte příkaz `using` pro obor názvů <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

6. Vytvořte veřejnou třídu, která implementuje rozhraní <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

7. Sestavte projekt.

8. Přidejte nový modul plug-in zátěžového testu pomocí Editor zátěžového testu:

    1. Klikněte pravým tlačítkem na kořenový uzel zátěžového testu a pak zvolte **Přidat modul plug-in zátěžového testu**.

    2. Zobrazí se dialogové okno **Přidat modul plug-in zátěžového testu** .

    3. V podokně **vlastnosti pro vybraný modul plug-in** nastavte počáteční hodnoty pro modul plug-in, které se použijí v době běhu.

        > [!NOTE]
        > Z modulů plug-in můžete vystavit tolik vlastností, kolik jich potřebujete. Stačí je nastavit jako veřejné, nastavitelné a základního typu, jako je například Integer, Boolean nebo String. Vlastnosti modulu plug-in zátěžového testu můžete také upravit později pomocí okna **vlastnosti** .

9. Spusťte zátěžový test.

     Implementaci <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> naleznete v tématu [How to: Create a Test Load-in](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Vytvoření vlastního kódu a modulů plug-in pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: použití rozhraní API testu výkonnosti webu](../test/how-to-use-the-web-performance-test-api.md)
- [Postupy: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md)