---
title: Jak používat Google Test pro C++
description: Použijte Google Test k vytvoření C++ testování částí v aplikaci Visual Studio.
ms.date: 05/06/2017
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 31078b060c94f3253232d22681a1a5dae47e03b6
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279304"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Jak používat Google Test pro C++ v sadě Visual Studio

V aplikaci Visual Studio 2017 a novějších jsou Google test integrovány do integrovaného vývojového prostředí sady Visual Studio jako výchozí součást  **C++ vývoje desktopových** aplikací. Pokud chcete ověřit, jestli je nainstalovaný na počítači, otevřete instalační program sady Visual Studio a vyhledejte Google Test v seznamu součástí úlohy:

![Instalovat Google Test](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Přidání projektu Google Test v aplikaci Visual Studio 2019

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení a vyberte **Přidat** > **Nový projekt**.
2. Do **vyhledávacího pole nastavte text** na **C++** a zadejte **test** . V seznamu výsledků vyberte možnost **Google test projekt**.
3. Zadejte název testovacího projektu a klikněte na tlačítko **OK**.

![Nového projektu Google Test](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Přidání projektu Google Test v aplikaci Visual Studio 2017

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení a vyberte **Přidat** > **Nový projekt**.
2. V levém podokně zvolte možnost **Visual C++**  > **test** a potom v prostředním podokně vyberte možnost **Google test projekt** .
3. Zadejte název testovacího projektu a klikněte na tlačítko **OK**.

![Nového projektu Google Test](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Konfigurace testovacího projektu

V dialogovém okně **konfigurace projektu testu** , které se zobrazí, můžete zvolit projekt, který chcete otestovat. Když vyberete projekt, Visual Studio přidá odkaz na vybraný projekt. Pokud se rozhodnete žádný projekt, je třeba ručně přidat odkazy na projekty, které chcete testovat. Při volbě mezi statickým a dynamickým propojení binárních souborů Google testu, jaké jsou požadavky jsou stejné jako u každého programu C++. Další informace naleznete v tématu [knihovny DLL v C++jazyce Visual ](/cpp/build/dlls-in-visual-cpp).

![Konfigurace projektu Google Test](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Nastavit další možnosti

V hlavní nabídce vyberte **nástroje** > **Možnosti** > **testovací adaptér pro Google test** pro nastavení dalších možností. Viz dokumentace ke službě Google Test pro další informace o těchto nastaveních.

![Nastavení projektu Google Test](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Přidání direktiv

V souboru Test *. cpp* přidejte všechny potřebné `#include` direktivy, aby byly typy a funkce programu viditelné pro testovací kód. Program je obvykle nahoru o jednu úroveň v hierarchii složek. Pokud zadáte `#include "../"` zobrazí se okno IntelliSense, které vám umožní vybrat úplnou cestu k souboru hlaviček.

![Přidejte #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Psání a spouštění testů

Nyní jste připraveni pro zápis a spouštění testů Google. Informace o testovacích makrech najdete v části [Google test Úvod](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) . Informace o zjišťování, spouštění a seskupování testů pomocí **Průzkumníka testů**naleznete v tématu [spuštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md) .

## <a name="see-also"></a>Viz také

[Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
