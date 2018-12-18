---
title: Postup použití testu CTest jazyka C++
ms.date: 11/07/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 7a4475cba023f792c2ff96895eb4dd7e0b4ebcf5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050210"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Postup použití testu CTest jazyka C++ v sadě Visual Studio

CMake (která zahrnuje CTest) je integrována do integrovaného vývojového prostředí sady Visual Studio ve výchozím nastavení jako součást sady **Develoment Desktop s C++** pracovního vytížení. Pokud je potřeba nainstalovat na svém počítači, spusťte program Instalační program sady Visual Studio, klikněte na tlačítko **změnit** tlačítko a pak zkontrolujte [nástroje CMake pro Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) v seznamu součástí úlohy.

## <a name="to-write-tests"></a>K psaní testů

Podpora CMake v sadě Visual Studio nezahrnuje projektu systému Visual Studio. Proto zápisu a nakonfigurujte testy CTest, stejně jako v jakémkoli prostředí CMake. Další informace o používání CMake v sadě Visual Studio najdete v tématu [nástroje CMake pro Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Pro spouštění testů (Visual Studio 2017 verze 15.6)

V sadě Visual Studio 2017 verze 15.6 CTest je plně integrována s **Průzkumník testů** a podporuje také rozhraní testování částí Googlu a Boost. Tyto architektury jsou zahrnuté ve výchozím nastavení jako komponentu **Develoment Desktop s C++** pracovního vytížení. Nicméně pokud provádíte upgrade projektu ze starší verze sady Visual Studio, budete muset nainstalovat tyto architektury pomocí programu Instalační program sady Visual Studio.

Následující obrázek znázorňuje výsledky CTest spouštět pomocí rozhraní Google Test:

![CTest pomocí rozhraní Google Test v VS2017 verzi 15.6](media/ctest-test-explorer.png)

Pokud používáte CTest, ale ne Google nebo Boost adaptérů, uvidíte výsledky na úrovni CTest namísto jednotlivých testovací metoda úroveň. Můžete ladit a procházení po kroku jen CTest spustitelné soubory, ale trasování zásobníku na jednotlivé testy nejsou podporovány.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Pro spouštění testů (Visual Studio 2017 verze 15.5)

V **Visual Studio 2017 verze 15.5**, CTest není integrován s **Průzkumník testů**. Testy můžete spustit z hlavní nabídky CMake nebo v místní nabídce *CMakeLists.txt* ve **Průzkumníka řešení**. Výsledky testů jsou směrované na Visual Studio **okno výstup**.

![Testy CTest ve verzi 15.5 VS2017](media/cpp-cmake-run-tests.png)

## <a name="see-also"></a>Viz také:

[Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)