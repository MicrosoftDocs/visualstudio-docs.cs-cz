---
title: Možnosti uživatele řešení (. Suo) soubor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723803"
---
# <a name="solution-user-options-suo-file"></a>Soubor uživatelských možností řešení (.Suo)
Soubor možností uživatele řešení (. suo) obsahuje možnosti řešení pro jednotlivé uživatele. Tento soubor by neměl být vrácen se změnami do správy zdrojového kódu.

 Soubor možností uživatele řešení (. suo) je strukturované úložiště nebo složený soubor uložený v binárním formátu. Informace o uživateli ukládáte do datových proudů s názvem datového proudu, který je klíčem, který bude použit k identifikaci informací v souboru. suo. Soubor možností uživatele řešení se používá k uložení nastavení uživatelských předvoleb a automaticky se vytvoří, když Visual Studio uloží řešení.

 Když prostředí otevře soubor. suo, vytvoří výčet všech aktuálně načtených VSPackage. Pokud VSPackage implementuje rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>, pak prostředí zavolá metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> v rozhraní VSPackage, která o ni žádá, aby načetla všechna jeho data ze souboru. suo.

 Je zodpovědností VSPackage, jak zjistit, které datové proudy mohly být zapsány do souboru. suo. Pro každý datový proud, který napsal, rozhraní VSPackage volá do prostředí prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> pro načtení konkrétního datového proudu, který je identifikován klíčem, což je název datového proudu. Prostředí pak zavolá zpět do VSPackage a přečte tento konkrétní proud, který předává název datového proudu a `IStream` ukazatel na metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>.

 V tomto okamžiku je k `LoadUserOptions` k dispozici jiné volání, aby bylo možné zjistit, zda existuje jiný oddíl souboru. suo, který je nutné číst. Tento proces pokračuje, dokud nebudou všechny datové proudy v souboru. suo načteny a zpracovány prostředím.

 Když je řešení uloženo nebo zavřeno, prostředí volá metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> s ukazatelem na metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>. @No__t_0 obsahující binární informace, které mají být uloženy, jsou předány metodě <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>, která pak zapisuje informace do souboru. suo a znovu volá metodu `SaveUserOptions`, aby bylo možné zjistit, zda je k zápisu do souboru. suo k dispozici jiný proud informací.

 Tyto dvě metody, `SaveUserOptions` a `WriteUserOptions`, se nazývají rekurzivní pro každý datový proud informací, které mají být uloženy do souboru. suo a předávají ukazatel na `IVsSolutionPersistence`. Jsou volány rekurzivně, aby umožňovaly zápis více datových proudů do souboru. suo. V takovém případě jsou informace o uživateli trvale uložené v řešení a při příštím otevření řešení je zaručeno, že bude k dispozici.

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Řešení](../../extensibility/internals/solutions-overview.md)