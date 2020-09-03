---
title: Příkazy, nabídky a panely nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 61
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 337bc4de9171d2f98bf0be0068b298b7f600b979
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155834"
---
# <a name="commands-menus-and-toolbars"></a>Příkazy, nabídky a panely nástrojů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nabídky a panely nástrojů jsou způsobem, kterým uživatelé přistupují k příkazům ve VSPackage. Příkazy jsou funkce, které provádějí úlohy, jako je například tisk dokumentu, aktualizace zobrazení nebo vytvoření nového souboru. Nabídky a panely nástrojů jsou praktické grafické způsoby, jak prezentovat příkazy uživatelům. Související příkazy jsou obvykle seskupené do stejné nabídky nebo panelu nástrojů.  
  
- Nabídky se obvykle zobrazují jako řetězce v jednom slově seskupené v řádku na vrcholu integrovaného vývojového prostředí (IDE) nebo panelu nástrojů. Nabídky lze také zobrazit jako výsledek události kliknutí pravým tlačítkem myši a jsou označovány jako místní nabídky v tomto kontextu. Po kliknutí se nabídky rozbalí a zobrazí se jeden nebo více příkazů. Příkazy, při kliknutí, mohou provádět úlohy nebo podnabídky, které obsahují další příkazy. Některé dobře známé nabídky jsou soubory, úpravy, zobrazení a okno. Další informace najdete v tématu [rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).  
  
- Panely nástrojů jsou typicky řádky tlačítek a dalších ovládacích prvků, jako jsou pole se seznamem, seznamy, textová pole a řadiče nabídek. Všechny ovládací prvky panelu nástrojů jsou přidruženy k příkazům. Když kliknete na tlačítko panelu nástrojů, aktivuje se jeho přidružený příkaz. Tlačítka panelu nástrojů mají obvykle ikony, které navrhují příslušné příkazy, jako je například tiskárna pro tiskový příkaz. V ovládacím prvku rozevírací seznam je každá položka v seznamu přidružena k jinému příkazu. Kontroler nabídek je hybrid, ve kterém je jedna strana ovládacího prvku tlačítko panelu nástrojů a druhá strana má šipku dolů, která při kliknutí zobrazuje další příkazy. Další informace najdete v tématu [Přidání řadiče nabídky na panel nástrojů](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
- Při vytváření příkazu je nutné pro něj také vytvořit obslužnou rutinu události. Obslužná rutina události Určuje, zda je příkaz viditelný nebo povolený, umožňuje upravit jeho text a zajistí, že příkaz reaguje správně ("trasy") při aktivaci. Ve většině instancí rozhraní IDE zpracovává příkazy pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Příkazy v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] cestě hierarchicky, počínaje nejvnitřnějším kontextem příkazu na základě místního výběru a pokračováním do nejvzdálenějšího kontextu v závislosti na globálním výběru. Příkazy přidané do hlavní nabídky jsou okamžitě k dispozici pro skriptování. Další informace naleznete v tématu [MenuCommands vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) and [Selection Context Objects](../../extensibility/internals/selection-context-objects.md).  
  
  Chcete-li definovat nové nabídky a panely nástrojů, je třeba je popsat v souboru tabulky příkazů sady Visual Studio (. vsct). Šablona balíčku sady Visual Studio vytvoří tento soubor za vás spolu s potřebnými prvky pro podporu jakýchkoli příkazů, panelů nástrojů a editorů, které jste vybrali v šabloně. Alternativně můžete napsat vlastní soubor. vsct pomocí schématu XML popsané zde: [vsct XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
  Další informace o práci se soubory. vsct naleznete v tématu [tabulka příkazů sady Visual Studio (. Vsct) soubory](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
  Témata v této části popisují, jak fungují příkazy, nabídky a panely nástrojů ve VSPackage.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Podrobný popis specifikace formátu tabulky příkazů.  
  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Popisuje syntaxi a kompilátor založený na jazyce XML pro tabulky příkazů.  
  
 [Výchozí umístění příkazů, skupin a panelů nástrojů](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Popisuje předdefinované příkazy, skupiny, nabídky a panely nástrojů.  
  
 [Příkazy, nabídky a skupiny definované integrovaným vývojovým prostředím](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Určuje předdefinované nabídky, příkazy a skupiny příkazů, které jsou k dispozici pro použití v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozhraní IDE.  
  
 [Návrh příkazu](../../extensibility/internals/command-design.md)  
 Vysvětluje, jak navrhovat příkazy.  
  
 [Optimalizace příkazů nabídky a panelu nástrojů](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Obsahuje pokyny pro příkazy.  
  
 [Zpřístupnění příkazů](../../extensibility/internals/making-commands-available.md)  
 Vysvětluje, jak zpřístupnit příkazy pro Visual Studio.  
  
 [Příkazy a nabídky, které používají definiční sestavení](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Vysvětluje, jak implementovat příkazy, které používají definiční sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Směrování příkazů v balíčcích VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Vysvětluje směrování příkazů v VSPackage.
