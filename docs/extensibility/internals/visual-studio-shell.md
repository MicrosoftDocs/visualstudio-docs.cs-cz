---
title: Prostředí sady Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60aa48da701857508f9b6fd7fc3d9d0c0603046e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722058"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Prostředí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je primárním agentem integrace v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Prostředí poskytuje potřebné funkce, které umožňuje VSPackage sdílet běžné služby. Vzhledem k tomu, že cílem architektury [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je vytvořit na VSPackage primární funkce, prostředí je rámec, který poskytuje základní funkce a podporuje křížovou komunikaci mezi svými VSPackage komponent.

## <a name="shell-responsibilities"></a>Odpovědnosti prostředí
 Prostředí má následující klíčové zodpovědnosti:

- Podpora (prostřednictvím rozhraní COM) základní prvky uživatelského rozhraní (UI). Mezi ně patří výchozí nabídky a panely nástrojů, rámečky oken dokumentů nebo podřízená okna rozhraní MDI (multi-Document Interface) a rámce okna nástrojů a podpora dokování.

- Údržba běžícího seznamu všech aktuálně otevřených dokumentů v běžící tabulce dokumentů (RDT), aby bylo možné koordinovat persistenci dokumentů a zaručit, že jeden dokument nelze otevřít více než jedním způsobem nebo nekompatibilním způsobem.

- Podpora rozhraní příkazového řádku a modulu pro zpracování příkazů `IOleCommandTarget`.

- Načítají se VSPackage v odpovídajících časech. Pro zlepšení výkonu prostředí se vyžaduje zpoždění načítání VSPackage.

- Správa některých sdílených služeb, jako je například <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, které poskytují základní funkce prostředí a <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, která poskytuje základní funkce okna.

- Správa souborů řešení (. sln). Řešení obsahují skupiny souvisejících projektů, podobně jako soubory pracovního prostoru (. DSW) v jazyce C++ Visual 6,0.

- Sledování výběru, kontextu a měny v rámci prostředí. Prostředí sleduje následující typy položek:

  - Aktuální projekt

  - Aktuální položka projektu nebo ItemID aktuální <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Aktuální výběr pro okno **vlastnosti** nebo `SelectionContainer`

  - Identifikátory kontextu uživatelského rozhraní nebo CmdUIGuids, které ovládají viditelnost příkazů, nabídek a panelů nástrojů

  - Aktuálně aktivní prvky, jako je aktivní okno, dokument a správce vrácení

  - Atributy kontextu uživatele, které zajišťují dynamickou pořídit

  Prostředí také napravuje komunikaci mezi nainstalovanými VSPackage a aktuálními službami. Podporuje základní funkce prostředí a zpřístupňuje je všem rozhraním VSPackage integrovaným v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Tyto základní funkce obsahují následující položky:

- **Dialogová** okna a úvodní obrazovka

- Dialogová okna **Přidat nové a přidat existující položky**

- **Zobrazení tříd** okno a **Prohlížeč objektů**

- **Odkazy** – dialogové okno

- Okno **Osnova dokumentu**

- **Dynamické okno Help**

- **Najít** a **nahradit**

- Otevře dialogová okna **Otevřít projekt** a **otevřít soubor** v nabídce **Nový** .

- Dialogové okno **Možnosti** v nabídce **nástroje**

- Okno **vlastností**

- **Průzkumník řešení**

- **Seznam úkolů** okno

- **Panel nástrojů**

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)