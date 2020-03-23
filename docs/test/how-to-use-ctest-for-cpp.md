---
title: Jak používat CTest pro C++
ms.date: 01/23/2020
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 78759a017575916bce3b3fff643cbce8ff303fd6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76826520"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Použití CTest pro C++ ve Visual Studiu 2017 a novějším

CMake (který zahrnuje CTest) je integrován do IDE Sady Visual Studio ve výchozím nastavení jako součást vývoje plochy s úlohou **C++.** Pokud ji potřebujete nainstalovat do počítače, otevřete instalační program sady Visual Studio, klepněte na tlačítko **Vývoj plochy s c++** a potom klepněte na **tlačítko Změnit**. V seznamu součástí pracovního vytížení vyberte **nástroje C++ CMake pro Windows.**

## <a name="to-write-tests"></a>Psaní testů

Podpora CMake v sadě Visual Studio nezahrnuje systém projektu sady Visual Studio. Proto můžete psát a konfigurovat ctest testy stejně jako v jakémkoli prostředí CMake. Pomocí `enable_testing()` příkazu povolte testování `add_test()` `gtest_discover_tests()` a příkaz nebo přidejte nový test. Další informace o CTest, naleznete v [dokumentaci CMake](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Další informace o použití CMake v sadě Visual Studio najdete v tématu [CMake projekty v sadě Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Spuštění testů

CTest je plně integrován s **Průzkumníkem testů** a také podporuje rozhraní pro testování částí Google i Boost. Tyto architektury jsou zahrnuty ve výchozím nastavení jako součásti ve vývoji plochy s úlohou **C++.** Pokud však inovujete projekt ze starší verze sady Visual Studio, bude pravděpodobně nutné tyto architektury nainstalovat pomocí instalačního programu sady Visual Studio.

Následující obrázek znázorňuje výsledky spuštění CTestu pomocí rozhraní Google Test Framework:

![CTest s google testovací framework v sadě Visual Studio](media/ctest-test-explorer.png)

Pokud používáte CTest, ale ne Adaptéry Google nebo Boost, zobrazí se výsledky na úrovni CTest namísto úrovně individuální zkušební metody. Můžete ladit a krokovat ctest pouze spustitelné soubory, ale trasování zásobníku na jednotlivé testy nejsou podporovány.

## <a name="see-also"></a>Viz také

- [Zapsat testy částí pro C/C++](writing-unit-tests-for-c-cpp.md)
