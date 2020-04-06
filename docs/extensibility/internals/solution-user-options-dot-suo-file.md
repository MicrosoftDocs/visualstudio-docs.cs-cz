---
title: Možnosti uživatele řešení (. Suo) Spis | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705320"
---
# <a name="solution-user-options-suo-file"></a>Soubor uživatelských možností řešení (.Suo)
Soubor uživatelských možností řešení (.suo) obsahuje možnosti řešení pro jednotlivé uživatele. Tento soubor by neměl být se změnami pro správě zdrojového kódu.

 Soubor uživatelských možností řešení (.suo) je strukturované úložiště nebo složený soubor uložený v binárním formátu. Informace o uživateli uložíte do datových proudů s názvem datového proudu, který bude použit k identifikaci informací v souboru .suo. Soubor uživatelských možností řešení se používá k ukládání nastavení uživatelských předvoleb a je vytvořen automaticky, když Visual Studio uloží řešení.

 Když prostředí otevře soubor .suo, vyjmenovává všechny aktuálně načtené balíčky VSPackages. Pokud VSPackage implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> rozhraní, pak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> prostředí volá metodu na VSPackage s žádostí o načtení všech svých dat ze souboru .suo.

 Je odpovědností VSPackage vědět, jaké datové proudy může mít zapsány do souboru .suo. Pro každý datový proud, který napsal, VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> volá zpět do prostředí prostřednictvím načíst konkrétní datový proud, který je identifikován klíč, což je název datového proudu. Prostředí pak volá zpět do VSPackage číst tento konkrétní datový proud `IStream` předávání <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> název datového proudu a ukazatel na metodu.

 V tomto okamžiku je provedeno `LoadUserOptions` další volání, aby se zjistilo, zda existuje další část souboru .suo, který musí být přečten. Tento proces pokračuje, dokud všechny datové proudy v souboru .suo byly přečteny a zpracovány prostředím.

 Při uložení nebo zavření řešení prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> volá metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> s ukazatelem na metodu. Binární `IStream` informace, které mají být uloženy, jsou předány <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> metodě, která pak zapíše `SaveUserOptions` informace do souboru .suo a znovu zavolá metodu, aby zjistila, zda existuje jiný proud informací pro zápis do souboru .suo.

 Tyto dvě `SaveUserOptions` metody `WriteUserOptions`a , se nazývají rekurzivně pro každý proud informací, které mají být `IVsSolutionPersistence`uloženy do souboru .suo, předávání v ukazatel na . Nazývají se rekurzivně, aby bylo možné do souboru .suo psát více datových proudů. Tímto způsobem informace o uživateli jsou trvalé s řešením a je zaručeno, že tam bude při příštím otevření řešení.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Řešení](../../extensibility/internals/solutions-overview.md)
