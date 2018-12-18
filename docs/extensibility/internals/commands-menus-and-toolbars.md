---
title: Příkazy, nabídky a panely nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a8bd6716b40816ae625dcdb32fb62237aa543fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928422"
---
# <a name="commands-menus-and-toolbars"></a>Příkazy, nabídky a panely nástrojů
Nabídky a panely nástrojů jsou způsob, jak uživatelům přístup k příkazům v vašeho balíčku VSPackage. Příkazy jsou funkce, které provádět úlohy, jako je například tisk dokumentu, aktualizuje zobrazení nebo vytvoření nového souboru. Nabídky a panely nástrojů jsou vhodné grafické způsoby, jak uživatelům k dispozici vaše příkazy. Související příkazy jsou obvykle Clusterované společně na stejném nabídky nebo panelu nástrojů.  
  
- Nabídky se obvykle zobrazují jako jednoslovným řetězce v řádku v horní části integrovaného vývojového prostředí (IDE) nebo panelu nástrojů v clusteru. Nabídky také mohou být zobrazeny v důsledku události kliknutí pravým tlačítkem myši a jsou označovány jako místní nabídky v tomto kontextu. Po kliknutí na nabídky rozbalte seznam jednoho nebo více příkazů. Příkazy, při kliknutí můžete provádět úlohy, nebo spusťte dílčích nabídek, které obsahují další příkazy. Některé názvy dobře známé nabídky jsou **souboru**, **upravit**, **zobrazení**, a **okno**. Další informace najdete v tématu [rozšířit nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).  
  
- Panely nástrojů jsou obvykle řádky tlačítka a další ovládací prvky, jako je například pole se seznamem, pole se seznamem, textová pole a nabídky řadiče. Všechny ovládací prvky panelu nástrojů jsou spojeny s příkazy. Po kliknutí na tlačítko panelu nástrojů, se aktivuje jeho přidružený příkaz. Tlačítka panelu nástrojů mají obvykle ikon, které naznačují základní příkazy, jako je například tiskárny pro tisk příkaz. V ovládacím prvku rozevíracího seznamu je přidružen k jinému příkazu každou položku v seznamu. Kontroleru nabídky je hybridní, ve kterém straně ovládacího prvku je tlačítko panelu nástrojů a je šipku dolů, která se zobrazí další příkazy při kliknutí na druhé straně. Další informace najdete v tématu [přidání kontroleru nabídky do panelu nástrojů](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
- Když vytvoříte příkaz, také musíte vytvořit obslužnou rutinu události pro něj. Obslužná rutina události určuje po příkazu je viditelný nebo povoleno, umožňuje změnit jeho textu a zajistí, že příkaz náležitě reaguje ("trasy") při aktivaci. Ve většině případů, rozhraní IDE zpracovává příkazy pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Příkazy v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] trasy hierarchické způsobem, počínaje kontext nejvnitřnější příkazů, na základě výběru v místní a pokračuje na vnější kontext na základě výběru v globální. Příkazy, které jsou přidány do hlavní nabídky jsou okamžitě k dispozici pro skriptování. Další informace najdete v tématu [MenuCommands vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) a [kontextové objekty výběru](../../extensibility/internals/selection-context-objects.md).  
  
  Chcete-li definovat nové nabídky a panely nástrojů, musíte popsat je v tabulky příkazů sady Visual Studio (*.vsct*) soubor. Balíček šablony sady Visual Studio vytvoří tento soubor, spolu s prvky potřebné pro podporu libovolné příkazy, panely nástrojů a editory vybrány v šabloně. Alternativně můžete napsat vlastní *.vsct* soubor, pomocí schématu XML je popsáno zde: [– referenční dokumentace schématu VSCT XML](../../extensibility/vsct-xml-schema-reference.md).  
  
  Další informace o práci s *.vsct* soubory, naleznete v tématu [soubory tabulky (.vsct) příkazů sady Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
  Témata v této části popisují, jak fungují v balíčcích VSPackage příkazy, nabídky a panely nástrojů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Podrobný popis příkazu specifikace formátu tabulky.  
  
 [Soubory tabulky (.vsct) příkaz pro Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Popisuje syntaxi založené na XML a služby kompilátoru pro příkaz tabulky.  
  
 [Výchozí umístění příkazu, skupiny a nástrojů](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Popisuje předdefinované příkazů, skupin, nabídek a panelů nástrojů.  
  
 [Příkazy definované prostředím IDE, nabídky a skupiny](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Určuje předdefinované nabídek, příkazy a skupinu příkazů, které jsou k dispozici pro použití [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí.  
  
 [Návrh příkazu](../../extensibility/internals/command-design.md)  
 Vysvětluje, jak navrhovat příkazy.  
  
 [Optimalizace příkazů nabídky a panelu nástrojů](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Poskytuje pokyny pro příkazy.  
  
 [Zpřístupnění příkazů](../../extensibility/internals/making-commands-available.md)  
 Vysvětluje, jak zpřístupnit příkazy sady Visual Studio.  
  
 [Příkazy a nabídky, které používají spolupracující sestavení](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Vysvětluje, jak implementovat příkazy, které používají spolupracující sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Směrování příkazů v balíčcích VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Tento článek vysvětluje směrování příkazů v balíčcích VSPackage.