---
title: Přehled řešení | Dokumentace Microsoftu
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
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d9eb36da433575710ae7f24da85e4a1a0970b79
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781059"
---
# <a name="solutions-overview"></a>Přehled řešení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Řešení je seskupení jednoho nebo více projektů, které vzájemně spolupracují na vytvoření aplikace. Projekt a stavové informace týkající se řešení jsou uloženy ve dvou souborech jiné řešení. Soubor řešení (.sln) je založený na textu a můžete umístit pod správou zdrojového kódu a sdílet mezi uživateli. Soubor řešení uživatelské možnosti (.suo) je binární. Soubor .suo v důsledku toho nemůže být umístěn pod správou zdrojového kódu a obsahuje informace specifické pro uživatele.  
  
 Žádné VSPackage lze zapisovat do obou typů souborů řešení. Vzhledem k povaze soubory existují dvě různá rozhraní implementována pro zápis do nich. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Rozhraní textové informace zapisuje do souboru .sln a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> rozhraní zapíše do souboru .suo binární datové proudy.  
  
> [!NOTE]
>  Projekt není nutné explicitně zápis záznamu pro samotné do souboru řešení. prostředí, která zpracovává pro projekt. Proto pokud chcete přidat další obsah konkrétně do souboru řešení, není potřeba registrovat vašeho balíčku VSPackage tímto způsobem.  
  
 Každý VSPackage podpora trvalosti řešení používá tři rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> rozhraní, které je implementované prostředí a volané sady VSPackage, a `IVsPersistSolutionProps` a `IVsPersistSolutionOpts`, které jsou obě implementované sady VSPackage. `IVsPersistSolutionOpts` Rozhraní pouze musí implementovat, pokud má být sady VSPackage zapsaného do souboru .suo soukromé informace.  
  
 Po otevření řešení následující proces probíhá.  
  
1. Prostředí přečte řešení.  
  
2. Pokud najde prostředí `CLSID`, načte odpovídající VSPackage.  
  
3. Pokud je VSPackage načteny, volání prostředí `QueryInterface` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> rozhraní pro rozhraní, které vyžaduje sady VSPackage.  
  
   1.  Při čtení ze souboru .sln, prostředí volá `QueryInterface` pro `IVsPersistSolutionProps`.  
  
   2.  Při čtení ze souboru .suo, prostředí volá `QueryInterface` pro `IVsPersistSolutionOpts`.  
  
   Konkrétní informace týkající se použití těchto souborů můžete najít v [řešení (. SLN) soubor](../../extensibility/internals/solution-dot-sln-file.md) a [uživatelské možnosti řešení (. Soubor suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Pokud chcete vytvořit novou konfiguraci řešení skládající se z konfigurace dva projekty a vyloučení třetí ze sestavení, budete muset použít uživatelské rozhraní vlastností stránky nebo služby automation. Správce konfigurace sestavení řešení a jejich vlastnosti nelze změnit přímo, ale můžete pracovat s použitím správci sestavení řešení `SolutionBuild` třídy z DTE v modelu automatizace. Další informace o konfiguraci řešení najdete v tématu [konfigurace řešení](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>

