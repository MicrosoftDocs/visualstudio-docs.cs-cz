---
title: Poskytnutí automatizace pro kód | Microsoft Docs
description: Seznamte se s implementací modelu kódu, který vyžaduje implementující rozhraní, která jsou určena interní strukturou dat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 41dca5d7a3d2a95ae9b89feb73fb7655b8923eb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837213"
---
# <a name="providing-automation-for-code"></a>Poskytování automatizace pro kód
Vytvoření modelu automatizace pro váš kód není vyžadováno. Sada SDK prostředí vám neposkytuje ukázku. Přehledy o modelech kódu naleznete v tématu <xref:EnvDTE.CodeModel> Object.

 Chcete-li implementovat model kódu, je nutné implementovat jakákoli rozhraní, která jsou určena vaší interní datovou strukturou. Objekty musí být odvozeny od `IDispatch` třídy.

 Objekty, které rozšiřujete, <xref:EnvDTE.CodeModel> <xref:EnvDTE.FileCodeModel> jsou k dispozici z <xref:EnvDTE.Project> objektu a vypadají jako následující:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Můžete zvolit, že se má implementovat pouze `CodeModel` `FileCodeModel` rozhraní nebo rozhraní v objektu, který vrátíte z `Project` objektů a <xref:EnvDTE.ProjectItem> . Poskytněte jakékoli funkce z tohoto rozhraní, které jsou vhodné pro váš projektový systém.

 Chcete-li přidat funkce, jako například metody nebo vlastnosti, které nejsou k dispozici ze standardních `CodeModel` rozhraní a `FileCodeModel` , vytvořte vlastní rozhraní, které dědí z úrovně Standard. Nezapomeňte dokument zdokumentovat v systému projektu, aby ho koncoví uživatelé věděli, jak ho vyhledat. Vrátíte standardní rozhraní, ale uživatel může volat `QueryInterface` metodu nebo přetypovat na rozhraní, pokud je známo, že existuje.

## <a name="see-also"></a>Viz také
- [Přehled modelu automatizace](../../extensibility/internals/automation-model-overview.md)
