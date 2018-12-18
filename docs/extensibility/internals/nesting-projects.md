---
title: Projekty vnoření | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35d0f4f8906acc08733894d1c24b6d8c2199e1f7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131157"
---
# <a name="nesting-projects"></a>Vnoření projekty
Podnikové aplikace vývojáře, kteří používají vašeho balíčku VS můžete pohodlně Seskupit podobné typy projektů společně v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pomocí *projektu vnoření*. Projekt šablony organizace například používá vnořené projektů pro projekty skupiny do kategorií. Obchodní průčelí za projekty, projekty webového uživatelského rozhraní a tak dále jsou seskupeny dohromady v jedné kategorii.  
  
 V tomto scénáři není nijak omezen počet projekty, které vývojář lze vnořit pod každý nadřazený projekt, i když vývojář může prostřednictvím kódu programu poskytnout omezení. Tento typ seskupení můžete také provést rekurzivní, v takovém případě projekty stejného typu jako podřízené projekt mohou být použity v podřízené stane dílčího podřízených, která je dílčí projekt nadřazeného objektu.  
  
 Vnoření projektu není vnitřní součástí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Budete muset napsat kód pro povolení vnoření a dílčí projekt vnoření v rámci podřízené projekty. Nadřazený projekt je speciální VSPackage, nebo typu projektu, vytvořená a zaregistrovaná s vlastní identifikátor GUID, který obsahuje kód, který se vyžaduje k implementaci vnoření projektu.  
  
 Příkladem vnořené projekty můžete najít v ukázce Example.Nested projektu C#.  
  
## <a name="nested-projects-example"></a>Příklad vnořené projekty  
 ![Vnořené projekty řešení](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Příklad vnořené projekty  
  
## <a name="see-also"></a>Viz také  
 [Postupy: implementace vnořené projekty](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Důležité informace pro uvolnění a překladní vnořené projekty](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Podpora průvodce pro vnořené projekty](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementace příkaz zpracování pro vnořené projekty](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtrování AddItem dialogových oken pro vnořené projekty](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Kontrolní seznam: Vytvoření nové typy projektu](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontextové parametry](../../extensibility/internals/context-parameters.md)   
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)