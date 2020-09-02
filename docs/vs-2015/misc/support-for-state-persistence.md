---
title: Podpora pro trvalost stavu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434316"
---
# <a name="support-for-state-persistence"></a>Podpora pro trvalost stavu
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] může udržovat stav běžných objektů. Například vlastnosti řešení a projektu jsou uloženy do a obnoveny z řešení a souborů projektu. Uživatelská nastavení se dají exportovat do souborů nastavení a naimportovat z nich.  
  
 Sady VSPackage obvykle spoléhají na místní úložiště, a to buď v registru systému, nebo ve složce Application data pro aktuálního uživatele nebo počítač. Hodnoty, které vyžadují malé množství prostoru pro úložiště, například celá čísla a řetězce, jsou obvykle uloženy v registru systému. Hodnoty, které vyžadují velké množství prostoru pro úložiště, například bitmapy, se ukládají do souboru. Cestu k souboru lze uložit do systémového registru. Mechanismus trvalosti musí mít oprávnění pro přístup k místnímu úložišti.  
  
## <a name="support-for-locating-local-storage"></a>Podpora pro vyhledání místního úložiště  
 <xref:Microsoft.VisualStudio.Shell.Package>Třída poskytuje podporu pro vyhledání informací o stavu v registru systému nebo ve složce Application data pro aktuálního uživatele nebo počítač.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Vrátí cestu k kořenovému adresáři registru místního počítače, například [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0Exp.  
  
 Z této služby se získá kořen místního registru <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> . Pokud není k dispozici, získá se z <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> atributu VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Vrátí cestu k kořenovému adresáři registru aktuálního uživatele (na počítači), například [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0Exp.  
  
 Z této služby se získá kořen místního registru <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> . Pokud není k dispozici, získá se z atributu DefaultLocalRegistryRoot sady VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Vrátí cestu k adresáři, který slouží jako společné úložiště pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] data aktuálního cestovního uživatele, například C:\Documents and Settings \\ *YourAccountName*\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Vrátí cestu k adresáři, který slouží jako společné úložiště pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] data pro aktuálního neroamingového uživatele, například C:\Documents and Settings \\ *YourAccountName*\Local Settings\Application Data\Microsoft\VisualStudio\8.0Exp..  
  
## <a name="see-also"></a>Viz také  
 [Stav VSPackage](../misc/vspackage-state.md)