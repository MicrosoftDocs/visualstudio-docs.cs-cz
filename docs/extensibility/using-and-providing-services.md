---
title: Využívání a poskytování služeb | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698743"
---
# <a name="using-and-providing-services"></a>Používání a poskytování služeb
Služba je smlouva mezi dvěma Balíčky VSPackages. Jeden VSPackage nabízí konkrétní sadu rozhraní pro jiné VSPackage využívat. Například [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nabízí <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> službu jakékoli VSPackage načte. Tato služba <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> poskytuje rozhraní, které lze použít k zápisu do protokolu aktivit. Další informace naleznete v [tématu How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).

 VSPackages mohou nabízet vlastní služby <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> pomocí rozhraní..

 Visual Studio nabízí důležité služby, jako jsou následující:

|Služba IDE|Popis|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Poskytuje přístup ke službám IDE zabývajícím se základními funkcemi, balíčky VSPackages a registru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Poskytuje základní okna a funkce související s uznatým prostředím v prostředí IDE, jako je například možnost vytvářet nástroje a okna dokumentu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Poskytuje základní funkce související s řešením, jako je například možnost výčtu projektů, vytváření nových projektů a sledování změn projektu.|

## <a name="in-this-section"></a>V tomto oddílu
- [Základy služeb](../extensibility/internals/service-essentials.md) Představuje důležité prvky služby sady Visual Studio.

- [Postup: Získání služby](../extensibility/how-to-get-a-service.md) Popisuje, jak požadovat (využívat) služby.

- [Postup: Poskytnutí služby](../extensibility/how-to-provide-a-service.md) Popisuje, jak poskytovat služby.

- [Postup: Poskytnutí asynchronní služby Sady Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Popisuje, jak poskytovat asynchronní služby.

- [Postup: Poradce při potížích se službami](../extensibility/how-to-troubleshoot-services.md) Popisuje běžné problémy a představuje jejich řešení.

## <a name="related-sections"></a>Související oddíly
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
