---
title: Nastavení projektu VC + +, projekty a řešení, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef861d13387c013659e5e4c1714680b71896858c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657868"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Nastavení projektu VC++, projekty a řešení, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto dialogové okno umožňuje definovat [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] nastavení projektu související s protokolováním sestavení a podpůrnými typy souborů.

### <a name="to-access-this-dialog-box"></a>Přístup k tomuto dialogovému oknu

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. Vyberte **projekty a řešení**a pak vyberte **nastavení projektu VC + +**.

## <a name="build-customization-search-path"></a>Cesta pro vyhledávání vlastního nastavení sestavení
 Určuje seznam adresářů, které obsahují soubory. Rules, které vám pomůžou definovat pravidla sestavení pro vaše projekty.

## <a name="build-logging"></a>Protokolování sestavení
 **Ano** Zapne generování souboru protokolu sestavení. Tato možnost generuje BuildLog.htm, které lze najít v adresáři zprostředkujících souborů projektu. Každé nové sestavení přepíše předchozí soubor BuildLog.htm.

 **Ne** Vypne generování souboru protokolu sestavení.

## <a name="build-timing"></a>Časování sestavení
 **Ano** Zapne časování buildu. Pokud je tato možnost vybrána, bude čas potřebný k dokončení sestavení odeslán do okna výstup. Další informace najdete v tématu [okno výstup](../../ide/reference/output-window.md).

 **Ne** Vypne časování buildu.

## <a name="extensions-to-hide"></a>Rozšíření pro skrytí
 Určuje přípony názvů souborů, které se nezobrazí v **Průzkumník řešení** , když je povolená možnost **Zobrazit všechny soubory** .

## <a name="extensions-to-include"></a>Rozšíření, která mají být zahrnuta
 Určuje přípony názvů souborů, které lze přenést do projektu.

## <a name="maximum-concurrent-c-compilations"></a>Maximální počet souběžných kompilací v jazyce C++
 Určuje maximální počet jader procesoru, které se mají použít pro paralelní kompilaci C++.

## <a name="show-environment-in-log"></a>Zobrazit prostředí v protokolu
 **Ano** Zobrazí seznam proměnných prostředí v souboru protokolu sestavení. Tato možnost určuje, že se všechny proměnné prostředí během sestavení [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektů do souboru protokolu sestavení budou zobrazovat jako ozvěny.

 **Ne** Vyloučení proměnných prostředí ze souboru protokolu sestavení.

## <a name="solution-explorer-mode"></a>Průzkumník řešení režim
 **Zobrazit pouze soubory v projektu** Nakonfiguruje **Průzkumník řešení** jenom zobrazení souborů v projektu.

 **Zobrazit všechny soubory** Nakonfiguruje **Průzkumník řešení** k zobrazení souborů v projektu a souborů na disku ve složce projektu.

## <a name="see-also"></a>Viz také
 [Sestavení c/C++ programy](https://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008) c/C++ – [Referenční dokumentace sestavení](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
