---
title: Identifikátory GUID a ID příkazů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e263678cca7e85993fefd01866352cafc83a74c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53047652"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identifikátory GUID a ID příkazů sady Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hodnoty GUID a ID příkazů součástí integrovaného vývojového prostředí (IDE) sady Visual Studio jsou definovány v souborech .vsct, které se instalují jako součást sady Visual Studio SDK. Další informace najdete v tématu [IDE-Defined příkazy, nabídky a skupiny](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Další informace o tom, jak pracovat s objekty integrovaného vývojového prostředí, které jsou definovány v souborech .vsct najdete v tématu [rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

## <a name="finding-a-command-definition"></a>Vyhledání definice příkazu
 Visual Studio definuje tisíc více než příkazy, proto je nepraktické uvádět na seznamu všechny zde. Místo toho použijte následující postup najděte definici příkazu.

#### <a name="to-locate-a-command-definition"></a>Vyhledejte definici příkazu

1. V sadě Visual Studio, otevřete následující soubory v seznamu *cestu instalace sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc\ složky: SharedCmdDef.vsct ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.

    Většina příkazů sady Visual Studio jsou definovány v SharedCmdDef.vsct a ShellCmdDef.vsct. VsDbgCmdUsed.vsct definuje příkazy, které se vztahují k ladicímu programu a Venusmenu.vsct definuje příkazy, které jsou specifické pro vývoj pro Web.

2. Pokud je příkaz položku nabídky, mějte na paměti přesný text položky nabídky. Pokud je příkaz tlačítka na panelu nástrojů, mějte na paměti text popisku, který se zobrazí při pozastavení na něj.

3. Stisknutím kláves CTRL + F otevřete **najít** dialogové okno.

4. V **najít** zadejte text, který jste si poznamenali v kroku 2.

5. Ověřte, že **všechny otevřené dokumenty** se zobrazí **Hledat v** pole.

6. Klikněte na tlačítko **najít další** tlačítko opakovaným text `<Strings>` část [Element přepínače](../../extensibility/button-element.md).

    `<Button>` Element, který se zobrazí v příkazu je příkaz definice.

   Po nalezení definici příkazu můžete umístit kopii tohoto příkazu na jinou nabídku nebo panel nástrojů tak, že vytvoříte [commandplacement – Element](../../extensibility/commandplacement-element.md) , který má stejný `guid` a `id` hodnoty jako u příkazu. Další informace najdete v tématu [vytvoření opakovaně použitelného skupiny z tlačítka](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Zvláštní případy
 V následujících případech text nabídky nebo text popisku nemusí přesně odpovídat co je v definici příkazu.

-   Položky nabídky, které obsahují podrženého znaku, například **tisk** příkaz **souboru** nabídka, ve které je podtrženo P.

     Znaky, které předchází znak '&' v názvech položek nabídky se zobrazí jako podtržené. Ale .vsct soubory jsou zapsány ve formátu XML, který používá znak 'a' označuje speciální znaky a vyžaduje, že musí být zadán znak, který je zobrazený jako&amp;". Proto se v souboru .vsct **tisk** příkazu se zobrazí jako "&amp;tisk".

-   Příkazy, které mají dynamický text, například **Uložit** *aktuální Filename*a dynamicky generované položky nabídky, jako je například položky na **poslední soubory** seznamu.

     Neexistuje žádný spolehlivý způsob pro vyhledávání na dynamický text. Místo toho najít skupinu, který je hostitelem požadovaného příkazu v součinnosti s [identifikátory GUID a ID sady Visual Studio nabídky](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) nebo [identifikátory GUID a ID sady Visual Studio panely nástrojů](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)a vyhledat ID této skupiny. Pokud definice příkazu nemá žádné skupiny jako jeho [nadřazeného elementu](../../extensibility/parent-element.md), vyhledejte SharedCmdPlace.vsct a ShellCmdPlace.vsct (nebo VsDbgCmdPlace.vsct pro příkazy ladicího programu) `<CommandPlacement>` element, který nastaví nadřazeného tohoto příkaz. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct ShellCmdPlace.vsct, jsou v *cestu instalace sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc\ složky.

## <a name="see-also"></a>Viz také
 [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) [tabulky příkazů sady Visual Studio (. Vsct) soubory](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [– referenční dokumentace schématu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)
