---
title: Funkce balíčku VSPackage správy zdrojového kódu | Microsoft Docs
description: Přečtěte si o funkcích balíčku VSPackage správy zdrojového kódu, včetně podrobností o registraci/výběru a o některých hlavních funkcích souvisejících se správou zdrojových kódů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd501aa6d1fc3189d5008d76deb56dd570d03d8e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064121"
---
# <a name="source-control-vspackage-features"></a>Funkce balíčku VSPackage správy zdrojového kódu
Tato část popisuje různé funkce balíčku VSPackage správy zdrojového kódu. Popisuje údaje o registraci a výběru pro takovou sadu VSPackage a zabývá se třemi hlavními funkcemi souvisejícími se správou zdrojového kódu: zpracování událostí Query-Editch Query-Save (QEQS), nahrazení glyfů a vlastní uživatelské rozhraní (UI) pro funkce správy zdrojového kódu.

## <a name="in-this-section"></a>V tomto oddílu
- [Registrace a výběr](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Popisuje mechanizmy pro registraci a výběr balíčku.

- [Události QEQS (Query Edit Query Save)](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Vysvětluje roli Query-Edit události Query-Save a jejich zpracování nástrojem VSPackage správy zdrojového kódu.

- [Správa piktogramů](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Popisuje úrovně ovládacího prvku glyf a jejich implementaci.

- [Vlastní uživatelského rozhraní](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Popisuje prvky uživatelského rozhraní, které může použít VSPackage správy zdrojového kódu.

## <a name="related-sections"></a>Související oddíly
- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Popisuje, jak vytvořit prvek VSPackage správy zdrojového kódu, který neposkytuje pouze funkce správy zdrojového kódu, ale lze jej použít k přizpůsobení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní správy zdrojového kódu.
