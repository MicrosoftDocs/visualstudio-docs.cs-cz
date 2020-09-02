---
title: Podpora automatizace pro stránky možností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157241"
---
# <a name="automation-support-for-options-pages"></a>Podpora automatizace pro stránky Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sady VSPackage mohou poskytnout dialogová okna vlastních **možností** do nabídky **nástroje** (stránky možností nástrojů) v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a mohou je zpřístupnit modelu automatizace.  
  
## <a name="tools-options-pages"></a>Stránky možností nástrojů  
 Aby bylo možné vytvořit stránku **možností nástroje** , VSPackage musí poskytnout implementaci uživatelského ovládacího prvku vrácenou do prostředí prostřednictvím implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody VSPackage (nebo pro spravovaný kód <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody).  
  
 Je volitelný, ale důrazně se doporučuje, aby byl přístup k této nové stránce povolen pomocí modelu automatizace. Můžete to provést pomocí následujících kroků:  
  
1. Rozšiřuje <xref:EnvDTE._DTE.Properties%2A> objekt pomocí implementace objektu odvozeného pro rozhraní IDispatch.  
  
2. Vraťte implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody (nebo spravovaného kódu <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metody) na objekt odvozený od rozhraní IDispatch.  
  
3. Když příjemce automatizace volá <xref:EnvDTE._DTE.Properties%2A> metodu na stránce vlastností vlastní **Možnosti** , prostředí používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodu k získání automatizované implementace stránky **možností nástrojů** .  
  
4. Automatizační objekt sady VSPackage je pak použit k poskytnutí všech <xref:EnvDTE.Property> vrácených funkcí <xref:EnvDTE._DTE.Properties%2A> .  
  
   Ukázku implementace vlastní možnosti nástrojů naleznete v tématu [VSSDK Samples](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Zveřejňování objektů projektu](../../extensibility/internals/exposing-project-objects.md)
