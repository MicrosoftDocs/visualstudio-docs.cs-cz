---
title: Rozhraní API zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3d949b8c73bb155b2e6fe4900c54c6d5314d26c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588808"
---
# <a name="how-to-use-the-load-test-api"></a>Postup: Použití rozhraní API zátěžového testu

Visual Studio podporuje moduly plug-in zátěžového testu, které můžou řídit nebo vylepšit zátěžový test. Moduly plug-in zátěžového testu jsou <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> uživatelem <xref:Microsoft.VisualStudio.TestTools.LoadTesting> definované třídy, které implementují rozhraní nalezené v oboru názvů. Moduly plug-in zátěžového testu umožňují vlastní ovládací prvek zátěžového testu, například přerušení zátěžového testu při splnění prahu čítače nebo chyby. Pomocí vlastností <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> třídy můžete získat nebo nastavit parametry zátěžového testu z uživatelem definovaného kódu. Pomocí událostí ve <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> třídě připojit delegáty pro oznámení při spuštění zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Pomocí prohlížeče objektů zkontrolujte <xref:Microsoft.VisualStudio.TestTools.LoadTesting> obor názvů. Editory Visual C# i Visual Basic nabízejí podporu technologie IntelliSense pro kódování s třídami v oboru názvů.

Můžete také vytvořit moduly plug-in pro testy výkonu webu. Další informace naleznete v [tématu Postup: Vytvoření modulu plug-in test výkonu webu](../test/how-to-create-a-web-performance-test-plug-in.md) a [Postup: Vytvoření modulu plug-in na úrovni požadavku](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Použití oboru názvů LoadTesting

1. Otevřete webový výkon a zatížení testovací projekt, který obsahuje zátěžový test.

2. Přidejte do testovacího řešení projekt knihovny tříd visual c# nebo visual basic.

3. Přidejte odkaz ve webovém výkonu a projektu zátěžového testu do projektu knihovny tříd.

4. Přidejte odkaz na knihovnu DLL Microsoft.VisualStudio.QualityTools.LoadTestFramework v projektu Knihovny tříd.

5. V souboru třídy umístěném v `using` projektu knihovny tříd přidejte příkaz pro obor <xref:Microsoft.VisualStudio.TestTools.LoadTesting> názvů.

6. Vytvořte veřejnou třídu, která implementuje <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> rozhraní.

7. Sestavte projekt.

8. Přidejte nový zásuvný modul zátěžového testu pomocí Editoru zátěžového testu:

    1. Klepněte pravým tlačítkem myši na kořenový uzel zátěžového testu a pak zvolte **Přidat modul plug-in zátěžového testu**.

    2. Zobrazí se dialogové okno **Přidat zatěžovací test plug-in.**

    3. V **podokně Vlastnosti vybraného modulu plug-in** nastavte počáteční hodnoty pro modul plug-in, které mají být používány za běhu.

        > [!NOTE]
        > Můžete vystavit tolik vlastností, kolik chcete z modulů plug-in. Stačí, aby byly veřejné, nastavitelné a základního typu, jako je například Integer, Boolean nebo String. Vlastnosti modulu plug-in zátěžového testu můžete také později upravit pomocí okna **Vlastnosti.**

9. Spusťte zátěžový test.

     Implementace aplikace <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>naleznete v [tématu How to: Create a load test plug-in](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postup: Použití rozhraní API pro testování výkonu webu](../test/how-to-use-the-web-performance-test-api.md)
- [Postup: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md)
