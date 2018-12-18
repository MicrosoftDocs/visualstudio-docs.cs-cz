---
title: Prostředí sady Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0ef0bf2811e9858925398637e835be8684c7f9ef
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928942"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Prostředí je primární agenta integrace v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Prostředí obsahuje potřebné funkce, které umožňují rozšíření VSPackages sdílení společných služeb. Protože architektury cílem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je vzor průmyslovému primární funkce v balíčcích VSPackage, prostředí je rámec, který poskytuje základní funkce a podporují různé komunikaci mezi komponenty rozšíření VSPackages.  
  
## <a name="shell-responsibilities"></a>Odpovědnosti prostředí  
 Prostředí má následující klíčové odpovědnosti:  
  
- Podpora (prostřednictvím rozhraní modelu COM) základní prvky uživatelského rozhraní (UI). Patří mezi ně výchozí nabídky a panely nástrojů, okna rámce dokumentu nebo podřízená okna rozhraní více dokumentů (MDI) a rámce okna nástrojů a podporu dokování.  
  
- Zachování seznam všechny aktuálně otevřené dokumenty v tabulce spuštěných dokumentů (r...) za účelem koordinace trvalost dokumenty a zaručuje, že daný jeden dokument nelze otevřít více než jedním způsobem, nebo nekompatibilní způsoby.  
  
- Podpora rozhraní směrování příkazů a zpracování příkazu `IOleCommandTarget`.  
  
- Načítání rozšíření VSPackages ve vhodných chvílích. Zpoždění načítání VSPackage je nezbytné ke zlepšení výkonu prostředí.  
  
- Správa určité sdílené služby, jako například <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, která poskytuje funkce pro základní prostředí, a <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, který poskytuje základní oddílová funkce.  
  
- Správa souborů řešení (.sln). Řešení obsahují skupiny souvisejících projektů, podobně jako soubory pracovního prostoru (.dsw) v aplikaci Visual C++ 6.0.  
  
- Sledování prostředí celý výběr, kontextu a měny. Prostředí sleduje následující typy položek:  
  
  -   Aktuální projekt  
  
  -   Aktuální položku projektu nebo ID aktuální položky <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
  -   Aktuální výběr **vlastnosti** okno nebo `SelectionContainer`  
  
  -   Kontextu uživatelského rozhraní ID nebo CmdUIGuids, které řídí, zda se příkazy, nabídky a panely nástrojů  
  
  -   Aktuálně aktivní prvky, jako jsou aktivní okno, dokument a vhodný  
  
  -   Atributy kontextu uživatele, které řídí, dynamická Nápověda  
  
  Prostředí také zprostředkovává komunikaci mezi nainstalovaných rozšíření VSPackages a službami. Podporuje základní funkce prostředí a je zpřístupní pro všechny balíčky VSPackages integrováno v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Tyto základní funkce zahrnují následující položky:  
  
- **O** dialogové okno pole a na úvodní obrazovce  
  
- **Přidat nový a přidat existující položku** dialogová okna  
  
- **Zobrazení tříd** okno a **prohlížeče objektů**  
  
- **Odkazy na** dialogové okno  
  
- **Osnova dokumentu** okna  
  
- **Dynamická nápověda** okna  
  
- **Najít** a **nahradit**  
  
- **Otevřete projekt** a **otevřít soubor** dialogová okna na **nový** nabídky  
  
- **Možnosti** dialogové okno na **nástroje** nabídky  
  
- **Vlastnosti** okna  
  
- **Průzkumník řešení**  
  
- **Seznam úkolů** okna  
  
- **Panel nástrojů**  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [Balíčky VSPackage](../../extensibility/internals/vspackages.md)