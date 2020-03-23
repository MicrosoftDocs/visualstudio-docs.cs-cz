---
title: Jak používat Google Test pro C++
description: Pomocí testu Google můžete ve Visual Studiu vytvořit testy jednotek jazyka C++.
ms.date: 05/06/2017
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 31078b060c94f3253232d22681a1a5dae47e03b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279304"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Použití testu Google pro C++ ve Visual Studiu

Ve Visual Studiu 2017 a novějších je Google Test integrován do integrovaného prostředí Visual Studio jako výchozí součást vývoje plochy s úlohami **C++.** Chcete-li ověřit, zda je nainstalována v počítači, otevřete Instalační službu sady Visual Studio a v seznamu součástí pracovního vytížení najděte Test Google:

![Instalace testu Google](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Přidání testovacího projektu Google ve Visual Studiu 2019

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na uzel řešení a zvolte **Přidat** > **nový projekt**.
2. Nastavte **jazyk** na **C++** a zadejte **test** do vyhledávacího pole. Ze seznamu výsledků zvolte **Testovací projekt Google**.
3. Pojmenujte testovací projekt a klepněte na tlačítko **OK**.

![Nový testovací projekt Google](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Přidání testovacího projektu Google ve Visual Studiu 2017

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na uzel řešení a zvolte **Přidat** > **nový projekt**.
2. V levém podokně zvolte **Visual C++** > **Test** a pak v prostředním podokně zvolte Testovací **projekt Google.**
3. Pojmenujte testovací projekt a klepněte na tlačítko **OK**.

![Nový testovací projekt Google](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Konfigurace testovacího projektu

V dialogovém okně **Testovat konfiguraci projektu,** které se zobrazí, můžete zvolit projekt, který chcete testovat. Když zvolíte projekt, Visual Studio přidá odkaz na vybraný projekt. Pokud zvolíte žádný projekt, budete muset ručně přidat odkazy na projekt (projekty), které chcete testovat. Při výběru mezi statickým a dynamickým propojením s binárními soubory Testu Google jsou důležité informace stejné jako u všech programů jazyka C++. Další informace naleznete [v tématu Knihovny DLL v jazyce Visual C++](/cpp/build/dlls-in-visual-cpp).

![Konfigurace testovacího projektu Google](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Nastavení dalších možností

V hlavní nabídce zvolte**Možnosti** >  **nástroje** > **Testovací adaptér pro Test Google** a nastavte další možnosti. Další informace o těchto nastaveních naleznete v dokumentaci k testu Google.

![Nastavení testovacího projektu Google](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Přidat direktivy zahrnutí

Do testovacího souboru *CPP* `#include` přidejte všechny potřebné direktivy, aby byly typy a funkce programu viditelné pro testovací kód. Program je obvykle v hierarchii složek o jednu úroveň vyšší. Pokud zadáte `#include "../"` okno Technologie IntelliSense, zobrazí se okno IntelliSense, které vám umožní vybrat úplnou cestu k souboru záhlaví.

![Přidání direktiv #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Zápis a spuštění testů

Nyní jste připraveni psát a spouštět testy Google. Informace o testovacích makru naleznete v [základním nátěru testu Google.](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) Informace o zjišťování, spouštění a seskupování testů pomocí **Průzkumníka testů**naleznete v tématu Spuštění testů částí pomocí [Průzkumníka testů](run-unit-tests-with-test-explorer.md) .

## <a name="see-also"></a>Viz také

[Zapsat testy částí pro C/C++](writing-unit-tests-for-c-cpp.md)
