---
title: Jak používat CTest pro C++
ms.date: 01/23/2020
ms.topic: how-to
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: c429c9e676ead54bb9f168e3220bf2d4791fac63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287230"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Jak používat CTest for C++ v aplikaci Visual Studio 2017 a novějších

CMake (která zahrnuje CTest) je integrovaná do integrovaného vývojového prostředí (IDE) sady Visual Studio ve výchozím nastavení jako součást **vývoje plochy pomocí úlohy C++** . Pokud ho potřebujete nainstalovat na váš počítač, otevřete Instalační program pro Visual Studio program, klikněte na tlačítko vývoj pro **stolní počítače pomocí C++** a pak klikněte na **Upravit**. V seznamu součástí úloh vyberte **nástroje C++ cmake Tools for Windows** .

## <a name="to-write-tests"></a>Zápis testů

Podpora CMake v sadě Visual Studio nezahrnuje projektový systém Visual Studio. Proto zapisujete a nakonfigurujete testy CTest stejně jako v jakémkoli prostředí CMake. Použijte `enable_testing()` příkaz pro povolení testování a `add_test()` `gtest_discover_tests()` příkaz nebo pro přidání nového testu. Další informace o CTest najdete v dokumentaci k [cmaki](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Další informace o použití CMake v sadě Visual Studio najdete v tématu [projekty cmake v sadě Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Spuštění testů

CTest je plně integrovaná s **průzkumníkem testů** a podporuje i rozhraní Google i zvýšení testovacích jednotek. Tyto architektury jsou ve výchozím nastavení zahrnuty jako komponenty ve **vývoji desktopových** aplikací v C++. Nicméně pokud upgradujete projekt ze starší verze sady Visual Studio, bude pravděpodobně nutné nainstalovat tyto architektury pomocí Instalační program pro Visual Studio programu.

Následující ilustrace znázorňuje výsledky spuštění CTest pomocí Google Test Framework:

![CTest s rozhraním Google Test Framework v aplikaci Visual Studio](media/ctest-test-explorer.png)

Pokud používáte CTest, ale ne pro adaptéry Google nebo zvyšte, zobrazí se výsledky na úrovni CTest namísto jednotlivé úrovně testovací metody. Můžete ladit a krokovat s CTest spustitelnými soubory, ale trasování zásobníku na jednotlivých testech nejsou podporována.

## <a name="see-also"></a>Viz také

- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
