---
title: Zajištění automatizace pro kód | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705997"
---
# <a name="providing-automation-for-code"></a>Poskytování automatizace pro kód
Vytvoření modelu automatizace pro váš kód není nutné. Sada Environment SDK neposkytuje vzorek pro to. Pro přehled o modelech <xref:EnvDTE.CodeModel> kódu, viz objekt.

 Chcete-li implementovat model kódu, musíte implementovat všechna rozhraní, která jsou určena vaší vnitřní datové struktury. Objekty musí být odvozeny od třídy. `IDispatch`

 Objekty, <xref:EnvDTE.CodeModel> které rozšiřujete a <xref:EnvDTE.FileCodeModel>, <xref:EnvDTE.Project> jsou k dispozici z objektu a vypadají takto:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Můžete se rozhodnout `CodeModel` implementovat `FileCodeModel` pouze nebo rozhraní v `Project` <xref:EnvDTE.ProjectItem> objektu, který vrátíte z objektu a objekty. Zajistěte všechny funkce z tohoto rozhraní, které jsou vhodné pro systém projektu.

 Pokud chcete přidat funkce, jako jsou metody nebo vlastnosti, `CodeModel` `FileCodeModel` které nejsou k dispozici ze standardu a rozhraní, vytvořte vlastní rozhraní, které dědí ze standardu. Ujistěte se, že dokument ovat s projektovým systémem, takže koncoví uživatelé budou vědět, hledat. Vrátíte standardní rozhraní, ale uživatel `QueryInterface` může volat metodu nebo přetypování do rozhraní, pokud je známo, že existuje.

## <a name="see-also"></a>Viz také
- [Přehled modelu automatizace](../../extensibility/internals/automation-model-overview.md)
