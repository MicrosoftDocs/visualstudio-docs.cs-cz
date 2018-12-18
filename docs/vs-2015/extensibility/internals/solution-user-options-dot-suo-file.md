---
title: Uživatelské možnosti řešení (. Soubor suo) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f101f4efe0afe2132477b83731871872fdfc90c9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799844"
---
# <a name="solution-user-options-suo-file"></a>Soubor uživatelských možností řešení (.Suo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Soubor řešení uživatelské možnosti (.suo) obsahuje možnosti řešení pro jednotlivé uživatele. Tento soubor by neměl být vráceny se změnami do správy zdrojového kódu.  
  
 Soubor řešení uživatelské možnosti (.suo) je strukturovaného úložiště, nebo složeného souboru uloženého v binárním formátu. Uložit informace o uživateli do datových proudů s názvem se klíč, který se použije k identifikaci informace v souboru .suo datového proudu. Souboru s možností uživatele řešení se používá k ukládání uživatelských předvoleb nastavení a je vytvořen automaticky při ukládání řešení sady Visual Studio.  
  
 Když prostředí otevře soubor .suo, vypíše všechny aktuálně načtené rozšíření VSPackages. Pokud VSPackage implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> rozhraní a pak volá prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> metodu na VSPackage žádáte ji načíst všechna data ze souboru .suo.  
  
 To je pravděpodobně jste napsali sady VSPackage odpovědnost vědět, co datových proudů do souboru .suo. Pro každý datový proud, který ho napsal, sady VSPackage zavolá zpět do prostředí prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> načíst konkrétní datového proudu, který je identifikován podle klíče, což je název datového proudu. Prostředí pak zavolá zpět do sady VSPackage ke čtení tohoto streamu název datového proudu a `IStream` ukazatel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metoda.  
  
 V tomto okamžiku je provedeno volání jiného `LoadUserOptions` jestli je jiné části souboru .suo, který má ke čtení. Tento proces pokračuje, dokud všechny datové proudy v souboru .suo číst a zpracovat prostředí.  
  
 Když je řešení uložit nebo closed, volání prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> metoda s ukazatelem na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> metody. `IStream` Obsahující binární informace o ukládání je předán <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> metodu, která pak zapisuje tyto informace do souboru .suo a volání `SaveUserOptions` metoda znovu, abyste viděli, pokud je jiný datový proud informací má být zapsáno .suo soubor.  
  
 Tyto dvě metody `SaveUserOptions` a `WriteUserOptions`, se nazývají rekurzivně pro každý datový proud informací, které mají být uloženy do souboru .suo, předejte ukazatel na `IVsSolutionPersistence`. Nazývají se rekurzivně povolit pro zápis různých datových proudů do souboru .suo. Tímto způsobem se informace o uživateli s řešením je trvalá a je zaručeno, že tam mají být při příštím otevření řešení.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Řešení](../../extensibility/internals/solutions.md)

