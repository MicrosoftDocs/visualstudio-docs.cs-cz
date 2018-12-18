---
title: Podtypy projektů | Dokumentace Microsoftu
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
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f4562eab97c28437d8722eacbb60459bd2732dfa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752700"
---
# <a name="project-subtypes"></a>Podtypy projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtypy projektů vám umožní přizpůsobit nebo flavor chování systémů projektů [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Vlastní nastavení zahrnují ukládá další data v souboru projektu, přidání nebo filtrování položek v **přidat novou položku** dialogové okno, řízení, jak ladit a nasadit, sestavení a rozšíření projektu **vlastnost Stránky** dialogové okno. Rozšíření VSPackages implementovat podtypů projektů pomocí modelu COM agregace.  
  
> [!NOTE]
>  Systém projektu Visual C++ nepodporuje podtypů projektů. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] samotný podtypů projektů používá k implementaci projekty systému SQL Server a inteligentní zařízení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Návrh podtypů projektů](../../extensibility/internals/project-subtypes-design.md)  
 Popisuje pojem podtypů projektů.  
  
 [Inicializační sekvence podtypů projektů](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Popisuje pořadí inicializace podtyp projektu programový podle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí.  
  
 [Vlastnosti a metody rozšířené prostřednictvím podtypů projektů](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Poskytuje podrobný popis funkce a metody nejčastěji rozšířené prostřednictvím podtypů projektů.  
  
 [Trvalá data v souboru projektu nástroje MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Popisuje, jak zachovat data v souboru projektu a jak používat <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> zachovat data v souboru projektu úrovních agregace podtyp projektu.  
  
 [Uživatelské rozhraní vlastností projektu](../../extensibility/internals/project-property-user-interface.md)  
 Popisuje, jak podtypů projektů můžete upravit projekt **stránky vlastností** dialogové okno.  
  
 [Rozšíření objektového modelu základního projektu](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Poskytuje informace o jak podtypů projektů můžete použít zařízení Extender automatizace k rozšíření objektového modelu automatizace.  
  
 [Přispívání do dialogového okna Přidat novou položku](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Popisuje postup přidání položky, které chcete **přidat novou položku** dialogové okno.  
  
 [Ukládání dat v souborech projektu](../../extensibility/saving-data-in-project-files.md)  
 Vysvětluje, jak uložit a načíst data specifická pro podtyp v souboru projektu pomocí Managed Package Framework (MPF) podtyp projektu.  
  
 [Zpracování specializovaného nasazení](../../extensibility/internals/handling-specialized-deployment.md)  
 Vysvětluje, jak můžete zadat chování specializovaného nasazení implementací podtypů projektů <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> rozhraní.  
  
 [Přidávání a odebírání stránek vlastností](../../extensibility/adding-and-removing-property-pages.md)  
 Popisuje, přidávání a odebírání stránek vlastností v Návrháři projektu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Obsahuje odkazy na témata s podrobnostmi o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projekty.

