---
title: Související služby a rozhraní (správa zdrojového kódu VSPackage) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 533f1bf4fcfbaebb25ec10908abf4a46ddacd521
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705630"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Související služby a rozhraní (balíček VSPackage správy zdrojového kódu)
Tato část obsahuje seznam všech rozhraní souvisejících se [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]službou VSPackage správy portů v rozhraní . Zdroj ovládacího prvku VSPackage implementuje některé z těchto rozhraní a používá jiné k provedení úloh správy zdrojového kódu.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Rozhraní implementovaná a pro řízení zdrojového kódu VSPackages
 Následující rozhraní jsou popsány [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]v , a zdrojový prvek VSPackage implementuje podmnožinu z nich v závislosti na jeho požadovanou sadu funkcí. Některá rozhraní jsou označeny jako povinné a musí být implementovány každý zdroj ového ovládacího prvku VSPackage.

 Pro rozhraní, která balíček neimplementuje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje výchozí implementaci. Všimněte si, že výchozí implementace je určena pro případ, kdy není registrován žádný VSPackage a žádný projekt je řízen. Správně napsaný zdrojový prvek VSPackage implementuje všechna potřebná rozhraní, nikoli ji ponechávají na výchozí implementaci těchto rozhraní.

 Zdroj ovládacího prvku VSPackage musí implementovat soukromou službu, která zapouzdřuje některé nebo všechny následující rozhraní.

 Rozhraní jsou:

- Povinné: Příslušná entita (správa zdrojového kódu VSPackage, útržek správy zdrojového kódu, projekt) musí implementovat rozhraní.

- Doporučeno: Entita by měla implementovat toto rozhraní; v opačném případě může být omezena funkce správy zdrojového kódu.

- Volitelné: entita může implementovat toto rozhraní poskytnout bohatší sadu funkcí.

