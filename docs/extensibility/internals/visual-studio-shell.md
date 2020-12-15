---
title: Prostředí sady Visual Studio | Microsoft Docs
description: Prostředí sady Visual Studio je primárním agentem integrace v aplikaci Visual Studio a poskytuje základní funkce a podporuje křížovou komunikaci mezi VSPackage.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 546a76d1533efaef28ddafb14b04514f64e9d4f9
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488047"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Prostředí je primárním agentem integrace v nástroji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Prostředí poskytuje potřebné funkce, které umožňuje VSPackage sdílet běžné služby. Vzhledem k tomu, že cílem architektury [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je vytvořit primární funkce v rozhraních VSPackage, je prostředí rozhraní, které poskytuje základní funkce a podporuje křížovou komunikaci mezi svými VSPackage komponent.

## <a name="shell-responsibilities"></a>Odpovědnosti prostředí
 Prostředí má následující klíčové zodpovědnosti:

- Podpora (prostřednictvím rozhraní COM) základní prvky uživatelského rozhraní (UI). Mezi ně patří výchozí nabídky a panely nástrojů, rámečky oken dokumentů nebo podřízená okna rozhraní MDI (multi-Document Interface) a rámce okna nástrojů a podpora dokování.

- Údržba běžícího seznamu všech aktuálně otevřených dokumentů v běžící tabulce dokumentů (RDT), aby bylo možné koordinovat persistenci dokumentů a zaručit, že jeden dokument nelze otevřít více než jedním způsobem nebo nekompatibilním způsobem.

- Podpora rozhraní příkazového řádku a příkazu pro zpracování příkazů `IOleCommandTarget` .

- Načítají se VSPackage v odpovídajících časech. Pro zlepšení výkonu prostředí se vyžaduje zpoždění načítání VSPackage.

- Správa některých sdílených služeb, jako například <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> , které poskytují základní funkce prostředí a <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> které poskytují základní funkce okna.

- Správa souborů řešení (. sln). Řešení obsahují skupiny souvisejících projektů, podobně jako soubory pracovního prostoru (. DSW) v Visual C++ 6,0.

- Sledování výběru, kontextu a měny v rámci prostředí. Prostředí sleduje následující typy položek:

  - Aktuální projekt

  - Aktuální položka projektu nebo ItemID aktuální <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Aktuální výběr pro okno **vlastnosti** nebo `SelectionContainer`

  - Identifikátory kontextu uživatelského rozhraní nebo CmdUIGuids, které ovládají viditelnost příkazů, nabídek a panelů nástrojů

  - Aktuálně aktivní prvky, jako je aktivní okno, dokument a správce vrácení

  - Atributy kontextu uživatele, které zajišťují dynamickou pořídit

  Prostředí také napravuje komunikaci mezi nainstalovanými VSPackage a aktuálními službami. Podporuje základní funkce prostředí a zpřístupňuje je všem rozhraním VSPackage integrovaným v nástroji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Tyto základní funkce obsahují následující položky:

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

- **Sada nástrojů**

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)
