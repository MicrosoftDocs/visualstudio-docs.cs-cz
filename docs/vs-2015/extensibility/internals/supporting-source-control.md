---
title: Podpora správy zdrojového kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1166197a5c79dcb0d1ddf4018227914346a6172
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156073"
---
# <a name="supporting-source-control"></a>Podpora správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podporuje rezervace souborů, vrácení se změnami a další operace správy zdrojového kódu pro váš projekt nebo editor. Jako klient správy zdrojového kódu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] je navržený tak, aby spolupracoval se balíčkem správy zdrojového kódu, jako je například [!INCLUDE[vsvss](../../includes/vsvss-md.md)] , který zajišťuje archivaci, správu verzí a řízení pro dynamicky definovanou sadu souborů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Model pro balíčky správy zdrojového kódu](../../extensibility/internals/model-for-source-control-packages.md)  
 Popisuje rozhraní, které musí typ projektu implementovat pro podporu správy zdrojového kódu.  
  
 [Rozhodnutí o návrhu](../../extensibility/internals/source-control-design-decisions.md)  
 Obsahuje otázky, jejichž odpovědi mění způsob implementace typu projektu.  
  
 [Podrobnosti o konfiguraci](../../extensibility/internals/source-control-configuration-details.md)  
 Popisuje, jak Podpora správy zdrojového kódu mění implementaci typu projektu.  
  
 [Další pokyny pro projekty a editory](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Popisuje osvědčené postupy pro typy a editory projektů.  
  
 [Podrobnosti modulu runtime](../../extensibility/internals/source-control-runtime-details.md)  
 Popisuje, jak zaregistrovat projekt, když ho uživatel přidá do systému správy zdrojového kódu.  
  
## <a name="reference"></a>Referenční informace  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indikuje prostředí nebo balíček správy zdrojového kódu, že se chystá změnit soubor v paměti nebo Uložit.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Umožňuje projektům a hierarchiím zaregistrovat se pomocí správy zdrojového kódu a získat informace o stavu správy zdrojového kódu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implementováno v systému projektu pro poskytování správy zdrojového kódu pro soubory projektu a položky projektu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Používá projekty k dotazování prostředí pro oprávnění k přidání, odebrání nebo přejmenování souboru nebo adresáře v řešení.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Upozorňuje klienty na změny, které byly provedeny v souborech projektu nebo adresářích.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Poskytuje přehled o projektech jako základních stavebních bloků [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí (IDE). Odkazy jsou k dispozici pro další témata, která vysvětlují, jak projekty řídí sestavení a kompilování kódu.
