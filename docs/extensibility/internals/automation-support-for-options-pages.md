---
title: Podpora automatizace pro stránky Možnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b18f8df30dc9f3385c2c5f154d66c598b423968e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929644"
---
# <a name="automation-support-for-options-pages"></a>Podpora automatizace pro stránky Možnosti
Rozšíření VSPackages můžete zadat vlastní **možnosti** dialogová okna pro **nástroje** nabídky (**možnosti nástrojů** stránek) v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a můžete zpřístupnit je automatizace model.  
  
## <a name="tools-options-pages"></a>stránky Možnosti nástrojů  
 Vytvoření **možnosti nástrojů** stránce VSPackage musí poskytnout implementaci ovládacího prvku uživatel vrátí do prostředí prostřednictvím sady VSPackage provádění <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metoda. (Nebo pro spravovaný kód, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metoda.) 
  
 Je volitelný, ale důrazně doporučujeme, pokud chcete povolit přístup na tuto novou stránku prostřednictvím modelu automatizace. Můžete tak učinit pomocí následujících kroků:  
  
1. Rozšíření <xref:EnvDTE._DTE.Properties%2A> objektu prostřednictvím implementace objektu odvozené rozhraní IDispatch.  
  
2. Vrátila implementace rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> – metoda (nebo pro spravovaný kód <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metoda) na objekt odvozené rozhraní IDispatch.  
  
3. Když příjemci automatizace zavolá <xref:EnvDTE._DTE.Properties%2A> metodu na vlastní **možnost** stránka vlastností prostředí používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metoda získat vlastní **možnosti nástrojů** automation na stránce implementace.  
  
4. Objekt automatizace sady VSPackage je pak sloužit ke každé <xref:EnvDTE.Property> vrácený <xref:EnvDTE._DTE.Properties%2A>.  
  
   Pro ukázku implementace vlastní **možnosti nástrojů** stránky, přečtěte si téma [VSSDK ukázky](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Viz také:  
 [Vystavení objektů projektu](../../extensibility/internals/exposing-project-objects.md)