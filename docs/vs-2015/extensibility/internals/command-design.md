---
title: Návrh příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6e9eaf69be62b38a880b07fd8eb51cfc9c256a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195078"
---
# <a name="command-design"></a>Návrh příkazu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Když přidáte příkaz do balíčku VSPackage, je nutné určit, kde se má objevit, kdy je k dispozici a jak má být zpracován.  
  
## <a name="defining-commands"></a>Definování příkazů  
 Chcete-li definovat nové příkazy, zahrňte do projektu VSPackage soubor tabulky příkazů sady Visual Studio (. vsct). Pokud jste vytvořili VSPackage pomocí šablony balíčku sady Visual Studio, projekt obsahuje jeden z těchto souborů. Další informace naleznete v tématu [tabulka příkazů sady Visual Studio (. Vsct) soubory](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio sloučí všechny soubory. vsct, které najde, aby mohl zobrazit příkazy. Vzhledem k tomu, že tyto soubory jsou odlišné od binárního souboru VSPackage, sada Visual Studio nemusí načíst balíček, aby bylo možné najít příkazy. Další informace najdete v tématu [jak prvky VSPackage přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio používá <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> registrační atribut k definování prostředků a příkazů nabídky. Další informace najdete v tématu [implementace](../../extensibility/internals/command-implementation.md).  
  
 Příkazy lze v době běhu měnit několika různými způsoby. Je možné je zobrazit nebo skrýt, povolit nebo zakázat. Mohou zobrazovat různý text nebo ikony nebo obsahovat jiné hodnoty. Velký způsob přizpůsobení může být proveden předtím, než aplikace Visual Studio načte VSPackage. Další informace najdete v tématu [jak prvky VSPackage přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Obslužné rutiny příkazů  
 Při vytváření příkazu je nutné zadat obslužnou rutinu události ke spuštění příkazu. Pokud uživatel vybere příkaz, musí být vhodně směrován. Směrování příkazu znamená, že ho pošle do správného VSPackage, aby ho mohl povolit nebo zakázat, skrýt nebo zobrazit a spustit v případě, že to uživatel zvolí. Další informace najdete v tématu [algoritmus směrování](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Příkazové prostředí sady Visual Studio  
 Sada Visual Studio může hostovat libovolný počet VSPackage a každá z nich může přispívat do své vlastní sady příkazů. Prostředí zobrazí pouze příkazy, které jsou pro aktuální úlohu vhodné. Další informace naleznete v tématu [objekty kontextu](../../extensibility/internals/selection-context-objects.md) [dostupnosti](../../extensibility/internals/command-availability.md) a výběru.  
  
 VSPackage, který definuje nové příkazy, nabídky, panely nástrojů nebo místní nabídky, poskytuje informace o příkazech sady Visual Studio v době instalace prostřednictvím položek registru, které odkazují na prostředky v nativních nebo spravovaných sestaveních. Každý prostředek pak odkazuje na binární soubor datového zdroje (. technický ředitel), který je vytvořen při kompilaci souboru tabulky příkazů sady Visual Studio (. vsct). To umožňuje sadě Visual Studio poskytovat sloučené sady příkazů, nabídky a panely nástrojů bez nutnosti načíst všechny nainstalované VSPackage.  
  
### <a name="command-organization"></a>Organizace příkazu  
 Prostředí umisťuje příkazy podle skupiny, priority a nabídky.  
  
- Skupiny jsou logické kolekce souvisejících příkazů, například skupina příkazů **Vyjmout**, **Kopírovat**a **Vložit** . Skupiny jsou příkazy, které se zobrazují v nabídkách.  
  
- Priorita určuje pořadí, ve kterém se jednotlivé příkazy ve skupině zobrazí v nabídce.  
  
- Nabídky slouží jako kontejnery pro skupiny.  
  
  Prostředí předdefinovány některé příkazy, skupiny a nabídky. Další informace najdete v tématu [výchozí umístění příkazů, skupin a panelů nástrojů](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Příkaz se dá přiřadit k primární skupině. Primární skupina řídí pozici příkazu ve struktuře hlavní nabídky a v dialogovém okně **přizpůsobit** . Příkaz se může objevit ve více skupinách. Například příkaz může být v hlavní nabídce, v místní nabídce a na panelu nástrojů. Další informace najdete v tématu [jak prvky VSPackage přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Směrování příkazů  
 Proces vyvolání a směrování příkazů pro VSPackage se liší od procesu volání metod v instancích objektů.  
  
 Prostředí směruje příkazy postupně z nejvnitřnějšího (místního) příkazu, který je založen na aktuálním výběru, do nejvzdálenějšího (globálního) kontextu. První kontext, který je schopný spustit příkaz, je ten, který ho zpracovává. Další informace najdete v tématu [algoritmus směrování](../../extensibility/internals/command-routing-algorithm.md).  
  
 Ve většině instancí prostředí zpracovává příkazy pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Vzhledem k tomu, že schéma směrování příkazu umožňuje mnoha různým objektům zpracovávat příkazy, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> lze implementovat libovolným počtem objektů. mezi ně patří ovládací prvky Microsoft ActiveX, implementace zobrazení oken, objekty dokumentu, hierarchie projektu a objekty VSPackage (pro globální příkazy). V některých specializovaných případech, například v příkazech směrování v hierarchii, je <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nutné implementovat rozhraní.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Implementace](../../extensibility/internals/command-implementation.md)|Popisuje, jak implementovat příkazy v VSPackage.|  
|[Dostupnost](../../extensibility/internals/command-availability.md)|Popisuje, jak kontext sady Visual Studio určuje, které příkazy jsou k dispozici.|  
|[Algoritmus směrování](../../extensibility/internals/command-routing-algorithm.md)|Popisuje, jak architektura směrování příkazů sady Visual Studio umožňuje, aby příkazy byly zpracovávány různými VSPackage.|  
|[Pokyny pro umístění](../../extensibility/internals/command-placement-guidelines.md)|Navrhuje, jak umístit příkazy v prostředí sady Visual Studio.|  
|[Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Popisuje, jak mohou sady VSPackage nejlépe využít architekturu příkazů sady Visual Studio.|  
|[Výchozí umístění příkazů, skupin a panelů nástrojů](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Popisuje, jak mohou sady VSPackage nejlépe využít příkazy, které jsou součástí sady Visual Studio.|  
|[Správa rozšíření VSPackages](../../extensibility/managing-vspackages.md)|Popisuje, jak Visual Studio načítá sady VSPackage.|  
|[Soubory tabulek příkazů sady Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Poskytuje informace o souborech. vsct založených na XML, které se používají k popisu rozložení a vzhledu příkazů v VSPackage.|
