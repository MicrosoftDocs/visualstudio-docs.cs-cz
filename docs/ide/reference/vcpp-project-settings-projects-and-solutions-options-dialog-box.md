---
title: Možnosti nastavení projektu jazyka C++
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: c7acd0d8f9c6d15f9f20c42f59c3bd5562884ac3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68918889"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Nastavení projektu VC++, projekty a řešení, dialogové okno Možnosti

Toto dialogové okno umožňuje definovat nastavení sestavení a projektu jazyka C++ související s protokolováním, výkonem a podpůrnými typy souborů.

## <a name="to-access-this-dialog-box"></a>Přístup k tomuto dialogovému oknu

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. Vyberte **Projekty a řešení**a pak vyberte **Nastavení projektu VC++**.

## <a name="build-logging"></a>Protokolování sestavení

 **Ano**

  Zapne generování souboru protokolu sestavení. Tato možnost generuje Soubor BuildLog.htm, který lze nalézt v adresáři zprostředkujících souborů projektu. Každé čerstvé sestavení přepíše předchozí soubor BuildLog.htm.

 **Ne**

  Vypne generování souboru protokolu sestavení.

## <a name="show-environment-in-log"></a>Zobrazit prostředí v protokolu

 **Ano**

Zobrazí seznam proměnných prostředí v souboru protokolu sestavení. Tato možnost určuje echo všechny proměnné prostředí, během sestavení projektů Jazyka C++ do souboru protokolu sestavení.

 **Ne**

Vyloučit proměnné prostředí ze souboru protokolu sestavení.

## <a name="build-timing"></a>Časování sestavení

 **Ano**

  Zapne časování sestavení. Pokud je tato možnost vybrána, čas potřebný k dokončení sestavení je zaúčtován do okna Výstup. Další informace naleznete v [tématu Output Window](../../ide/reference/output-window.md).

 **Ne**

Vypne časování sestavení.

## <a name="maximum-concurrent-c-compilations"></a>Maximální počet souběžných kompilací jazyka C++

Určuje maximální počet jader procesoru, které mají být používány pro paralelní kompilaci jazyka C++.

## <a name="extensions-to-include"></a>Rozšíření, která mají být zahrnuta

Určuje přípony názvů souborů, které lze přenést do projektu.

## <a name="extensions-to-hide"></a>Rozšíření ke skrytí

Určuje přípony názvů souborů, které se nebudou zobrazovat v **Průzkumníku řešení,** pokud je povoleno **zobrazit všechny soubory.**

## <a name="build-customization-search-path"></a>Cesta hledání vlastního nastavení sestavení

Určuje seznam adresářů, které obsahují soubory pravidel, které vám pomohou definovat pravidla sestavení pro vaše projekty.

## <a name="solution-explorer-mode"></a>Režim Průzkumníka řešení

**Zobrazit pouze soubory v projektu**

Nakonfiguruje **Průzkumníka řešení** tak, aby zobrazoval pouze soubory v projektu.

**Zobrazit všechny soubory**

Nakonfiguruje **Průzkumníka řešení** tak, aby zobrazoval soubory v projektu a soubory na disku ve složce projektu.

## <a name="enable-project-caching"></a>Povolení ukládání do mezipaměti projektu

**Ano**

Umožňuje visual studio ukládat data projektu tak, aby při příštím otevření projektu, může načíst data uložená v mezipaměti, nikoli recomputing z souborů projektu. Použití dat uložených v mezipaměti může výrazně urychlit dobu načítání projektu.

**Ne**

Nepoužívejte data projektu uložená v mezipaměti. Analyzovat soubory projektu při každém načtení projektu.

## <a name="see-also"></a>Viz také

- [Sestavování programů v jazyku C/C++](/cpp/build/projects-and-build-systems-cpp)
- [Odkaz sestavení C/C++](/cpp/build/reference/c-cpp-building-reference)