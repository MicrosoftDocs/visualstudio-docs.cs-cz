---
title: Prvky návrhu balíčku VSPackage správy zdrojového kódu | Microsoft Docs
description: Seznamte se se strukturou, kterou musí VSPackage správy zdrojového kódu implementovat, a rozhraní a služby, které může VSPackage správy zdrojového kódu implementovat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e3e8d70d721e77e0ed7b93dda3be5defdbf7dd9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064062"
---
# <a name="source-control-vspackage-design-elements"></a>Prvky návrhu balíčku VSPackage správy zdrojového kódu
Témata v této části popisují strukturu, kterou musí VSPackage správy zdrojového kódu implementovat pro rozsáhlou integraci. Obsahuje také seznam rozhraní a služeb, které může model VSPackage správy zdrojového kódu implementovat, a rozhraní a služby, které může VSPackage správy zdrojového kódu využít z jiných [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komponent k podpoře modelu a funkčnosti správy zdrojového kódu.

## <a name="in-this-section"></a>V tomto oddílu
- [Struktura balíčku VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definuje strukturu balíčku VSPackage správy zdrojového kódu.

- [Související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Obsahuje seznam rozhraní a služeb souvisejících s balíčkem správy zdrojového kódu.

- [Poskytované služby](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Popisuje službu správy zdrojového kódu poskytovanou nástrojem VSPackage správy zdrojového kódu.

## <a name="related-sections"></a>Související oddíly
- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Popisuje, jak vytvořit prvek VSPackage správy zdrojového kódu, který neposkytuje pouze funkce správy zdrojového kódu, ale lze jej použít k přizpůsobení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní správy zdrojového kódu.
