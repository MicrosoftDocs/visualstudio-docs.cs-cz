---
title: Modelování projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725563"
---
# <a name="project-modeling"></a>Modelování projektu
Dalším krokem poskytnutí automatizace pro váš projekt je implementace standardních objektů projektu: kolekce <xref:EnvDTE.Projects> a `ProjectItems`; objekty `Project` a <xref:EnvDTE.ProjectItem>; a zbývající objekty, které jsou pro vaši implementaci jedinečné. Tyto standardní objekty jsou definovány v souboru Dteinternal. h. V ukázce BscPrj je k dispozici implementace standardních objektů. Tyto třídy můžete použít jako modely k vytvoření vlastních objektů projektu, které jsou umístěny souběžně s objekty projektu z jiných typů projektů.

 Předpokládá se, že příjemce automatizace může volat <xref:EnvDTE.Solution> ("`<UniqueProjName>")` a <xref:EnvDTE.ProjectItems> (`n`), kde n je číslo indexu pro získání konkrétního projektu v řešení. Provedení tohoto volání automatizace způsobí, že prostředí zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> v příslušné hierarchii projektu a předává VSITEMID_ROOT jako parametr ItemID a VSHPROPID_ExtObject jako parametr VSHPROPID. `IVsHierarchy::GetProperty` vrátí ukazatel `IDispatch` na automatizační objekt, který poskytuje základní `Project` rozhraní, které jste nasadili.

 Následuje syntaxe `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT``*pvar`

 `);`

 Projekty, které přizpůsobily vnořování a používání kolekcí k vytváření skupin položek projektu. Hierarchie vypadá takto.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Vnořování znamená, že objekt <xref:EnvDTE.ProjectItem> lze <xref:EnvDTE.ProjectItems> kolekci ve stejnou dobu, protože kolekce `ProjectItems` může obsahovat vnořené objekty. Základní ukázka projektu neukazuje toto vnořování. Implementací objektu `Project` se můžete zúčastnit struktury podobné stromové struktury, která charakterizuje návrh celkového modelu automatizace.

 Automatizace projektu následuje cesta v následujícím diagramu.

 ![Objekty projektu sady Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automatizace projektu

 Pokud neimplementujete objekt `Project`, prostředí bude stále vracet obecný objekt `Project`, který obsahuje pouze název projektu.

## <a name="see-also"></a>Viz také:
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>