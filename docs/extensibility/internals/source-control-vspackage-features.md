---
title: Funkce správy zdrojového kódu VSPackage | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a01b9d8fbf5f8d0645b5245d21b05aba9e7dacea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705021"
---
# <a name="source-control-vspackage-features"></a>Funkce balíčku VSPackage správy zdrojového kódu
Tato část popisuje různé funkce správy zdrojového kódu VSPackage. Popisuje podrobnosti registrace a výběru pro takový VSPackage a popisuje tři z hlavních funkcí souvisejících s ovládacím prvkem zdrojového kódu: zpracování událostí Query-Edit Query-Save (QEQS), nahrazení glyfu a vlastní uživatelské rozhraní (UI) pro funkce správy zdrojového kódu.

## <a name="in-this-section"></a>V tomto oddílu
- [Registrace a výběr](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Popisuje mechanismy registrace a výběru balíčku.

- [Události QEQS (Query Edit Query Save)](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Vysvětluje roli query-Edit Query-Save události a jak jsou zpracovány pomocí správy zdrojového kódu VSPackage.

- [Správa piktogramů](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Popisuje úrovně glyfů a jejich implementaci.

- [Vlastní uživatelského rozhraní](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Popisuje prvky uživatelského rozhraní, které může určit zdrojový prvek VSPackage.

## <a name="related-sections"></a>Související oddíly
- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Popisuje, jak vytvořit zdrojového ovládacího prvku VSPackage, který poskytuje nejen funkce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] správy zdrojového kódu, ale lze jej přizpůsobit ui správy zdrojového kódu.
