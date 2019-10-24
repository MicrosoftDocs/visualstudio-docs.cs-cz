---
title: Poskytnutí automatizace pro kód | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 874446aa6bf2e40a120aac49e7d91fd3d861d1d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724964"
---
# <a name="providing-automation-for-code"></a>Poskytování automatizace pro kód
Vytvoření modelu automatizace pro váš kód není vyžadováno. Sada SDK prostředí vám neposkytuje ukázku. Informace o modelech kódu naleznete v objektu <xref:EnvDTE.CodeModel>.

 Chcete-li implementovat model kódu, je nutné implementovat jakákoli rozhraní, která jsou určena vaší interní datovou strukturou. Objekty musí být odvozeny od `IDispatch` třídy.

 Objekty, které rozšiřujete, <xref:EnvDTE.CodeModel> a <xref:EnvDTE.FileCodeModel>, jsou k dispozici z objektu <xref:EnvDTE.Project> a vypadají jako následující:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Můžete zvolit, že se má implementovat pouze `CodeModel` nebo rozhraní `FileCodeModel` v objektu, který vrátíte z objektů `Project` a <xref:EnvDTE.ProjectItem>. Poskytněte jakékoli funkce z tohoto rozhraní, které jsou vhodné pro váš projektový systém.

 Chcete-li přidat funkce, jako například metody nebo vlastnosti, které nejsou k dispozici ze standardních `CodeModel` a `FileCodeModel` rozhraní, vytvořte vlastní rozhraní, které dědí z úrovně Standard. Nezapomeňte dokument zdokumentovat v systému projektu, aby ho koncoví uživatelé věděli, jak ho vyhledat. Vrátíte standardní rozhraní, ale uživatel může zavolat metodu `QueryInterface` nebo přetypovat na rozhraní, pokud je známo, že existuje.

## <a name="see-also"></a>Viz také:
- [Přehled modelu automatizace](../../extensibility/internals/automation-model-overview.md)