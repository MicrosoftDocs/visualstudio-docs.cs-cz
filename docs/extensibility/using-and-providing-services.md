---
title: Použití a poskytování služeb | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 351b5b5c0ab32ab7e8267864eddaae10459a23bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138337"
---
# <a name="using-and-providing-services"></a>Použití a poskytování služeb
Služba je smlouva mezi dvěma VSPackages. Jeden VSPackage nabízí konkrétní sadu rozhraní pro jiné VSPackage využívat. Například [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nabízí <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> služby pro všechny VSPackage se zatížením. Tato služba poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> rozhraní, které lze použít k zápisu do protokolu činnosti. Další informace najdete v tématu [postupy: použití protokolu činnosti](../extensibility/how-to-use-the-activity-log.md).  
  
 VSPackages nabízejí služby své vlastní podle použití <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> rozhraní...  
  
 Visual Studio nabízí důležité služby, jako je následující:  
  
|Služba IDE|Popis|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Poskytuje přístup k rozhraní IDE služeb práci s základních funkcí, VSPackages a registru.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Poskytuje základní oddílová a související uživatelské rozhraní funkce v prostředí IDE, jako je například schopnost vytvářet nástroje a okna dokumentu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Poskytuje základní funkce související s řešení, jako je například možnost vytvořit výčet projekty, vytvořte nové projekty a sledování změn projektu.|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Základy služeb](../extensibility/internals/service-essentials.md)  
 Uvede důležité elementy služby Visual Studio.  
  
 [Postupy: Získání služby](../extensibility/how-to-get-a-service.md)  
 Popisuje, jak požádat o (spotřebovávat) služby.  
  
 [Postupy: Poskytování služby](../extensibility/how-to-provide-a-service.md)  
 Popisuje, jak mají poskytovat služby.  
  
 [Postupy: Poskytování asynchronní služby sady Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Popisuje, jak zajistit asynchronní služby.  
  
 [Postupy: Řešení problémů se službami](../extensibility/how-to-troubleshoot-services.md)  
 Popisuje běžné problémy a uvede řešení k nim.  
  
## <a name="related-sections"></a>Související oddíly  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)