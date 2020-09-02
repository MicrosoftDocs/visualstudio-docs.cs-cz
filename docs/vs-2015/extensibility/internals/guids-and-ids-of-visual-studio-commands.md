---
title: Identifikátory GUID a ID příkazů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2feef3cbe72b7eb8db96052236fe483733e22273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538135"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identifikátory GUID a ID příkazů sady Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hodnoty identifikátoru GUID a ID příkazů zahrnutých v integrovaném vývojovém prostředí (IDE) sady Visual Studio jsou definovány v souborech. vsct, které jsou nainstalovány jako součást sady Visual Studio SDK. Další informace naleznete v tématu [příkazy, nabídky a skupiny definované rozhraním IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Další informace o tom, jak pracovat s objekty IDE, které jsou definovány v souborech. vsct, naleznete v tématu [rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

## <a name="finding-a-command-definition"></a>Hledání definice příkazu
 Vzhledem k tomu, že Visual Studio definuje více než 1000 příkazů, je nepraktické je uvést zde. Místo toho použijte následující postup k vyhledání definice příkazu.

#### <a name="to-locate-a-command-definition"></a>Vyhledání definice příkazu

1. V sadě Visual Studio otevřete následující soubory ve složce *Instalační cesta sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc\ složka: SharedCmdDef. vsct, ShellCmdDef. vsct, VsDbgCmdUsed. vsct, Venusmenu. vsct.

    Většina příkazů sady Visual Studio je definována v SharedCmdDef. vsct a ShellCmdDef. vsct. VsDbgCmdUsed. vsct definuje příkazy, které se vztahují k ladicímu programu, a Venusmenu. vsct definuje příkazy, které jsou specifické pro vývoj na webu.

2. Pokud je příkaz položkou nabídky, poznamenejte si přesný text položky nabídky. Pokud se jedná o tlačítko na panelu nástrojů, poznamenejte si text popisku, který se zobrazí při pozastavení.

3. Stisknutím kombinace kláves CTRL + F otevřete dialogové okno **Najít** .

4. Do pole **Najít** zadejte text, který jste si poznamenali v kroku 2.

5. Ověřte, že se v poli **Hledat v** zobrazí **všechny otevřené dokumenty** .

6. Klikněte na tlačítko **Najít další** , dokud se text nevybere v `<Strings>` části [elementu Button](../../extensibility/button-element.md).

    `<Button>`Element, ve kterém se příkaz objeví, je definice příkazu.

   Po nalezení definice příkazu můžete umístit kopii příkazu do jiné nabídky nebo panelu nástrojů vytvořením [prvku CommandPlacement](../../extensibility/commandplacement-element.md) , který má stejné `guid` `id` hodnoty a jako příkaz. Další informace najdete v tématu [vytváření opakovaně použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Zvláštní případy
 V následujících případech se text v nabídce nebo text popisku nemusí přesně shodovat s tím, co je v definici příkazu.

- Položky nabídky, které obsahují podtržený znak, jako je například příkaz **Tisk** v nabídce **soubor** , ve kterém je podtržena P.

     Znaky, které předcházejí znak ' & ' v názvech položek nabídky, jsou zobrazeny podtrženě. Soubory. vsct jsou však napsány v jazyce XML, který používá znak ' & ' k označení speciálních znaků a vyžaduje, aby byl znak ampersand, který se má zobrazit, zadán jako ' &amp; '. Proto se v souboru. vsct zobrazí příkaz **Tisk** jako &amp; Tisk.

- Příkazy, které mají dynamický text, jako je například **Uložit** *aktuální název souboru*a dynamicky generované položky nabídky, například položky v seznamu **Poslední soubory** .

     Neexistuje spolehlivý způsob, jak prohledávat dynamický text. Místo toho vyhledejte skupinu, která je hostitelem požadovaného příkazu, pomocí konzultačních [identifikátorů GUID a ID nabídek](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) nebo [identifikátorů GUID](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)sady Visual Studio a vyhledejte ID této skupiny. Pokud definice příkazu nemá skupinu jako svůj [nadřazený prvek](../../extensibility/parent-element.md), vyhledejte SharedCmdPlace. vsct a ShellCmdPlace. vsct (nebo VsDbgCmdPlace. vsct pro příkazy ladicího programu) pro `<CommandPlacement>` prvek, který nastaví nadřazený objekt příkazu. SharedCmdPlace. vsct, ShellCmdPlace. vsct, andVsDbgCmdPlace. vsct jsou ve složce *Instalační cesta sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc\.

## <a name="see-also"></a>Viz také
 [MenuCommands vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) [příkazová tabulka sady Visual Studio (. Vsct) soubory](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [vsct XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md)
