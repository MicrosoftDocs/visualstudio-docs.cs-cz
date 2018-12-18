---
title: Používání a poskytování služeb | Dokumentace Microsoftu
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
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 189ff14c566c3007810ef35cd63ec03a5958e07c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779707"
---
# <a name="using-and-providing-services"></a>Používání a poskytování služeb
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Služba je kontrakt mezi dvěma rozšíření VSPackages. Jeden VSPackage nabízí konkrétní sadu rozhraní pro jiné VSPackage využívat. Například [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nabízí <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> služby žádné VSPackage jeho zatížení. Tato služba poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> rozhraní, které lze použít k zápisu do protokolu aktivit. Další informace najdete v tématu [postupy: použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).  
  
 Rozšíření VSPackages můžete nabízet služby jejich vlastní použití <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> rozhraní...  
  
 Visual Studio nabízí důležité služby, jako je následující:  
  
|Služba na integrované vývojové prostředí|Popis|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Poskytuje přístup k integrované vývojové prostředí služby práci s základní funkce, rozšíření VSPackages a registru.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Poskytuje základní oddílová a související s Uživatelským rozhraním funkce v rozhraní IDE, jako je například schopnost vytvářet nástroje a oken s dokumentem.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Poskytuje základní funkce týkající se řešení, jako je například možnost udělat výčet projektů, vytvořit nové projekty a sledovat změny v projektu.|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Základy služeb](../extensibility/internals/service-essentials.md)  
 Uvede počet důležité elementy služby Visual Studio.  
  
 [Postupy: Získání služby](../extensibility/how-to-get-a-service.md)  
 Popisuje, jak požádat o (spotřebovávat) služby.  
  
 [Postupy: Poskytování služby](../extensibility/how-to-provide-a-service.md)  
 Popisuje, jak poskytovat služby.  
  
 [Postupy: Poskytování asynchronní služby sady Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Popisuje, jak k poskytování asynchronní služby.  
  
 [Postupy: Řešení problémů se službami](../extensibility/how-to-troubleshoot-services.md)  
 Tento článek popisuje běžné problémy a nabídne řešení k nim.  
  
## <a name="related-sections"></a>Související oddíly  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

