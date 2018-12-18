---
title: Možnosti uživatele řešení (. Soubor suo) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b96e3ad2ec29402dddc7354df46293b99bac3ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130844"
---
# <a name="solution-user-options-suo-file"></a>Možnosti uživatele řešení (. Soubor suo)
Soubor řešení uživatelské možnosti (.suo) obsahuje možnosti řešení na uživatele. Tento soubor by neměl být vráceny se změnami do správy zdrojového kódu.  
  
 Soubor řešení uživatelské možnosti (.suo) je strukturovaných úložiště, nebo složené souborů ukládají v binárním formátu. S názvem datového proudu se klíč, který se použije k identifikaci informace v souboru .suo uložit informace o uživateli do datových proudů. Soubor možností řešení uživatele se používá k ukládání nastavení předvoleb uživatele a je vytvořena automaticky při uloží řešení sady Visual Studio.  
  
 Když prostředí otevře soubor .suo, vytvoří výčet všech aktuálně načtených VSPackages. Pokud VSPackage implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> rozhraní a pak volání prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> metodu VSPackage žádostí ji načíst všechna data ze souboru .suo.  
  
 Je zodpovědností VSPackage vědět, co datové proudy může mít zapisují do souboru .suo. Pro každý datový proud, který ho napsal, zavolá VSPackage zpět do prostředí prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> načíst konkrétní datový proud, který je určený podle klíč, který je název datového proudu. Prostředí poté zavolá zpátky do VSPackage ke čtení tohoto konkrétního datového proudu předání názvu datového proudu a `IStream` ukazatel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metoda.  
  
 V tomto bodě jiné Přišla žádost o `LoadUserOptions` jestli je jinou část .suo souboru, který má být číst. Tento proces pokračuje, dokud všechny datové proudy v souboru .suo čtení a zpracovává prostředí.  
  
 Když je řešení uložené nebo zavřená, volání prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> metoda s ukazatelem <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> metoda. `IStream` Předaný obsahující binární informace uložit <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> metodu, která pak zapisuje informace do souboru .suo a volání `SaveUserOptions` metoda znovu a zjistit, jestli jiného datového proudu informace k zápisu do .suo soubor.  
  
 Tyto dvě metody `SaveUserOptions` a `WriteUserOptions`, se nazývají rekurzivně pro každý datový proud informace uložit soubor .suo, předávání v má ukazatel na `IVsSolutionPersistence`. Označují se jako rekurzivní umožňující zápis víc datových proudů do souboru .suo. Informace o uživateli v tímto způsobem je zachovat pomocí řešení a záruku, že existovat dalším otevření řešení.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Řešení](../../extensibility/internals/solutions.md)