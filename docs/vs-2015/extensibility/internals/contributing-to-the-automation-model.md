---
title: Přispívání do modelu automatizace | Dokumentace Microsoftu
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
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53a669ed6f1ddaa9c2274371439828da24b92789
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726980"
---
# <a name="contributing-to-the-automation-model"></a>Přispívání do modelu automatizace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio poskytuje sadu rozhraní automatizace pro přizpůsobení prostředí. Model automatizace je objektový model, který umožňuje koncovým uživatelům vytvářet doplňky sady Visual Studio a rozšíření.  
  
 Kromě toho je vhodné pro vás, jako vývojář VSPackage přispívat do modelu automatizace Tímto způsobem, koncovým uživatelům vašeho balíčku VSPackage pro vytváření doplňků a obecně poskytují konzistentní uživatelské prostředí modelu při použití vašeho balíčku VSPackage v povolíte [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Chcete-li konzistentní prostředí koncového uživatele, můžete postupovat podle sadu pokynů, které při návrhu vašeho balíčku VSPackage tak, aby model automatizace pro vaše VSPackage následuje myšlenky v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled modelu automatizace](../../extensibility/internals/automation-model-overview.md)  
 Definuje model automatizace jako související skupiny objektů, které řídí hlavní charakteristiky společné prostředí. Tuto sadu objektů je uvedena v diagramu modelu automatizace.  
  
 [Poskytování automatizace pro balíčky VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Tento článek popisuje dva hlavní způsoby poskytování automatizace pro vaše VSPackage.  
  
 [Zveřejňování objektů projektu](../../extensibility/internals/exposing-project-objects.md)  
 Poskytuje podrobné pokyny pro vytvoření balíčku VSPackage konkrétní objekty.  
  
 [Modelování projektu](../../extensibility/internals/project-modeling.md)  
 Popisuje standardní projekt objekty, které jsou nutné k vytvoření automatizace pro nový typ projektu a ukazuje cestu, která následuje automatizace projektu. Toto téma obsahuje také výpisech deklarací a implementaci tříd.  
  
 [Zveřejňování událostí](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Poskytuje podrobné pokyny pro vytvoření události pro váš model automatizace.  
  
 [Podpora automatizace pro stránky Možnosti](../../extensibility/internals/automation-support-for-options-pages.md)  
 Popisuje, jak vrátit objekt automatizace pro podporu vlastnosti VSPackage vlastní **možnosti** dialogové okno na **nástroj** nabídky tím, že rozšíří `DTE.Properties` objektu.  
  
 [Poskytování automatizace pro kód](../../extensibility/internals/providing-automation-for-code.md)  
 Tento článek vysvětluje, že vytvoření modelu automatizace kódu se nevyžaduje. Ale je k dispozici odkaz v tomto tématu, které poskytuje přehledné informace do modely kódu.  
  
 [Postupy: Poskytování automatizace pro Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Vysvětluje, že poskytování automatizace je vhodné pokaždé, když chcete zpřístupnit objekty automatizace v okně a prostředí už neposkytuje předem připravená automatizační objekt. Tento článek popisuje automatizace pro okna nástrojů a oken dokumentu.  
  
 [Použití modelu automatizace](../../extensibility/internals/using-the-automation-model.md)  
 Poskytuje dva příklady kódu, které ukazují, jak spotřebitel automatizace získá počáteční projekt objekty automatizace.  
  
 [Automatizace pro konfiguraci a objekty SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Poskytuje informace o automatizaci pro možnosti konfigurace a automatizace pro vybrané položky.  
  
## <a name="reference"></a>Odkaz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Obsahuje ukázku kódu, který ukazuje, jak VSPackage podílí na objektový model DTE automatizace. Obsahuje seznam parametrů, vrácené hodnoty a vybrané poznámky.  
  
## <a name="related-sections"></a>Související oddíly

