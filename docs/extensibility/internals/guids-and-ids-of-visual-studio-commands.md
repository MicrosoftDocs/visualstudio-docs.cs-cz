---
title: Identifikátory GUID a ID příkazů sady Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7670eacc875bf7c5437d9bb92cc1932753093bd
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186637"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identifikátory GUID a ID příkazů sady Visual Studio
Hodnoty identifikátoru GUID a ID příkazů zahrnutých v integrovaném vývojovém prostředí (IDE) sady Visual Studio jsou definovány v souborech. vsct, které jsou nainstalovány jako součást sady Visual Studio SDK. Další informace naleznete v tématu [příkazy, nabídky a skupiny definované rozhraním IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Další informace o tom, jak pracovat s objekty IDE, které jsou definovány v souborech *. vsct* , naleznete v tématu [extend menu and Commands](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Najít definici příkazu
 Vzhledem k tomu, že Visual Studio definuje více než 1000 příkazů, je nepraktické je uvést zde. Místo toho použijte následující postup k vyhledání definice příkazu.

### <a name="to-locate-a-command-definition"></a>Vyhledání definice příkazu

1. V sadě Visual Studio otevřete následující soubory v *instalační cestě sady Visual studio <\>\\\VisualStudioIntegration\Common\Inc* složka: *SharedCmdDef. vsct*, *ShellCmdDef. vsct*, *VsDbgCmdUsed. vsct*, *Venusmenu. vsct*.

    Většina příkazů sady Visual Studio je definována v *SharedCmdDef. vsct* a *ShellCmdDef. vsct*. *VsDbgCmdUsed. vsct* definuje příkazy, které se vztahují k ladicímu programu, a *Venusmenu. vsct* definuje příkazy, které jsou specifické pro vývoj na webu.

2. Pokud je příkaz položkou nabídky, poznamenejte si přesný text položky nabídky. Pokud se jedná o tlačítko na panelu nástrojů, poznamenejte si text popisku, který se zobrazí při pozastavení.

3. Stisknutím **kombinace kláves Ctrl**+**F** otevřete dialogové okno **Najít** .

4. Do pole **Najít** zadejte text, který jste si poznamenali v kroku 2.

5. Ověřte, že se v poli **Hledat v** zobrazí **všechny otevřené dokumenty** .

6. Klikněte na tlačítko **Najít další** , dokud se text nevybere v části `<Strings>` [elementu Button](../../extensibility/button-element.md).

    Element `<Button>`, ve kterém se nachází příkaz, je definice příkazu.

   Po nalezení definice příkazu můžete umístit kopii příkazu do jiné nabídky nebo panelu nástrojů vytvořením [prvku CommandPlacement](../../extensibility/commandplacement-element.md) , který má stejné `guid` a `id` hodnoty jako příkaz. Další informace najdete v tématu [vytvoření opakovaně použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Zvláštní případy
 V následujících případech se text v nabídce nebo text popisku nemusí přesně shodovat s tím, co je v definici příkazu.

- Položky nabídky, které obsahují podtržený znak, jako je například příkaz **Tisk** v nabídce **soubor** , ve kterém je podtržena *P* .

     Znaky, které jsou uvozeny znakem ampersand (&) v názvu položky nabídky, jsou zobrazeny podtrženě. Soubory *. vsct* jsou však napsány v jazyce XML, který používá znak ampersand (&) k označení speciálních znaků a vyžaduje, aby byl znak ampersand zobrazen jako *&amp;amp;* . Proto se v souboru *. vsct* zobrazí příkaz **Tisk** jako *&amp;amp; Tisk*.

- Příkazy, které mají dynamický text, jako je například **Save** \<Current filename\>a dynamicky generované položky nabídky, jako například položky v seznamu **Poslední soubory** .

     Neexistuje spolehlivý způsob, jak prohledávat dynamický text. Místo toho vyhledejte skupinu, která je hostitelem požadovaného příkazu, pomocí konzultačních [identifikátorů GUID a ID nabídek](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) nebo [identifikátorů GUID](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)sady Visual Studio a vyhledejte ID této skupiny. Pokud definice příkazu nemá skupinu jako svůj [nadřazený element](../../extensibility/parent-element.md), vyhledejte *SharedCmdPlace. vsct* a *ShellCmdPlace. vsct* (nebo *VsDbgCmdPlace. vsct* pro příkazy ladicího programu) pro `<CommandPlacement>` element, který nastaví nadřazený prvek systému. *SharedCmdPlace. vsct*, *ShellCmdPlace. vsct*a *VsDbgCmdPlace. vsct* jsou v *\<cestě k instalaci sady Visual Studio SDK\>\VisualStudioIntegration\Common\Inc\\* složce.

## <a name="see-also"></a>Viz také:

- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referenční dokumentace schématu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)
