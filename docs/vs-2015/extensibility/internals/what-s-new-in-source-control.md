---
title: Co&#39;s nový ve správě zdrojového kódu | Dokumentace Microsoftu
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
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a108acb2ae32b64292cd819c75de4726f067a00
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752457"
---
# <a name="what39s-new-in-source-control"></a>Co&#39;s nový ve správě zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] může nabídnout řešení hluboce integrované zdrojového ovládacího prvku implementací balíčku VSPackage správy zdrojového kódu. Tato část popisuje funkce správy zdrojového kódu rozšíření VSPackages a poskytuje přehled o implementaci.  
  
## <a name="the-source-control-vspackage"></a>Ovládací prvek VSPackage zdroje  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podporuje dva typy řešení pro řízení zdrojů. Ve všech verzích [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], stále můžete integrovat na rozhraní API modulu Plug-in zdroje ovládacího prvku modulu plug-in. Můžete také vytvořit VSPackage pro správu zdrojového kódu, který poskytuje hluboká integrace, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] vhodná pro řešení pro řízení zdrojů, které vyžadují vysokou úroveň vyspělosti a autonomie cestu.  
  
 VSPackage můžete přidat téměř jakýkoli druh funkce, které [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Balíčku VSPackage správy zdrojového kódu obsahuje funkci úplný zdrojový ovládací prvek pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], v uživatelském rozhraní zobrazovat uživateli back-end odpovíte na sdělení a systém správy zdrojového kódu.  
  
 Implementace balíčku VSPackage správy zdrojového kódu vyžaduje strategii "všechno nebo nic". Tvůrce balíčku VSPackage správy zdrojového kódu musí investovat značné úsilí při implementaci řady rozhraní ovládacího prvku zdroje a nových prvků uživatelského rozhraní (dialogová okna, nabídek a panelů nástrojů) k pokrytí celé funkce správy zdrojového kódu, a také rozhraní vyžadují libovolný balíček úspěšně integrovat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Následující kroky poskytují obecný přehled toho, co je potřeba implementovat zdrojový balíček ovládacího prvku. Podrobnosti najdete v tématu [vytváření VSPackage ovládací prvek zdroje](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Vytvoření VSPackage proffers službu správy privátní zdrojových kódů.  
  
2.  Implementovat rozhraní v zdroje týkající se řízení služby, které jsou proffered podle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (například <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> rozhraní).  
  
3.  Registrace správy zdrojového kódu VSPackage.  
  
4.  Implementujte všechny správy zdrojového kódu uživatelského rozhraní, včetně položek nabídky, dialogová okna, panely nástrojů a kontextové nabídky.  
  
5.  Všechny zdroje události související s ovládacími jsou předány do správy zdrojových kódů VSackage, když je aktivní a musí být zpracována vaše VSPackage.  
  
6.  Správy zdrojového kódu VSPackage musí naslouchat událostem ohrožují implementující <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> rozhraní a sledování projektu dokumentu (TPD) události (jak je implementované <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> rozhraní) a proveďte potřebné akce.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Přehled](../../extensibility/internals/source-control-integration-overview.md)   
 [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)

