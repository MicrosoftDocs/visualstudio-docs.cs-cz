---
title: Příkazy, nabídky a panely nástrojů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2be2f719d0f123328d5c518c08e30df2185e2a19
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709507"
---
# <a name="commands-menus-and-toolbars"></a>Příkazy, nabídky a panely nástrojů
Nabídky a panely nástrojů jsou způsob, jakým uživatelé přistupují k příkazům ve vašem balíčku VSPackage. Příkazy jsou funkce, které provádějí úkoly, jako je tisk dokumentu, aktualizace zobrazení nebo vytvoření nového souboru. Nabídky a panely nástrojů jsou vhodné grafické způsoby, jak prezentovat příkazy uživatelům. Související příkazy jsou obvykle seskupeny ve stejné nabídce nebo panelu nástrojů.

- Nabídky jsou obvykle zobrazeny jako jednoslovné řetězce seskupené v řádku v horní části integrovaného vývojového prostředí (IDE) nebo okna nástroje. Nabídky lze také zobrazit jako výsledek události po kliknutí pravým tlačítkem myši a v tomto kontextu se označují jako místní nabídky. Po klepnutí se nabídky rozbalí a zobrazí jeden nebo více příkazů. Příkazy po klepnutí mohou provádět úkoly nebo spouštět podnabídky, které obsahují další příkazy. Některé známé názvy nabídek jsou **Soubor**, **Úprava**, **Zobrazení**a **Okno**. Další informace naleznete v [tématu Rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

- Panely nástrojů jsou obvykle řádky tlačítek a dalšíovládací prvky, jako jsou pole se seznamem, seznamy, textová pole a řadiče nabídek. Všechny ovládací prvky panelu nástrojů jsou přidruženy k příkazům. Po klepnutí na tlačítko panelu nástrojů se aktivuje jeho přidružený příkaz. Tlačítka panelu nástrojů mají obvykle ikony, které navrhují základní příkazy, například tiskárnu pro příkaz Tisk. V ovládacím prvku rozevíracího seznamu je každá položka v seznamu přidružena k jinému příkazu. Řadič nabídky je hybrid, ve kterém jedna strana ovládacího prvku je tlačítko panelu nástrojů a druhá strana je šipka dolů, která zobrazuje další příkazy po klepnutí. Další informace naleznete [v tématu Přidání ovladače nabídky na panel nástrojů](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Při vytváření příkazu je také nutné vytvořit obslužnou rutinu události. Obslužná rutina události určuje, kdy je příkaz viditelný nebo povolený, umožňuje upravit jeho text a zajistí, že příkaz při aktivaci odpovídajícím způsobem odpoví ("trasy"). Ve většině případů ide zpracovává příkazy <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pomocí rozhraní. Příkazy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v cestě hierarchickým způsobem, počínaje nejvnitřnějším kontextem příkazu, na základě místního výběru a přecvakující k nejvzdálenějšímu kontextu na základě globálního výběru. Příkazy přidané do hlavní nabídky jsou okamžitě k dispozici pro skriptování. Další informace naleznete [v tématu MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015) and [Selection context objects](../../extensibility/internals/selection-context-objects.md).

  Chcete-li definovat nové nabídky a panely nástrojů, musíte je popsat v souboru příkazu Sady Visual Studio (*.vsct*). Šablona balíčku sady Visual Studio vytvoří tento soubor pro vás spolu s prvky nezbytné pro podporu bez ohledu na příkazy, panely nástrojů a editory, které jste vybrali v šabloně. Případně můžete napsat vlastní soubor *.vsct* pomocí schématu XML popsaného zde: [Odkaz na schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

  Další informace o práci se soubory *.vsct* naleznete v [tématu Soubory příkazů sady Visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

  Témata v této části vysvětlují, jak příkazy, nabídky a panely nástrojů fungují v Položkách VSPackages.

## <a name="in-this-section"></a>V tomto oddílu
- [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Podrobný popis specifikace formátu tabulky příkazů.

- [Soubory příkazů sady Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Popisuje syntaxi a kompilátor založený na jazyce XML pro tabulky příkazů.

- [Výchozí umístění příkazu, skupiny a panelu nástrojů](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Popisuje předdefinované příkazy, skupiny, nabídky a panely nástrojů.

- [Příkazy, nabídky a skupiny definované ide](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Určuje předdefinované nabídky, příkazy a skupiny příkazů, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] které jsou k dispozici pro použití rozhraním IDE.

- [Návrh příkazu](../../extensibility/internals/command-design.md)

 Vysvětluje, jak navrhovat příkazy.

- [Optimalizace příkazů nabídek a panelu nástrojů](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Poskytuje pokyny pro příkazy.

- [Zpřístupnění příkazů](../../extensibility/internals/making-commands-available.md)

 Vysvětluje, jak zpřístupnit příkazy visual studio.

- [Příkazy a nabídky, které používají mezioperační sestavy](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Vysvětluje, jak implementovat příkazy, které používají interop sestavení.

## <a name="related-sections"></a>Související oddíly
- [Směrování příkazů v balíčcích VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Vysvětluje směrování příkazů v VSPackages.
