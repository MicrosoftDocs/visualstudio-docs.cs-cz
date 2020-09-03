---
title: Struktura VSPackage (Správa zdrojového kódu) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08bb0a296daca0de1c02b905a75fb10ce05f254e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205999"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura balíčku VSPackage (balíček VSPackage správy zdrojového kódu)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sada SDK pro správu zdrojového kódu poskytuje pokyny pro vytvoření balíčku VSPackage, který umožňuje implementátoru správy zdrojového kódu integrovat své funkce správy zdrojového kódu do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí. VSPackage je komponenta modelu COM, která je obvykle načtena na vyžádání [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaným vývojovým prostředím (IDE) na základě služeb, které jsou inzerovány balíčkem v položkách registru. Každý VSPackage musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . VSPackage obvykle spotřebovává služby nabízené [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozhraním IDE a proffers některé služby.  
  
 VSPackage deklaruje své položky nabídky a vytvoří výchozí stav položky prostřednictvím souboru. vsct. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Rozhraní IDE zobrazí položky nabídky v tomto stavu, dokud není načteno VSPackage. Následně je implementována implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody VSPackage pro povolení nebo zakázání položek nabídky.  
  
## <a name="source-control-package-characteristics"></a>Charakteristiky balíčku zdrojového kódu  
 Balíček VSPackage správy zdrojového kódu je hluboko integrovaný do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Sémantika VSPackage zahrnuje:  
  
- Rozhraní, které má být implementováno na základě toho, že je VSPackage ( `IVsPackage` rozhraní)  
  
- Implementace příkazu uživatelského rozhraní (soubor. vsct a implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní)  
  
- Registrace VSPackage pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
  Prvek VSPackage správy zdrojového kódu musí komunikovat s těmito dalšími [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entitami:  
  
- Projekty  
  
- Editory  
  
- Řešení  
  
- Windows  
  
- Spuštěná tabulka dokumentů  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Služby prostředí Visual Studio, které mohou být spotřebovány  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Služba SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Implementovaná a volaná rozhraní VSIP  
 Balíček správy zdrojového kódu je VSPackage, a proto může komunikovat přímo s jinými prvky VSPackage, které jsou zaregistrovány v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Aby bylo možné zajistit plnou škálu funkcí správy zdrojového kódu, může VSPackage správy zdrojového kódu pracovat s rozhraními poskytovanými projekty nebo prostředím.  
  
 Každý projekt v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] musí implementovat rozhraní, které se má <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> rozpoznat jako projekt v rámci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí (IDE). Toto rozhraní však není pro správu zdrojového kódu dostatečně specializované. Projekty, které mají být pod správou zdrojových kódů, implementují <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Toto rozhraní používá VSPackage správy zdrojového kódu k dotazování projektu na jeho obsah a k poskytnutí glyfů a informací o vazbě (informace potřebné k navázání spojení mezi umístěním serveru a umístěním disku projektu, který se nachází pod správou zdrojových kódů).  
  
 Rozhraní VSPackage správy zdrojového kódu implementuje rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , které zase umožňuje projektům zaregistrovat se pro správu zdrojového kódu a načíst jejich glyfy stavu.  
  
 Úplný seznam rozhraní, které musí VSPackage správy zdrojového kódu zvážit, najdete v tématu [související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Viz také  
 [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
