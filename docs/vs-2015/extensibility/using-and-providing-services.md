---
title: Používání a poskytování služeb | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f58e29797e9a7760aa0f48c68868199f51b3c92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177430"
---
# <a name="using-and-providing-services"></a>Používání a poskytování služeb
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Služba je smlouva mezi dvěma VSPackage. Jedna sada VSPackage nabízí konkrétní sadu rozhraní, které se mají využít pro další VSPackage. Například [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nabízí <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> službu pro všechny rozhraní VSPackage, které načítá. Tato služba poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> rozhraní, které lze použít k zápisu do protokolu aktivit. Další informace najdete v tématu [Postupy: použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).  
  
 Sady VSPackage mohou nabízet své vlastní služby pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> rozhraní..  
  
 Visual Studio nabízí důležité služby, například následující:  
  
|Služba IDE|Popis|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Poskytuje přístup ke službám IDE, které se týkají základních funkcí, sady VSPackage a registru.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Poskytuje základní okna a funkce související s uživatelským rozhraním v integrovaném vývojovém prostředí (IDE), jako je například schopnost vytvářet nástroje a okna dokumentů.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Poskytuje základní funkce související s řešeními, jako je možnost zobrazení výčtu projektů, vytváření nových projektů a sledování změn projektů.|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Základy služeb](../extensibility/internals/service-essentials.md)  
 Představuje důležité prvky služby Visual Studio.  
  
 [Postupy: Získání služby](../extensibility/how-to-get-a-service.md)  
 Popisuje, jak vyžádat (spotřebovat) službu.  
  
 [Postupy: Poskytování služby](../extensibility/how-to-provide-a-service.md)  
 Popisuje, jak poskytnout službu.  
  
 [Postupy: Poskytování asynchronní služby sady Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Popisuje, jak poskytnout asynchronní službu.  
  
 [Postupy: Řešení problémů se službami](../extensibility/how-to-troubleshoot-services.md)  
 Popisuje běžné problémy a prezentuje jejich řešení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
