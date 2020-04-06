---
title: Identifikátory GUID a ID příkazů sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708257"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identifikátory GUID a ID příkazů sady Visual Studio
Hodnoty GUID a ID příkazů zahrnutých v integrovaném vývojovém prostředí sady Visual Studio (IDE) jsou definovány v souborech .vsct, které jsou nainstalovány jako součást sady Visual Studio SDK. Další informace naleznete v tématu [Příkazy, nabídky a skupiny definované ide](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Další informace o práci s objekty IDE, které jsou definovány v souborech *.vsct,* naleznete [v tématu Rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Vyhledání definice příkazu
 Vzhledem k tomu, že Visual Studio definuje více než 1000 příkazů, je nepraktické uvést je všechny zde. Místo toho postupujte podle následujících kroků vyhledejte definici příkazu.

### <a name="to-locate-a-command-definition"></a>Vyhledání definice příkazu

1. V sadě Visual Studio otevřete následující soubory v *instalační\>cestě sady<Sady\\ Visual Studio SDK \VisualStudioIntegration\Common\Inc:* *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    Většina příkazů sady Visual Studio je definována v *souborech SharedCmdDef.vsct* a *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* definuje příkazy, které se připojují k ladicímu programu, a *Venusmenu.vsct* definuje příkazy, které jsou specifické pro vývoj webu.

2. Pokud se jedná o příkaz položku nabídky, poznamenejte si přesný text položky nabídky. Pokud je příkazem tlačítko na panelu nástrojů, poznamenejte si text popisu, který se zobrazí při pozastavení.

3. Stisknutím **klávesy Ctrl**+**F** otevřete dialogové okno **Najít.**

4. Do pole **Najít** zadejte text, který jste si poznamenali v kroku 2.

5. Ověřte, zda jsou v poli **Hledat v** zobrazeny všechny **otevřené dokumenty.**

6. Klepněte na tlačítko **Najít další,** `<Strings>` dokud nebude text vybraný v části [Prvku Button](../../extensibility/button-element.md).

    Prvek, `<Button>` ve které se příkaz zobrazí, je definice příkazu.

   Pokud jste našli definici příkazu, můžete vložit kopii příkazu do jiné nabídky nebo panelu `id` nástrojů vytvořením [elementu CommandPlacement,](../../extensibility/commandplacement-element.md) který má stejné `guid` hodnoty a hodnoty jako příkaz. Další informace naleznete v [tématu Vytvoření opakovaně použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Zvláštní případy
 V následujících případech nemusí text nabídky nebo text popisku přesně odpovídat tomu, co je v definici příkazu.

- Položky nabídky, které obsahují podtržený znak, například příkaz **Tisk** v nabídce **Soubor,** ve kterém je podtrženo *P.*

     Znaky, kterým předchází znak ampersand (&) v názvech položek nabídky, jsou zobrazeny jako podtržené. Soubory *.vsct* jsou však zapsány ve formátu XML, který používá znak ampersand (&) k označení speciálních znaků a vyžaduje, aby ampersand, který má být zobrazen, musí být napsán jako * &amp;amp;*. Proto v souboru *.vsct* se příkaz **Tisk** zobrazí jako * &amp;a Tisk*.

- Příkazy, které mají dynamický **Save** \<text,\>například Uložit aktuální název souboru , a dynamicky generované položky nabídky, například položky v seznamu **Poslední soubory.**

     Neexistuje žádný spolehlivý způsob vyhledávání na dynamický text. Místo toho vyhledejte skupinu, která je hostitelem požadovaného příkazu, nahlédnutím do [guid a ID nabídek sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) nebo [guid a ID panelů nástrojů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)a vyhledáním ID této skupiny. Pokud definice příkazu nemá skupinu jako [nadřazený prvek](../../extensibility/parent-element.md), vyhledejte *SharedCmdPlace.vsct* a *ShellCmdPlace.vsct* (nebo *VsDbgCmdPlace.vsct* pro ladicí příkazy) pro `<CommandPlacement>` prvek, který nastaví nadřazený příkaz. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*a *VsDbgCmdPlace.vsct* jsou ve * \<složce\>instalace sady Visual Studio\\ SDK \VisualStudioIntegration\Common\Inc.*

## <a name="see-also"></a>Viz také

- [Soubory příkazů sady Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odkaz na schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
