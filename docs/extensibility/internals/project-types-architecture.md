---
title: Typy projektu architektura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6ef7fe6fbf4a8899606dca35c10745e68e3cbfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130599"
---
# <a name="project-types-architecture"></a>Architektura typy projektu
Tato část obsahuje podrobné informace o architektuře typy projektů v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)  
 Jsou uvedené služby, které můžou využívat typu projektu a, kterou musí implementovat rozhraní.  
  
 [Základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)  
 Popisuje rozhraní typy projektů současně musí implementovat a volitelně můžete implementovat dodatečných funkcí.  
  
 [Kdy vytvořit typy projektů](../../extensibility/internals/when-to-create-project-types.md)  
 Zadejte pomůže vám při rozhodování při musíte vytvořit projekt a kdy můžete použít jiné [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkce rozšíření, jako je například VSPackages a editory k dosažení stejného cíle.  
  
 [Hierarchie a výběr](../../extensibility/internals/hierarchies-and-selection.md)  
 Popisuje, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používá hierarchie a výběr kontextu zajistit konzistentní a zjednodušená uživatelské prostředí.  
  
## <a name="related-sections"></a>Související oddíly  
 [Podtypy projektů](../../extensibility/internals/project-subtypes.md)  
 Vysvětluje, jak projektu podtypů umožňují přizpůsobit chování projektu systémy [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] a [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Poskytuje přehled projekty jako základní stavební bloky [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE). Jsou uvedeny odkazy na další témata, které vysvětlují, jak řídit projekty vytváření a kompilování kódu.