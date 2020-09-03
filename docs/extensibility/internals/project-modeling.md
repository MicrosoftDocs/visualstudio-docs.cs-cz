---
title: Modelování projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706545"
---
# <a name="project-modeling"></a>Modelování projektu
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
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Vnořování znamená, že <xref:EnvDTE.ProjectItem> objekt může být <xref:EnvDTE.ProjectItems> ve stejnou dobu kolekce, protože `ProjectItems` kolekce může obsahovat vnořené objekty. Základní ukázka projektu neukazuje toto vnořování. Implementací `Project` objektu se můžete zúčastnit struktury podobné stromové struktury, která charakterizuje návrh celkového modelu automatizace.

 Automatizace projektu následuje cesta v následujícím diagramu.

 ![Objekty projektu sady Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automatizace projektu

 Pokud objekt neimplementujete `Project` , prostředí stále vrátí obecný `Project` objekt, který obsahuje pouze název projektu.

## <a name="see-also"></a>Viz také
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
