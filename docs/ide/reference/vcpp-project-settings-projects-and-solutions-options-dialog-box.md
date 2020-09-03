---
title: Možnosti nastavení projektu C++
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68918889"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Nastavení projektu VC++, projekty a řešení, dialogové okno Možnosti

Toto dialogové okno umožňuje definovat sestavení C++ a nastavení projektu související s protokolováním, výkonem a podpůrnými typy souborů.

## <a name="to-access-this-dialog-box"></a>Přístup k tomuto dialogovému oknu

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. Vyberte **projekty a řešení**a pak vyberte **nastavení projektu VC + +**.

## <a name="build-logging"></a>Protokolování sestavení

 **Ano**

  Zapne generování souboru protokolu sestavení. Tato možnost generuje BuildLog.htm, které lze najít v adresáři zprostředkujících souborů projektu. Každé nové sestavení přepíše předchozí soubor BuildLog.htm.

 **Ne**

  Vypne generování souboru protokolu sestavení.

## <a name="show-environment-in-log"></a>Zobrazit prostředí v protokolu

 **Ano**

Zobrazí seznam proměnných prostředí v souboru protokolu sestavení. Tato možnost určuje, že se všechny proměnné prostředí během sestavení projektů jazyka C++ budou zobrazovat do souboru protokolu sestavení.

 **Ne**

Vyloučení proměnných prostředí ze souboru protokolu sestavení.

## <a name="build-timing"></a>Časování sestavení

 **Ano**

  Zapne časování buildu. Pokud je tato možnost vybrána, bude čas potřebný k dokončení sestavení odeslán do okna výstup. Další informace najdete v tématu [okno výstup](../../ide/reference/output-window.md).

 **Ne**

Vypne časování buildu.

## <a name="maximum-concurrent-c-compilations"></a>Maximální počet souběžných kompilací v jazyce C++

Určuje maximální počet jader procesoru, které se mají použít pro paralelní kompilaci C++.

## <a name="extensions-to-include"></a>Rozšíření, která mají být zahrnuta

Určuje přípony názvů souborů, které lze přenést do projektu.

## <a name="extensions-to-hide"></a>Rozšíření pro skrytí

Určuje přípony názvů souborů, které se nezobrazí v **Průzkumník řešení** , když je povolená možnost **Zobrazit všechny soubory** .

## <a name="build-customization-search-path"></a>Cesta pro vyhledávání vlastního nastavení sestavení

Určuje seznam adresářů, které obsahují soubory. Rules, které vám pomůžou definovat pravidla sestavení pro vaše projekty.

## <a name="solution-explorer-mode"></a>Průzkumník řešení režim

**Zobrazit pouze soubory v projektu**

Nakonfiguruje **Průzkumník řešení** jenom zobrazení souborů v projektu.

**Zobrazit všechny soubory**

Nakonfiguruje **Průzkumník řešení** k zobrazení souborů v projektu a souborů na disku ve složce projektu.

## <a name="enable-project-caching"></a>Povolit ukládání projektů do mezipaměti

**Ano**

Umožňuje aplikaci Visual Studio ukládat data projektu do mezipaměti, aby při příštím otevření projektu mohla tato data načíst z mezipaměti, nikoli ze souborů projektu. Použití dat uložených v mezipaměti může výrazně zrychlit dobu načítání projektu.

**Ne**

Nepoužívejte data projektu v mezipaměti. Analyzujte soubory projektu pokaždé, když se projekt načte.

## <a name="see-also"></a>Viz také

- [Sestavování programů v jazyku C/C++](/cpp/build/projects-and-build-systems-cpp)
- [Odkaz sestavení C/C++](/cpp/build/reference/c-cpp-building-reference)