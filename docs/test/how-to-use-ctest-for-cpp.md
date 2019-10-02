---
title: Postup použití testu CTest jazyka C++
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: cc0ced6205444e1436ffbffa73ba647a6b682c5c
ms.sourcegitcommit: 628eb202a1153ebfe69c668f966f821b98b34b34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71720553"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Jak používat CTest pro C++ v aplikaci Visual Studio 2017 a novější

Cmake (která zahrnuje CTest) je integrovaná do integrovaného vývojového prostředí sady Visual Studio ve výchozím nastavení jako součást **vývoje C++ plochy s** úlohou. Pokud ho potřebujete nainstalovat na váš počítač, otevřete instalační program pro Visual Studio program, klikněte na tlačítko **vývoj plochy s C++**  tlačítkem a pak klikněte na tlačítko **Upravit**. V seznamu součástí úloh vyberte  **C++ nástroje cmake pro Windows** .

## <a name="to-write-tests"></a>K psaní testů

Podpora CMake v sadě Visual Studio nezahrnuje projektu systému Visual Studio. Proto zápisu a nakonfigurujte testy CTest, stejně jako v jakémkoli prostředí CMake. K povolení testování použijte příkaz `enable_testing()` a pomocí příkazu `add_test()` přidejte nový test. Další informace o CTest najdete v dokumentaci k [cmaki](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Další informace o použití CMake v sadě Visual Studio najdete v tématu [projekty cmake v sadě Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Spuštění testů

CTest je plně integrovaná s **průzkumníkem testů** a podporuje i rozhraní Google i zvýšení testovacích jednotek. Tyto architektury jsou ve výchozím nastavení zahrnuty jako komponenty v rámci **vývoje C++ desktopových** aplikací. Nicméně pokud provádíte upgrade projektu ze starší verze sady Visual Studio, budete muset nainstalovat tyto architektury pomocí programu Instalační program sady Visual Studio.

Následující obrázek znázorňuje výsledky CTest spouštět pomocí rozhraní Google Test:

![CTest s rozhraním Google Test Framework v aplikaci Visual Studio](media/ctest-test-explorer.png)

Pokud používáte CTest, ale ne Google nebo Boost adaptérů, uvidíte výsledky na úrovni CTest namísto jednotlivých testovací metoda úroveň. Můžete ladit a procházení po kroku jen CTest spustitelné soubory, ale trasování zásobníku na jednotlivé testy nejsou podporovány.

## <a name="see-also"></a>Viz také:

- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
