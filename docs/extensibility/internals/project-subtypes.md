---
title: Projekt podtypů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e91a16ad11f7089230138919519922d58f3cc472
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130654"
---
# <a name="project-subtypes"></a>Projekt podtypů
Projekt podtypů umožňují přizpůsobit nebo flavor chování projektu systémech [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Přizpůsobení zahrnují ukládání další data v souboru projektu, přidání nebo filtrování položek v **přidat novou položku** dialogové okno, řízení jakým způsobem jsou sestavení ladit a nasadit a rozšíření projektu **vlastnost Stránky** dialogové okno. VSPackages implementovat podtypů projektu pomocí COM agregace.  
  
> [!NOTE]
>  Systém projektu Visual C++ nepodporuje podtypů projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] samotný podtypů projektu používá k implementaci projekty pro inteligentní zařízení a systému SQL Server.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Návrh podtypů projektů](../../extensibility/internals/project-subtypes-design.md)  
 Popisuje koncept podtypů projektu.  
  
 [Inicializační sekvence podtypů projektů](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Popisuje pořadí inicializace dílčí programový projektu pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí.  
  
 [Vlastnosti a metody rozšířené prostřednictvím podtypů projektů](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Poskytuje podrobný popis funkce a metody, které jsou nejčastěji rozšířeno pomocí podtypů projektu.  
  
 [Trvalá data v souboru projektu nástroje MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Popisuje, jak uchovávat data v souboru projektu a jak používat <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> zachování dat v souboru projektu na úrovni projektu dílčí agregace.  
  
 [Uživatelské rozhraní vlastností projektu](../../extensibility/internals/project-property-user-interface.md)  
 Popisuje, jak podtypů projektu můžete upravit projektu **stránky vlastností** dialogové okno.  
  
 [Rozšíření objektového modelu základního projektu](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Poskytuje informace o jak projektu podtypů automatizace Extender k rozšíření můžete použít objektový model automatizace.  
  
 [Přispívání do dialogového okna Přidat novou položku](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Popisuje postup přidání položky do **přidat novou položku** dialogové okno.  
  
 [Ukládání dat v souborech projektu](../../extensibility/saving-data-in-project-files.md)  
 Vysvětluje, jak uložit a načtení dat specifické pro podtyp v souboru projektu pomocí spravované balíček Framework (MPF) podtypem projektu.  
  
 [Zpracování specializovaného nasazení](../../extensibility/internals/handling-specialized-deployment.md)  
 Vysvětluje, jak můžete zadat chování specializovaná nasazení implementací podtypů projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> rozhraní.  
  
 [Přidávání a odebírání stránek vlastností](../../extensibility/adding-and-removing-property-pages.md)  
 Popisuje přidání a odebrání stránky vlastností v Návrháři projektu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Obsahuje odkazy na témata s podrobnostmi o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty.