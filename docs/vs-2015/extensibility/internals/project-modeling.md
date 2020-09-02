---
title: Modelování projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e0edca4a45419a4a4c962ebf62b65e99c4732a12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431375"
---
# <a name="project-modeling"></a>Modelování projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dalším krokem poskytnutí automatizace pro váš projekt je implementace standardních objektů projektu: <xref:EnvDTE.Projects> `ProjectItems` kolekce a, `Project` objekty a a <xref:EnvDTE.ProjectItem> zbývající objekty, které jsou pro vaši implementaci jedinečné. Tyto standardní objekty jsou definovány v souboru Dteinternal. h. V ukázce BscPrj je k dispozici implementace standardních objektů. Tyto třídy můžete použít jako modely k vytvoření vlastních objektů projektu, které jsou umístěny souběžně s objekty projektu z jiných typů projektů.  
  
 V případě, že se spotřebitel automatizace předpokládá, že <xref:EnvDTE.Solution> `<UniqueProjName>")` <xref:EnvDTE.ProjectItems> `n` n je číslo indexu pro získání konkrétního projektu v řešení, předpokládá se, že je. Provedení tohoto volání automatizace způsobí, že prostředí zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> příslušnou hierarchii projektu a předává VSITEMID_ROOT jako parametr ItemId a VSHPROPID_ExtObject jako parametr VSHPROPID. `IVsHierarchy::GetProperty` Vrátí `IDispatch` ukazatel na automatizační objekt `Project` , který poskytuje základní rozhraní, které jste nasadili.  
  
 Následuje syntaxe `IVsHierarchy::GetProperty` .  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projekty, které přizpůsobily vnořování a používání kolekcí k vytváření skupin položek projektu. Hierarchie vypadá takto.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Vnořování znamená, že <xref:EnvDTE.ProjectItem> objekt může být <xref:EnvDTE.ProjectItems> ve stejnou dobu kolekce, protože `ProjectItems` kolekce může obsahovat vnořené objekty. Základní ukázka projektu neukazuje toto vnořování. Implementací `Project` objektu se můžete zúčastnit struktury podobné stromové struktury, která charakterizuje návrh celkového modelu automatizace.  
  
 Automatizace projektu následuje cesta v následujícím diagramu.  
  
 ![Objekty projektu sady Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automatizace projektu  
  
 Pokud objekt neimplementujete `Project` , prostředí stále vrátí obecný `Project` objekt, který obsahuje pouze název projektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>
