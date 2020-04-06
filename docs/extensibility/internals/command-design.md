---
title: Návrh příkazu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709660"
---
# <a name="command-design"></a>Návrh příkazu
Přidáte-li příkaz v Balíčku VSPackage, musíte určit, kde se má zobrazit, kdy je k dispozici a jak má být zpracován.

## <a name="define-commands"></a>Definování příkazů
 Chcete-li definovat nové příkazy, zahrňte do projektu VSPackage soubor příkazu Sady Visual Studio (*.vsct*). Pokud jste vytvořili VSPackage pomocí šablony balíčku Sady Visual Studio, projekt obsahuje jeden z těchto souborů. Další informace naleznete v tématu [Visual Studio příkaz tabulka (.vsct) soubory](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

 Visual Studio sloučí všechny *.vsct* soubory, které najde, aby bylo možné zobrazit příkazy. Vzhledem k tomu, že tyto soubory se liší od binárního souboru VSPackage, visual studio není třeba načíst balíček najít příkazy. Další informace naleznete v tématu [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> používá atribut registrace k definování prostředků a příkazů nabídky. Další informace naleznete v [tématu Command implementation](../../extensibility/internals/command-implementation.md).

 Příkazy lze měnit za běhu několika různými způsoby. Mohou být zobrazeny nebo skryté, povolené nebo zakázané. Mohou zobrazovat jiný text nebo ikony nebo obsahovat různé hodnoty. Velké množství přizpůsobení může být provedena před Visual Studio načte váš VSPackage. Další informace naleznete v tématu [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Obslužné rutiny příkazů
 Při vytváření příkazu je nutné zadat obslužnou rutinu události ke spuštění příkazu. Pokud uživatel vybere příkaz, musí být odpovídajícím způsobem směrován. Směrování příkazu znamená jeho odeslání do správného balíčku VSPackage, který jej povolí nebo zakáže, skryje nebo zobrazí a spustí, pokud se uživatel rozhodne tak učinit. Další informace naleznete v [tématu Command routing algorithm](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Prostředí příkazů sady Visual Studio
 Visual Studio může hostit libovolný počet VSPackages a každý může přispět vlastní sadu příkazů. Prostředí zobrazuje pouze příkazy, které jsou vhodné pro aktuální úlohu. Další informace naleznete v [tématu Command availability](../../extensibility/internals/command-availability.md) and [Selection context objects](../../extensibility/internals/selection-context-objects.md).

 Balíček VSPackage, který definuje nové příkazy, nabídky, panely nástrojů nebo místní nabídky, poskytuje informace o příkazech sady Visual Studio v době instalace prostřednictvím položek registru, které odkazují na prostředky v nativních nebo spravovaných sestaveních. Každý prostředek pak odkazuje na binární datový prostředek (*.cto*) soubor, který je vytvořen při kompilaci souboru příkazů sady Visual Studio (*.vsct).* To umožňuje visual studio poskytovat sloučené sady příkazů, nabídky a panely nástrojů bez nutnosti načítat všechny nainstalované VSPackage.

### <a name="command-organization"></a>Velitelská organizace
 Prostředí umístí příkazy podle skupiny, priority a nabídky.

- Skupiny jsou logické kolekce souvisejících příkazů, například skupina příkazů **Vyjmout**, **Kopírovat**a **Vložit.** Skupiny jsou příkazy, které se zobrazují v nabídkách.

- Priorita určuje pořadí, ve kterém se jednotlivé příkazy ve skupině zobrazují v nabídce.

- Nabídky fungují jako kontejnery pro skupiny.

  Prostředí předdefinuje některé příkazy, skupiny a nabídky. Další informace naleznete [v tématu Výchozí umístění příkazů, skupin a panelu nástrojů](../../extensibility/internals/default-command-group-and-toolbar-placement.md).

  Příkaz lze přiřadit k primární skupině. Primární skupina řídí umístění příkazu ve struktuře hlavní nabídky a v dialogovém okně **Přizpůsobit.** Příkaz se může zobrazit ve více skupinách. příkaz může být například v hlavní nabídce, v místní nabídce a na panelu nástrojů. Další informace naleznete v tématu [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Směrování příkazů
 Proces vyvolání a směrování příkazů pro VSPackages se liší od procesu volání metod na instance objektu.

 Prostředí směruje příkazy postupně z nejvnitřnějšího (místního) kontextu příkazu, který je založen na aktuálním výběru, do nejvzdálenějšího (globálního) kontextu. První kontext, který je schopen spustit příkaz je ten, který zpracovává. Další informace naleznete v [tématu Command routing algorithm](../../extensibility/internals/command-routing-algorithm.md).

 Ve většině případů prostředí zpracovává příkazy pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Vzhledem k tomu, že schéma směrování <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> příkazů umožňuje mnoho různých objektů pro zpracování příkazů, lze implementovat libovolný počet objektů; Patří mezi ně ovládací prvky Microsoft ActiveX, implementace zobrazení oken, objekty dokumentu, hierarchie projektu a samotné objekty VSPackage (pro globální příkazy). V některých specializovaných případech, například směrovací příkazy v hierarchii, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní musí být implementována.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Implementace příkazu](../../extensibility/internals/command-implementation.md)|Popisuje, jak implementovat příkazy v Balíčku VSPackage.|
|[Dostupnost příkazu](../../extensibility/internals/command-availability.md)|Popisuje, jak kontext sady Visual Studio určuje, které příkazy jsou k dispozici.|
|[Algoritmus směrování příkazů](../../extensibility/internals/command-routing-algorithm.md)|Popisuje, jak architektura směrování příkazů sady Visual Studio umožňuje zpracování příkazů různými balíčky VSPackages.|
|[Pokyny pro umístění příkazů](../../extensibility/internals/command-placement-guidelines.md)|Navrhuje umístění příkazů v prostředí sady Visual Studio.|
|[Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Popisuje, jak vSPackages můžete nejlépe využít architekturu příkazů sady Visual Studio.|
|[Výchozí umístění příkazu, skupiny a panelu nástrojů](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Popisuje, jak VSPackages můžete nejlépe použít příkazy, které jsou součástí sady Visual Studio.|
|[Správa balíčků VSPackage](../../extensibility/managing-vspackages.md)|Popisuje, jak Visual Studio načte VSPackages.|
|[Soubory příkazů sady Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Obsahuje informace o souborech *VSCT* založených na jazyce XML, které slouží k popisu rozložení a vzhledu příkazů v souborech VSPackages.|
