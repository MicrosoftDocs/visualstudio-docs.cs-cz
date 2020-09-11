---
title: Příkazová tabulka sady Visual Studio (. Soubory vsct) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 24ebac7aee2294d2ad8cee06cd88102bb8d3fd78
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012344"
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