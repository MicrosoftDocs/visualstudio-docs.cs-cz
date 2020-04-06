---
title: Podpora správy zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704733"
---
# <a name="supporting-source-control"></a>Podpora správy zdrojového kódu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]podporuje výběry souborů, vrácení se změnami a další operace správy zdrojového kódu pro váš projekt nebo editor. Jako klient správy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zdrojového kódu je navržen tak, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]aby pracoval s balíčkem správy zdrojového kódu, například , který poskytuje archivaci, správu verzí a řídicí zařízení pro dynamicky definovanou sadu souborů.

## <a name="in-this-section"></a>V tomto oddílu
- [Model pro balíčky správy zdrojového kódu](../../extensibility/internals/model-for-source-control-packages.md)

 Popisuje rozhraní, která musí typ projektu implementovat pro podporu správy zdrojového kódu.

- [Rozhodnutí o návrhu](../../extensibility/internals/source-control-design-decisions.md)

 Obsahuje otázky, jejichž odpovědi změnit způsob implementace typu projektu.

- [Podrobnosti konfigurace](../../extensibility/internals/source-control-configuration-details.md)

 Popisuje, jak podpůrná směřování zdrojového kódu mění implementaci typu projektu.

- [Další pokyny pro projekty a editory](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Popisuje osvědčené postupy pro typy projektů a editory.

- [Podrobnosti modulu runtime](../../extensibility/internals/source-control-runtime-details.md)

 Popisuje, jak zaregistrovat projekt, když jej uživatel přidá do systému správy zdrojového kódu.

## <a name="reference"></a>Referenční informace
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>Označuje prostředí nebo balíček správy zdrojového kódu, že soubor se chystá změnit v paměti nebo uložit.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>Umožňuje projektům a hierarchiím zaregistrovat se pomocí správy zdrojového kódu a získat informace o stavu správy zdrojového kódu.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>Implementována v systému projektu poskytovat správou zdrojového kódu pro soubory projektu a položky projektu.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>Projekty používají k dotazování prostředí na oprávnění k přidání, odebrání nebo přejmenování souboru nebo adresáře v řešení.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>Upozorní klienty na změny, které byly provedeny v souborech projektu nebo adresářích.

## <a name="related-sections"></a>Související oddíly
- [Typy projektů](../../extensibility/internals/project-types.md)

 Poskytuje přehled projektů jako základní stavební [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kameny integrovaného vývojového prostředí (IDE). Odkazy jsou k dispozici na další témata, která vysvětlují, jak projekty řídí vytváření a kompilaci kódu.
