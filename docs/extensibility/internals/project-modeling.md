---
title: Modelování projektů | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706545"
---
# <a name="project-modeling"></a>Modelování projektu
Dalším krokem v poskytování automatizace pro váš projekt je <xref:EnvDTE.Projects> `ProjectItems` implementovat standardní projektové objekty: a kolekce; předměty `Project` <xref:EnvDTE.ProjectItem> a předměty; a zbývající objekty jedinečné pro vaši implementaci. Tyto standardní objekty jsou definovány v souboru Dteinternal.h. Implementace standardních objektů je k dispozici v bscprj vzorku. Tyto třídy můžete použít jako modely k vytvoření vlastní chod standardního projektu, které stojí vedle sebe s objekty projektu z jiných typů projektů.

 Spotřebitel automatizace předpokládá, že <xref:EnvDTE.Solution>bude`<UniqueProjName>")` moci <xref:EnvDTE.ProjectItems> `n`volat (" a ( ), kde n je indexové číslo pro získání konkrétního projektu v řešení. Provedení tohoto volání automatizace <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> způsobí, že prostředí volat na příslušné hierarchii projektu, předávání VSITEMID_ROOT jako ItemID parametr a VSHPROPID_ExtObject jako vshpropid parametr. `IVsHierarchy::GetProperty`vrátí `IDispatch` ukazatel na objekt automatizace `Project` poskytující základní rozhraní, které jste implementovali.

 Následuje syntaxe souboru `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Projekty pojmou vnoření a používají kolekce k vytvoření skupin položek projektu. Hierarchie vypadá takto.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Vnoření znamená, <xref:EnvDTE.ProjectItem> že <xref:EnvDTE.ProjectItems> objekt může být `ProjectItems` kolekce současně, protože kolekce může obsahovat vnořené objekty. Ukázka základního projektu neukazuje toto vnoření. Implementací `Project` objektu se účastníte stromové struktury, která charakterizuje návrh modelu celkové automatizace.

 Automatizace projektu následuje cestu v následujícím diagramu.

 ![Objekty projektu visual studia](../../extensibility/internals/media/projectobjects.gif "Objekty projektu") Automatizace projektů

 Pokud neimplementujete `Project` objekt, prostředí stále `Project` vrátí obecný objekt, který obsahuje pouze název projektu.

## <a name="see-also"></a>Viz také
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
