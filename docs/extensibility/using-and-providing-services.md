---
title: Používání a poskytování služeb | Microsoft Docs
description: Seznamte se se službami, které Visual Studio IDE nabízí pro sady VSPackage k poskytování a použití. Tyto články popisují, jak získat a poskytnout služby.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbf04b5e4b032bc44040cf14f6bf23225696ee61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934116"
---
# <a name="using-and-providing-services"></a>Používání a poskytování služeb
Služba je smlouva mezi dvěma VSPackage. Jedna sada VSPackage nabízí konkrétní sadu rozhraní, které se mají využít pro další VSPackage. Například [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nabízí <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> službu pro všechny rozhraní VSPackage, které načítá. Tato služba poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> rozhraní, které lze použít k zápisu do protokolu aktivit. Další informace najdete v tématu [Postupy: použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).

 Sady VSPackage mohou nabízet své vlastní služby pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> rozhraní..

 Visual Studio nabízí důležité služby, například následující:

|Služba IDE|Description|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Poskytuje přístup ke službám IDE, které se týkají základních funkcí, sady VSPackage a registru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Poskytuje základní okna a funkce související s uživatelským rozhraním v integrovaném vývojovém prostředí (IDE), jako je například schopnost vytvářet nástroje a okna dokumentů.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Poskytuje základní funkce související s řešeními, jako je možnost zobrazení výčtu projektů, vytváření nových projektů a sledování změn projektů.|

## <a name="in-this-section"></a>V tomto oddílu
- [Základy služby](../extensibility/internals/service-essentials.md) Představuje důležité prvky služby Visual Studio.

- [Postupy: získání služby](../extensibility/how-to-get-a-service.md) Popisuje, jak vyžádat (spotřebovat) službu.

- [Postupy: poskytování služby](../extensibility/how-to-provide-a-service.md) Popisuje, jak poskytnout službu.

- [Postupy: poskytnutí asynchronní služby sady Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Popisuje, jak poskytnout asynchronní službu.

- [Postupy: řešení potíží se službami](../extensibility/how-to-troubleshoot-services.md) Popisuje běžné problémy a prezentuje jejich řešení.

## <a name="related-sections"></a>Související oddíly
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
