---
title: Jak používat Google Test pro C++
description: Použijte Google Test k vytvoření testů jednotek C++ v aplikaci Visual Studio.
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: bf4db1c01fc79d32f7e498c265b74dec34f67e48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287243"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Použití Google Test pro jazyk C++ v aplikaci Visual Studio

V aplikaci Visual Studio 2017 a novějších jsou Google Test integrovány do integrovaného vývojového prostředí (IDE) sady Visual Studio jako výchozí součást **vývoje desktopových aplikací v jazyce C++** . Pokud chcete ověřit, že je na vašem počítači nainstalovaný, otevřete Instalační program pro Visual Studio a vyhledejte Google Test v seznamu součástí úlohy:

![Nainstalovat Google Test](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Přidání projektu Google Test v aplikaci Visual Studio 2019

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení a vyberte možnost **Přidat** > **Nový projekt**.
2. Do vyhledávacího pole nastavte **jazyk** na **C++** a zadejte **test** . V seznamu výsledků vyberte možnost **Google test projekt**.
3. Zadejte název testovacího projektu a klikněte na tlačítko **OK**.

![Nový Google Test projekt](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Přidání projektu Google Test v aplikaci Visual Studio 2017

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení a vyberte možnost **Přidat** > **Nový projekt**.
2. V levém podokně zvolte **Visual C++** > **test** a pak zvolte **Google test projekt** v prostředním podokně.
3. Zadejte název testovacího projektu a klikněte na tlačítko **OK**.

![Nový Google Test projekt](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Konfigurace testovacího projektu

V dialogovém okně **konfigurace projektu testu** , které se zobrazí, můžete zvolit projekt, který chcete otestovat. Když vyberete projekt, Visual Studio přidá odkaz na vybraný projekt. Pokud nezvolili žádný projekt, musíte ručně přidat odkazy na projekt, který chcete testovat. Při volbě statického a dynamického propojení s Google Test binárními soubory jsou požadavky stejné jako u jakéhokoli programu v jazyce C++. Další informace najdete v tématu [knihovny DLL v Visual C++](/cpp/build/dlls-in-visual-cpp).

![Nakonfigurovat Google Test projekt](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Nastavit další možnosti

V hlavní nabídce vyberte možnosti **nástrojů**  >  **Options**  >  **testovací adaptér pro Google test** a nastavte další možnosti. Další informace o těchto nastaveních najdete v dokumentaci k Google Test.

![Nastavení projektu Google Test](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Přidat direktivy include

V souboru Test *. cpp* přidejte všechny potřebné `#include` direktivy, aby byly typy a funkce programu viditelné pro testovací kód. Obvykle je program o jednu úroveň v hierarchii složek. Pokud zadáte `#include "../"` okno IntelliSense, budete moci vybrat úplnou cestu k souboru hlaviček.

![Přidat direktivy #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Zápis a spouštění testů

Nyní jste připraveni zapsat a spustit testy Google. Informace o testovacích makrech najdete v části [Google test Úvod](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) . Informace o zjišťování, spouštění a seskupování testů pomocí **Průzkumníka testů**naleznete v tématu [spuštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md) .

## <a name="see-also"></a>Viz také

[Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
