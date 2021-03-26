---
title: Příkazová tabulka sady Visual Studio (. Soubory vsct) | Microsoft Docs
description: Seznamte se s textovými soubory, které popisují sadu příkazů, které obsahuje VSPackage, v konfiguračních souborech tabulky příkazů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 305bf0e5463fd4e030f2ce3e9f7fa6eca99bfe20
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085738"
---
# <a name="visual-studio-command-table-vsct-files"></a>Soubory tabulek příkazů sady Visual Studio (.Vsct)
Konfigurační soubor tabulky příkazů je textový soubor, který popisuje sadu příkazů, které obsahuje VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kompilátor příkazového řádku (vsct) zkompiluje konfigurační soubory založené na jazyce XML (soubory. vsct) do binárního výstupního příkazu tabulky (. technický ředitel). Výsledné soubory. technický ředitel jsou stejné jako ty, které jsou vytvořeny pomocí kompilátoru příkazového řádku (CTC) ke kompilaci konfiguračních souborů. ctc. Soubory. vsct založené na jazyce XML však mají některé výhody, jako je editor XML a XML IntelliSense.

 Další informace o syntaxi a sémantikě souborů. vsct naleznete v tématu [design XML Command Table (. Soubory vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>V tomto oddílu
 [Návrh souborů tabulky příkazů XML (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Popisuje návrh souborů. vsct.

 [Postupy: Vytvoření souboru .Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Porovná metody pro vytvoření souboru. vsct. Popisuje proces ručního vytvoření nového souboru. vsct.

## <a name="related-sections"></a>Související oddíly
 [XML schéma VSCT – referenční informace](../../extensibility/vsct-xml-schema-reference.md)

 Poskytuje podrobnosti o jednotlivých oddílech konfiguračního souboru XML tabulky příkazů.

 [Konfigurace příkazového tabulky (. CTC)](/previous-versions/bb165153(v=vs.100)) představují Přehled nepoužívaného formátu souboru. ctc.

 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Popisuje specifikaci formátu tabulky příkazů.

 [Prostředky v balíčcích VSPackage](../../extensibility/internals/resources-in-vspackages.md)

 Popisuje způsob použití spravovaných a nespravovaných prostředků ve spravovaných VSPackage.

 [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)

 Vysvětluje, jak vytvořit uživatelské rozhraní, které obsahuje nabídky, panely nástrojů a pole se seznamem příkazů.