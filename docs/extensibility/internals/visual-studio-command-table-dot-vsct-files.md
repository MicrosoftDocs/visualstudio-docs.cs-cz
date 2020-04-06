---
title: Visual Studio Příkaz tabulka (. Vsct) Soubory | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704029"
---
# <a name="visual-studio-command-table-vsct-files"></a>Soubory tabulek příkazů sady Visual Studio (.Vsct)
Konfigurační soubor tabulky příkazů je textový soubor, který popisuje sadu příkazů, které obsahuje VSPackage. Kompilátor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] příkazové tabulky (VSCT) zkompiluje konfigurační soubory založené na XML (.vsct files) do souborů s binárním výstupem příkazové tabulky (.cto). Výsledné soubory .cto jsou stejné jako ty, které jsou vytvořeny pomocí kompilátoru příkazové tabulky (CTC) ke kompilaci konfiguračních souborů CTC. Soubory V .vsct založené na jazyce XML však mají některé výhody, například editor XML a xml intellisense.

 Další informace o syntaxi a sémantice souborů .vsct naleznete v [tématu Návrh tabulky příkazů XML (. Vsct) Soubory](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>V tomto oddílu
 [Návrh souborů tabulky příkazů XML (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Popisuje, jak navrhnout soubory .vsct.

 [Postupy: Vytvoření souboru .Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Porovná metody pro vytvoření souboru .vsct. Popisuje proces ručního vytvoření nového souboru VSCT.

## <a name="related-sections"></a>Související oddíly
 [XML schéma VSCT – referenční informace](../../extensibility/vsct-xml-schema-reference.md)

 Obsahuje podrobnosti o jednotlivých oddílech konfiguračního souboru XML tabulky příkazů.

 [Konfigurace příkazové tabulky (. Ctc) Soubory](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c) Představuje přehled zastaralého formátu souboru CTC.

 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Popisuje specifikaci formátu tabulky příkazů.

 [Prostředky v balíčcích VSPackage](../../extensibility/internals/resources-in-vspackages.md)

 Popisuje použití spravovaných a nespravovaných prostředků ve spravovaných balíčcích VSPackages.

 [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)

 Vysvětluje, jak vytvořit nové prostředí, které obsahuje nabídky, panely nástrojů a pole se seznamem příkazů.