| Rozhraní | Účel | Implementováno | Implementovat? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Editoři volají toto rozhraní před úpravou nebo uložením souboru. Zdrojový ovládací prvek VSPackage můžete rezervovat soubor nebo odmítnout operaci, pokud se nezdaří pokladny. | Ovládací prvek zdroje VSPackage | Doporučené |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Toto rozhraní poskytuje základní funkce správy zdrojového kódu pro projekty, jako je například registrace a zrušení registrace projektů se slučováním zdrojového kódu a poskytování podpory pro základní glyfy správy zdrojového kódu. | Ovládací prvek zdroje VSPackage | Požaduje se |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Toto rozhraní je <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> získáno pomocí <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> funkce nebo jednoduše `IVsHierarchy` přetypováním objektu implementujícího do `IVsSccProject2`. Používá se pro získání souborů pod směřování zdrojového kódu v projektu nebo pro informování projektu o aktuálním stavu správy zdrojového kódu nebo umístění. | Project | Požaduje se |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Integrační modul používá toto rozhraní k nastavení aktuálního aktivního balíčku VSPackage. | Ovládací prvek zdroje VSPackage | Požaduje se |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Toto rozhraní je založeno na modelu předplatného. Jakýkoli VSPackage může signalizovat, že chce přijímat události dokumentu a být upozorněnprostředí na události, které se chystáte stát. Je implementován [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]a zpracován a bude provádět `IVsTrackProjectDocumentsEvents2` události , které zase předají události implementující do balíčku VSPackage. | Se zakázaným inzerováním správy zdrojového kódu | Požaduje se |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Toto rozhraní poskytuje dávkové zpracování, synchronizované operace `OnQueryAddFiles` čtení a zápisu a pokročilou metodu. | Se zakázaným inzerováním správy zdrojového kódu | Požaduje se |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Průzkumník řešení** a projekty volají toto rozhraní při přidání nových souborů do projektů nebo při přejmenování nebo odstranění souborů a složek z projektů. Zdrojový ovládací prvek VSPackage můžete rezervovat soubor projektu nebo zrušit operaci. | Ovládací prvek zdroje VSPackage | Doporučené |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Průzkumník řešení** a projekty volání tohoto rozhraní v reakci na volání metody IVstrackProjectDocuments3 rozhraní. Zdrojové ovládací prvek VSPackage můžete sledovat dávkové operace, synchronizované operace `OnQueryAddFiles` čtení a zápisu a pracovat s pokročilejší metodou. | Ovládací prvek zdroje VSPackage | Doporučené |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Toto rozhraní poskytuje podporu správy zařazení webových projektů. | Ovládací prvek zdroje VSPackage | Doporučené |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Toto rozhraní se používá k načtení popisků pro soubory řízené zdrojem v projektech. | Ovládací prvek zdroje VSPackage | Nepovinné |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Toto rozhraní poskytuje podporu rozšíření oboru názvů. | Ovládací prvek zdroje VSPackage | Nepovinné |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | VSPackage používá toto rozhraní k integraci rozšíření oboru názvů do dialogových oken **Nový**, **Otevřít**nebo **Uložit.** V důsledku toho lze projekty automaticky přidat do správy zdrojového kódu při vytváření nebo přidat do správy zdrojového kódu, když je operace uložení v platnosti. | Ovládací prvek zdroje VSPackage | Nepovinné |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | VSPackage používá toto rozhraní k definování dalších glyfů jako glyfů správy zdrojového kódu pro uzly v **Průzkumníku řešení**. | Ovládací prvek zdroje VSPackage | Nepovinné |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Dialogové okno **Přidat** pro webové projekty používá toto rozhraní. Poskytuje metody pro procházení umístění správy zdrojového kódu a pro otevření webového projektu, který byl dříve přidán do úložiště správy zdrojového kódu v tomto umístění. | Ovládací prvek zdroje VSPackage | Doporučené |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Toto rozhraní poskytuje podporu pro asynchronní (pozadí) načítání projektů ze správy zdrojového kódu. | Ovládací prvek zdroje VSPackage | Nepovinné |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Toto rozhraní umožňuje projektům sledovat průběh asynchronnínačítání iniciované <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>. | Project | Nepovinné |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Toto rozhraní umožňuje ide dotaz aktivní zdrojového ovládacího prvku VSPackage. IDE dotazuje hodnotu nastavení správy zdrojového kódu, které mají význam i v případě, že neexistuje žádný aktivní zdrojový prvek VSPackage registrovány. Toto rozhraní je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]implementováno a zpracováno společností . | Se zakázaným inzerováním správy zdrojového kódu | Požaduje se |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Toto rozhraní se používá při registraci správy zdrojového kódu VSPackage. | Se zakázaným inzerováním správy zdrojového kódu | Požaduje se |
| <xref:EnvDTE.SourceControl> | Toto rozhraní se používá v automatizaci. Jako takové zpřístupňuje pouze funkce, které lze spustit bez zobrazení libovolného ui. | Ovládací prvek zdroje VSPackage | Nepovinné |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Toto rozhraní slouží k uložení nastavení správy zdrojového kódu v souboru řešení (.sln). Nastavení zahrnují umístění správy zdrojového kódu a příznaky stavu správy zdrojového kódu. | Ovládací prvek zdroje VSPackage | Doporučené |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Toto rozhraní slouží k uložení nastavení správy zdrojového kódu v souboru možností řešení (.suo). To může zahrnovat nastavení správy zdrojového kódu specifické pro uživatele, jako je například umístění zařazení aktuálního uživatele. | Ovládací prvek zdroje VSPackage | Doporučené |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Toto rozhraní se používá ke sledování událostí za účelem provádění operací, jako je například vrácení souborů projektu před zavřením řešení nebo získání nových souborů ze správy zdrojového kódu při otevírání projektu. | Ovládací prvek zdroje VSPackage | Doporučené |

## <a name="see-also"></a>Viz také
- [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)
