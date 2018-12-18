---
title: Struktura balíčku VSPackage (řízení zdrojového balíčku VSPackage) | Dokumentace Microsoftu
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
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6eaad545d1c1b3fe96ecbad3a88cc7636b777a54
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737983"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura balíčku VSPackage (balíček VSPackage správy zdrojového kódu)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zdrojový ovládací prvek balíčku SDK poskytuje pokyny pro vytvoření VSPackage, která umožňují zdrojového ovládacího prvku implementátorovi integrovat své funkce správy zdrojového kódu s [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí. VSPackage je komponenta modelu COM, který je obvykle načtena na vyžádání pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE) podle služby, které mají být inzerovány balíček v jeho položky registru. Každý VSPackage musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. VSPackage obvykle využívá služeb, které [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí a proffers některých služeb.  
  
 VSPackage deklaruje jeho položky nabídky a vytvoří výchozí položku Stav prostřednictvím souboru .vsct. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrovaného vývojového prostředí zobrazovat položky nabídky v tomto stavu, dokud se načte sady VSPackage. Následně sady VSPackage provádění <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda je volána k povolení nebo zakázání položky nabídky.  
  
## <a name="source-control-package-characteristics"></a>Vlastnosti balíčku zdrojového ovládacího prvku  
 Ovládací prvek zdroje balíčku VSPackage se úzce integruje do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Sémantika VSPackage patří:  
  
- Rozhraní k implementaci tím, že se VSPackage ( `IVsPackage` rozhraní)  
  
- Implementace příkazu uživatelského rozhraní (.vsct souborů a provádění <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní)  
  
- Registrace balíčku VSPackage pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
  Ovládací prvek zdroje balíčku VSPackage musí komunikovat s těmito jiné [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entity:  
  
- Projekty  
  
- Editory  
  
- Řešení  
  
- Windows  
  
- Spuštění tabulky dokumentů  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Prostředí služby Visual Studio, které mohou být využívány  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider služby  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Rozhraní VSIP implementovat a s názvem  
 Zdrojový ovládací prvek balíček je VSPackage, a proto mohou komunikovat přímo s další rozšíření VSPackages, který je registrovaný pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Pokud chcete zajistit plnou škálu funkce správy zdrojového kódu, můžete řešení správy zdrojového kódu VSPackage s rozhraním poskytovaným tímto systémem projektů nebo prostředí.  
  
 Každý projekt v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Chcete-li rozpoznán jako projekt v rámci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí. Však není toto rozhraní specializované dostatečná pro správu zdrojového kódu. Implementace řídit projekty, které se očekává, že se v části zdroj <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Toto rozhraní je používán ovládací prvek zdroje balíčku VSPackage dotazy projekt pro jeho obsah a poskytnout ho glyfy a informace o vazbě (informace potřebné k navázání připojení mezi umístěním serveru a na místo na disku, který je v rámci projektu správy zdrojového kódu).  
  
 Ovládací prvek zdroje balíčku VSPackage implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, který zase umožňuje zaregistrovat pro správu zdrojového kódu a jejich stav glyfy načítat projekty.  
  
 Úplný seznam rozhraní, které musíte zvážit balíčku VSPackage správy zdrojového kódu, naleznete v tématu [související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Viz také  
 [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

