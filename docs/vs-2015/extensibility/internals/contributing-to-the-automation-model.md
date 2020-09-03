---
title: Přispívání do modelu automatizace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c84ea078f9b7c1268b765111cc400f6e51b783f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196997"
---
# <a name="contributing-to-the-automation-model"></a>Přispívání do modelu automatizace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sada Visual Studio poskytuje sadu automatizačních rozhraní pro přizpůsobení prostředí. Model automatizace je objektový model, který koncovým uživatelům umožňuje vytvářet doplňky a rozšíření sady Visual Studio.  
  
 Kromě toho je vhodné, jako vývojář VSPackage, pro přispívání do modelu automatizace; Díky tomu můžete koncovým uživatelům vaší VSPackage povolit vytváření doplňků a obecně poskytovat konzistentní prostředí uživatelského modelu při použití VSPackage v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Pro zajištění konzistence prostředí koncových uživatelů můžete při navrhování VSPackage použít sadu pokynů, takže model automatizace pro sadu VSPackage bude odpovídat nápadům v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled modelu automatizace](../../extensibility/internals/automation-model-overview.md)  
 Definuje model automatizace jako související skupiny objektů, které řídí hlavní charakteristiky společného prostředí. Tato sada objektů je naformátovaná v diagramu modelu automatizace.  
  
 [Poskytování automatizace pro balíčky VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Popisuje dva hlavní způsoby, jak zajistit automatizaci pro VSPackage.  
  
 [Zveřejňování objektů projektu](../../extensibility/internals/exposing-project-objects.md)  
 Poskytuje podrobné pokyny pro vytváření objektů specifických pro VSPackage.  
  
 [Modelování projektu](../../extensibility/internals/project-modeling.md)  
 Vysvětluje standardní objekty projektu, které jsou požadovány pro vytvoření automatizace pro nový typ projektu a ilustruje cestu, kterou automatizace projektu sleduje. Toto téma také poskytuje výpisy deklarací a implementaci tříd.  
  
 [Zveřejňování událostí](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Poskytuje podrobné pokyny pro vytváření událostí pro model automatizace.  
  
 [Podpora automatizace pro stránky Možnosti](../../extensibility/internals/automation-support-for-options-pages.md)  
 Popisuje, jak vrátit objekt automatizace pro podporu vlastností dialogového okna vlastních **možností** sady VSPackage v nabídce **nástroje** rozšířením `DTE.Properties` objektu.  
  
 [Poskytování automatizace pro kód](../../extensibility/internals/providing-automation-for-code.md)  
 Vysvětluje, že vytvoření modelu automatizace pro váš kód není vyžadováno. Odkaz je však k dispozici v tomto tématu, které poskytuje přehledné informace do modelů kódu.  
  
 [Postupy: Poskytování automatizace pro Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Vysvětluje, že poskytnutí automatizace je dobrý nápad vždy, když chcete objekty automatizace zpřístupnit v okně a prostředí již neposkytuje předem připravený automatizační objekt. Popisuje automatizaci pro okna nástrojů a okna dokumentů.  
  
 [Použití modelu automatizace](../../extensibility/internals/using-the-automation-model.md)  
 Obsahuje dva příklady kódu, které ukazují, jak spotřebitel automatizace získává počáteční objekty automatizace projektu.  
  
 [Automatizace pro konfiguraci a objekty SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Poskytuje informace o automatizaci pro možnosti konfigurace a automatizaci pro vybrané položky.  
  
## <a name="reference"></a>Referenční informace  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Obsahuje ukázku kódu, který ukazuje, jak se VSPackage účastní modelu automatizačních objektů DTE. Zobrazí seznam parametrů, vrácených hodnot a vybraných poznámek.  
  
## <a name="related-sections"></a>Související oddíly
