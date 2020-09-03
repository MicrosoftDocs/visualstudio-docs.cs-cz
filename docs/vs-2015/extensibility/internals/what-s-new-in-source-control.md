---
title: Co je nového ve správě zdrojového kódu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200953"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Co&#39;s je nového ve správě zdrojového kódu v aplikaci Visual Studio 2015

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V nástroji [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] můžete poskytnout hluboko integrované řešení správy zdrojového kódu implementací balíčku pro správu zdrojového kódu. Tato část popisuje funkce balíčku VSPackage správy zdrojového kódu a poskytuje přehled kroků implementace.  
  
## <a name="the-source-control-vspackage"></a>VSPackage správy zdrojového kódu  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podporuje dva typy řešení správy zdrojového kódu. Ve všech verzích nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] můžete i nadále integrovat modul plug-in založený na modulu API pro správu zdrojového kódu. Můžete také vytvořit VSPackage pro správu zdrojového kódu, který poskytuje hloubkovou integraci, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] cestu vhodnou pro řešení správy zdrojového kódu, která vyžadují vysokou úroveň sofistikovanější a autonomie.  
  
 VSPackage může přidat skoro jakýkoli druh funkčnosti do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . VSPackage správy zdrojového kódu poskytuje úplnou funkci správy zdrojového kódu pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nástroj z uživatelského rozhraní prezentovaného uživateli do back-endové komunikace se systémem správy zdrojového kódu.  
  
 Implementace balíčku VSPackage správy zdrojového kódu vyžaduje strategii "vše nebo Nothing". Tvůrce balíčku VSPackage pro správu zdrojového kódu musí investovat značnou náročnost při implementaci řady rozhraní pro správu zdrojového kódu a nových prvků uživatelského rozhraní (dialogová okna, nabídky a panely nástrojů), aby pokryly celou funkci správy zdrojového kódu, a také rozhraní vyžadovaná všemi balíčky, které se mají úspěšně integrovat s [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Následující kroky poskytují obecný přehled o tom, co je potřeba k implementaci balíčku správy zdrojového kódu. Podrobnosti najdete v tématu [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1. Vytvořte VSPackage, který proffers službu správy privátních zdrojů.  
  
2. Implementujte rozhraní ve službě související se správou zdrojových kódů, které jsou proffered nástrojem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (například <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> rozhraní).  
  
3. Zaregistrujte VSPackage pro správu zdrojového kódu.  
  
4. Implementujte všechny uživatelské rozhraní správy zdrojového kódu, včetně položek nabídky, dialogových oken, panelů nástrojů a místních nabídek.  
  
5. Všechny události související se správou zdrojového kódu jsou předány do vašeho VSackage správy zdrojového kódu, když je aktivní a musí být zpracovávány pomocí VSPackage.  
  
6. Váš prvek VSPackage správy zdrojového kódu musí naslouchat událostem, jako jsou například implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> rozhraní a sledování událostí dokumentu projektu (TPD) (jak je implementováno <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> rozhraním) a podniknout potřebné akce.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Přehled](../../extensibility/internals/source-control-integration-overview.md)   
 [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)
