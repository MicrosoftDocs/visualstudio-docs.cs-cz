---
title: Projekty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2ca4edabcee9f561dea51ea4b579ce194d13fa8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131002"
---
# <a name="projects"></a>Projekty
V sadě Visual Studio, projekty jsou kontejnery, které vývojáři použít k uspořádání soubory zdrojového kódu a další prostředky, které se zobrazují v **Průzkumníku řešení**. Projekty jsou obvykle soubory (například souboru .csproj projektů C#), které obsahují odkazy na soubory zdrojového kódu a prostředkům, jako jsou soubory rastrového obrázku. Projekty umožňují uspořádat, sestavení, ladění a nasazení zdrojového kódu, odkazuje na webové služby a databáze a dalším prostředkům. VSPackages systém projektu sady Visual Studio můžete rozšířit třemi hlavními způsoby: *typy projektů*, *projektu podtypů*, a *vlastních nástrojů*.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 *Typy projektů* přidat podporu pro nové typy projektů, jako je například programovacích jazyků. Například jednotlivé jazyky, Visual Studio podporuje má svůj vlastní typ projektu a ukázka integrace IronPython zahrnuje typ projektu pro jazyk IronPython. Musíte vytvořit typu projektu pro jiné jazyky než C# nebo Visual Basic pro přizpůsobení, jak se položky vytvořené, ladit, nasazení a zobrazují v **Průzkumníku řešení**. Další informace najdete v tématu [typy projektů](../../extensibility/internals/project-types.md).  
  
 [Podtypy projektů](../../extensibility/internals/project-subtypes.md)  
 *Projekt podtypů* jsou založená na typy projektů a umožňuje přizpůsobit projekty jsou vytvořené, ladit a nasadit. Visual Studio použije podtypů projektu s projekty Smart Device Project; nasazení se přizpůsobit tak, že zkopírujete program nově vytvořené z vývojovém počítači cílového zařízení. C# a typy projektů jazyka Visual Basic lze použít jako základ pro projekt podtypů; Typy projektů C++ nelze. Vlastní typy projektů můžete také použít jako základ u podtypů projektu. Další informace najdete v tématu [projektu podtypů](../../extensibility/internals/project-subtypes.md).  
  
 [Webové projekty](../../extensibility/internals/web-projects.md)  
 Vysvětluje webový projekt, který naopak vytvářet webové aplikace.  
  
 [Nové generace projektu: Pod pokličkou, první část](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) a [nové generace projektu: pod pokličkou, část 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Vysvětluje, co se skutečně děje při vytvoření nového projektu.  
  
 [Ukázky VSSDK](http://aka.ms/vs2015sdksamples)  
 Obsahuje ukázky v VSSDK, které pracují s projekty a řešení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Práce se sadou Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Popisují různé aspekty rozšíření sady Visual Studio.