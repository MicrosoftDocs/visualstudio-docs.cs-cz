---
title: Rozhraní API zátěžového testu
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1fc3ff1aa238249f7425c61b5b28d2a96e299fec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287100"
---
# <a name="how-to-use-the-load-test-api"></a>Postupy: použití rozhraní API zátěžového testu

Visual Studio podporuje moduly plug-in zátěžového testu, které mohou řídit nebo zdokonalit zátěžový test. Moduly plug-in zátěžového testu jsou uživatelsky definované třídy, které implementují rozhraní, které se <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> nachází v <xref:Microsoft.VisualStudio.TestTools.LoadTesting> oboru názvů. Moduly plug-in zátěžového testu umožňují vlastní ovládací prvek zátěžového testu, jako je například přerušení zátěžového testu při splnění čítače nebo prahové hodnoty chyby. Použijte vlastnosti <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> třídy pro získání nebo nastavení parametrů zátěžového testu z kódu definovaného uživatelem. Použijte události pro <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> třídu k připojení delegátů k oznámením, když je spuštěn zátěžový test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> K prohlédnutí oboru názvů použijte prohlížeč objektů <xref:Microsoft.VisualStudio.TestTools.LoadTesting> . Editory jazyka Visual C# i Visual Basic nabízejí podporu technologie IntelliSense pro kódování s třídami v oboru názvů.

Můžete také vytvořit moduly plug-in pro testy výkonnosti webu. Další informace najdete v tématu [Postupy: Vytvoření modulu plug-in testu výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md) a [Postup: Vytvoření modulu plug-in na úrovni požadavků](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Použití oboru názvů LoadTesting

1. Otevřete projekt webového výkonu a zátěžového testu, který obsahuje zátěžový test.

2. Do testovacího řešení přidejte projekt knihovny tříd Visual C# nebo Visual Basic.

3. Do projektu knihovny tříd přidejte odkaz v projektu testování výkonu webu a zátěžového testu.

4. Přidejte odkaz na knihovnu DLL Microsoft. VisualStudio. QualityTools. LoadTestFramework v projektu knihovny tříd.

5. V souboru třídy, který se nachází v projektu knihovny tříd, přidejte `using` příkaz pro <xref:Microsoft.VisualStudio.TestTools.LoadTesting> obor názvů.

6. Vytvořte veřejnou třídu, která implementuje <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> rozhraní.

7. Sestavte projekt.

8. Přidejte nový modul plug-in zátěžového testu pomocí Editor zátěžového testu:

    1. Klikněte pravým tlačítkem na kořenový uzel zátěžového testu a pak zvolte **Přidat modul plug-in zátěžového testu**.

    2. Zobrazí se dialogové okno **Přidat modul plug-in zátěžového testu** .

    3. V podokně **vlastnosti pro vybraný modul plug-in** nastavte počáteční hodnoty pro modul plug-in, které se použijí v době běhu.

        > [!NOTE]
        > Z modulů plug-in můžete vystavit tolik vlastností, kolik jich potřebujete. Stačí je nastavit jako veřejné, nastavitelné a základního typu, jako je například Integer, Boolean nebo String. Vlastnosti modulu plug-in zátěžového testu můžete také upravit později pomocí okna **vlastnosti** .

9. Spusťte zátěžový test.

     Implementaci nástroje naleznete <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> v tématu [How to: Create a Test Load-in](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: použití rozhraní API testu výkonnosti webu](../test/how-to-use-the-web-performance-test-api.md)
- [Postupy: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md)
