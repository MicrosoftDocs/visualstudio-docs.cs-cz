---
title: Jak používat Google Test pro C++
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 704d842aaf3ea5e3075939e4d52b042a4128b810
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060388"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Jak používat Google Test pro C++ v sadě Visual Studio
V **Visual Studio 2017 verze 15.5** a později, Google Test je integrována do integrovaného vývojového prostředí sady Visual Studio jako součást výchozí **Desktop Development with C++** pracovního vytížení. Pokud chcete ověřit, jestli je nainstalovaný na počítači, otevřete instalační program sady Visual Studio a vyhledejte Google Test v seznamu součástí úlohy:

![Instalovat Google Test](media/cpp-google-component.png)

## <a name="add-a-google-test-project-to-the-solution"></a>Přidat do řešení projektu Google Test
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení a zvolte **přidat** > **nový projekt**.
2. V levém podokně vyberte **Visual C++** > **testovací** a klikněte na tlačítko **projektu Google Test** v prostředním podokně.
3. Pojmenujte testovací projekt a klikněte na tlačítko **OK**.

![Nového projektu Google Test](media/cpp-gtest-new-project.png)

## <a name="configure-the-test-project"></a>Konfigurace testovacího projektu
V **testovací konfigurace projektu** zobrazeném dialogovém okně můžete nastavit projekt, kterou potřebujete otestovat. Když vyberete projekt, Visual Studio přidá odkaz na vybraný projekt. Pokud se rozhodnete žádný projekt, je třeba ručně přidat odkazy na projekty, které chcete testovat. Při volbě mezi statickým a dynamickým propojení binárních souborů Google testu, jaké jsou požadavky jsou stejné jako u každého programu C++. Další informace najdete v tématu [knihovny DLL v jazyce Visual C++](/cpp/build/dlls-in-visual-cpp).

 ![Konfigurace projektu Google Test](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Nastavit další možnosti
V hlavní nabídce zvolte **nástroje** > **možnosti** > **testovací adaptér pro Google Test** můžete nastavit další možnosti. Viz dokumentace ke službě Google Test pro další informace o těchto nastaveních.

 ![Nastavení projektu Google Test](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Přidání direktiv
V testu *.cpp* přidejte všechny potřebné `#include` direktivy zviditelnit typy a funkce vaší aplikace k testovacímu kódu. Program je obvykle nahoru o jednu úroveň v hierarchii složek. Pokud zadáte `#include "../"` okno technologie IntelliSense se zobrazí a vám umožní vybrat úplná cesta k souboru hlaviček.

![Přidejte #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Psání a spouštění testů
Nyní jste připraveni pro zápis a spouštění testů Google. Najdete v článku [Úvod do Google Test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) informace o makra testu. Zobrazit [spouštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md) informace o zjišťování, spouštění a seskupení testů s použitím **Průzkumník testů**.

## <a name="see-also"></a>Viz také:
[Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
