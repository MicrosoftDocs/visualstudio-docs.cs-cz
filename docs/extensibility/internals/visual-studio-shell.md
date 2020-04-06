---
title: Prostředí Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704006"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Prostředí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je primárním původcem integrace v . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Prostředí poskytuje nezbytné funkce, které umožňují VSPackages sdílet běžné služby. Vzhledem k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tomu, že cílem architektury je převést primární funkce v VSPackages, prostředí je rámec pro poskytování základních funkcí a podporu křížové komunikace mezi jeho součástí VSPackages.

## <a name="shell-responsibilities"></a>Shell odpovědnosti
 Prostředí má následující klíčové povinnosti:

- Podpora (prostřednictvím rozhraní COM) základní prvky uživatelského rozhraní (UI). Patří mezi ně výchozí nabídky a panely nástrojů, rámečky oken dokumentu nebo podřízená okna rozhraní mdi (multi-document) a rámečky oken nástrojů a podpora ukotvení.

- Udržování spuštěného seznamu všech aktuálně otevřených dokumentů v běžící tabulce dokumentů (RDT) za účelem koordinace trvalosti dokumentů a zajištění toho, že jeden dokument nelze otevřít více než jedním způsobem nebo nekompatibilními způsoby.

- Podpora rozhraní pro směrování příkazů a `IOleCommandTarget`zpracování příkazů .

- Načítání VSPackages ve vhodných časech. Zpoždění načítání VSPackage je nezbytné ke zlepšení výkonu prostředí.

- Správa některých sdílených <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>služeb, například , <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>která poskytuje základní funkce prostředí a , která poskytuje základní funkce okna.

- Správa souborů řešení (.sln). Řešení obsahují skupiny souvisejících projektů, podobně jako soubory pracovního prostoru (.dsw) v jazyce Visual C++ 6.0.

- Sledování výběru celého prostředí, kontextu a měny. Skořepina sleduje následující typy položek:

  - Aktuální projekt

  - Aktuální položka projektu nebo ItemID aktuální<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Aktuální výběr okna **Vlastnosti** nebo`SelectionContainer`

  - ID kontextu uživatelského rozhraní nebo identifikátory CmdUIGuid, které řídí viditelnost příkazů, nabídek a panelů nástrojů

  - Aktuálně aktivní prvky, jako je aktivní okno, dokument a správce zpět

  - Atributy Kontextu uživatele, které pohánějí dynamickou nápovědu

  Prostředí také zprostředkuje komunikaci mezi nainstalovanými Balíčky VSPackages a aktuálními službami. Podporuje základní funkce prostředí a zpřístupňuje je všem VSPackages integrovaným v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Mezi základní funkce patří následující položky:

- Dialogové okno **A** úvodní obrazovka

- **Dialogové okna Přidat novou a Přidat existující položku**

- **Okno Zobrazení tříd a** **prohlížeč objektů**

- Dialogové okno **Odkazy**

- Okno **Osnova dokumentu**

- **Okno dynamické nápovědy**

- **Najít** a **nahradit**

- **Otevření** dialogových oken Projekt a **Otevřít soubor** v nabídce **Nový**

- Dialogové okno **Volby** v nabídce **Nástroje**

- **Okno Vlastnosti**

- **Průzkumník řešení**

- **Okno Seznam úkolů**

- **Sada nástrojů**

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)
