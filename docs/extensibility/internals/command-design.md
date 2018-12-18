---
title: Příkaz návrhu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5bd810d0c2f33d4a8ddbffd876357ead7e0e5e7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816505"
---
# <a name="command-design"></a>Návrh příkazu
Při přidání příkazu do VSPackage, musíte zadat, kam se má zobrazit, když je k dispozici a jak je zpracovat.  
  
## <a name="define-commands"></a>Definujte příkazy  
 Pokud chcete definovat nové příkazy, zahrnují tabulky příkazů sady Visual Studio (*.vsct*) soubor v projektu VSPackage. Když vytvoříte VSPackage pomocí balíčku šablony sady Visual Studio projekt obsahuje některý z těchto souborů. Další informace najdete v tématu [soubory tabulky (.vsct) příkazů sady Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio slučuje všechny *.vsct* soubory ho najde, tak, aby ho zobrazit příkazy. Protože tyto soubory se liší od sady VSPackage binární, není nutné načíst balíček najít příkazy sady Visual Studio. Další informace najdete v tématu [jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio používá <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> registrace atribut pro definování prostředků nabídky a příkazy. Další informace najdete v tématu [implementace příkazu](../../extensibility/internals/command-implementation.md).  
  
 Příkazy lze změnit za běhu v několika různými způsoby. Můžete zobrazit nebo skryté, povolit nebo zakázat. Můžete zobrazit jiné text nebo ikony nebo obsahovat různé hodnoty. Spoustu přizpůsobení mohou být provedeny před Visual Studio načte vašeho balíčku VSPackage. Další informace najdete v tématu [jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Obslužné rutiny příkazů  
 Když vytvoříte příkaz, je nutné zadat obslužnou rutinu události ke spuštění příkazu. Pokud si uživatel vybere příkaz, se musí být odpovídajícím způsobem směrovaná. Směrování příkazu znamená, že odesílání správný VSPackage chcete povolit nebo zakázat, skrýt nebo zobrazit ho a proveďte jej, pokud uživatel zvolí možnost udělat. Další informace najdete v tématu [algoritmus směrování příkazů](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="visual-studio-command-environment"></a>Visual Studio příkazového prostředí  
 Visual Studio může být hostitelem libovolný počet rozšíření VSPackages a každý může přispívat svou vlastní sadu příkazů. Prostředí se zobrazí jenom příkazy, které jsou vhodné pro aktuální úlohu. Další informace najdete v tématu [příkaz dostupnosti](../../extensibility/internals/command-availability.md) a [kontextové objekty výběru](../../extensibility/internals/selection-context-objects.md).  
  
 VSPackage, která definuje nové příkazy, nabídky, panely nástrojů nebo místní nabídky do sady Visual Studio poskytuje jeho informace o příkazu v době instalace prostřednictvím položky registru, které odkazují na prostředky v nativním nebo spravovaným sestavení. Každý prostředek pak odkazuje na prostředek binárních dat (*.cto*) soubor, který je vytvořen při kompilaci tabulky příkazů sady Visual Studio (*.vsct*) soubor. Díky tomu Visual Studio, abyste sady sloučené příkazů, nabídek a panelů nástrojů bez nutnosti načtení všech nainstalovaných VSPackage.  
  
### <a name="command-organization"></a>Příkaz organizace  
 Prostředí umístí příkazů podle skupiny, priority a nabídky.  
  
- Skupiny jsou logické kolekce související příkazy, například, **Vyjmout**, **kopírování**, a **vložit** skupinu příkazů. Skupiny jsou příkazy, které se zobrazují v nabídkách.  
  
- Priorita určuje pořadí, ve kterém se zobrazují jednotlivé příkazy ve skupině v nabídce.  
  
- Nabídky fungují jako kontejnery pro skupiny.  
  
  Prostředí predefines některé příkazy, skupiny a nabídek. Další informace najdete v tématu [výchozí příkaz, skupiny a panelu nástrojů umístění](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Příkaz je možné přiřadit ke skupině primární. Určuje pozici příkazu v hlavní nabídce struktuře a v primární skupině **vlastní** dialogové okno. Příkaz může objevit ve více skupinách; příkaz může být například v hlavní nabídce, v místní nabídce a na panelu nástrojů. Další informace najdete v tématu [jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Směrování příkazů  
 Proces směrování příkazů pro rozšíření VSPackages a volání se liší od procesu volání metod na instance objektů.  
  
 Prostředí směruje příkazy sekvenčně od nejvnitřnější (místní) příkaz kontext, který je založen na aktuální výběr, vnějšího (globální) v kontextu. První kontext, aby bylo možné provést příkaz je ta, kterou to všechno zvládne. Další informace najdete v tématu [algoritmus směrování příkazů](../../extensibility/internals/command-routing-algorithm.md).  
  
 Ve většině případů prostředí zpracovává příkazy pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Protože mnoho různých objektů zpracovává příkazy, umožňuje směrování schéma příkaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> může implementovat libovolný počet objektů; tyto patří ovládací prvky ActiveX, implementace okna zobrazení, objekty dokumentu, hierarchie projektu a VSPackage samotných objektech (pro globální příkazy). V některých případech specializované například směrování příkazů v hierarchii, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> musí implementovat rozhraní.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Implementace příkazu](../../extensibility/internals/command-implementation.md)|Popisuje, jak implementovat příkazy v sadě VSPackage.|  
|[Dostupnost příkazu](../../extensibility/internals/command-availability.md)|Popisuje, jak Visual Studio kontext určuje, které příkazy jsou k dispozici.|  
|[Algoritmus směrování příkazů](../../extensibility/internals/command-routing-algorithm.md)|Popisuje, jak směrování architektury sady Visual Studio příkaz povolí příkazy zpracovávat jiné rozšíření VSPackages.|  
|[Pokyny pro umístění příkazu](../../extensibility/internals/command-placement-guidelines.md)|Navrhne, jak chcete umístit příkazy v prostředí sady Visual Studio.|  
|[Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Popisuje, jak balíčky VSPackages nejlépe využít příkaz architektury sady Visual Studio.|  
|[Výchozí umístění příkazu, skupiny a nástrojů](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Popisuje, jak můžete pomocí rozšíření VSPackages nejlépe příkazy, které jsou zahrnuty v sadě Visual Studio.|  
|[Správa rozšíření VSPackages](../../extensibility/managing-vspackages.md)|Popisuje, jak Visual Studio načte rozšíření VSPackages.|  
|[Soubory tabulky (.vsct) příkaz pro Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Poskytuje informace o formátu XML *.vsct* soubory, které se používají k popisu rozložení a vzhled příkazů v balíčcích VSPackage.|