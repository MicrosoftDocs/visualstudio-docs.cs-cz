---
title: Správa zdrojového kódu VSPackage Konstrukční prvky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5e94829f781c058d9b0ea56cdec6c03c71ffe0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704998"
---
# <a name="source-control-vspackage-design-elements"></a>Prvky návrhu balíčku VSPackage správy zdrojového kódu
Témata v této části popisují strukturu správy zdrojového kódu VSPackage musí implementovat pro hlubokou integraci. Obsahuje také seznam rozhraní a služeb, které může implementovat ovládací prvek zdrojového kódu VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a rozhraní a služby, které může nástroj VSPackage správy zdrojového kódu použít z jiných součástí pro podporu modelu a funkčnosti správy zdrojového kódu.

## <a name="in-this-section"></a>V tomto oddílu
- [Struktura balíčku VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definuje strukturu správy zdrojového kódu VSPackage.

- [Související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Seznam rozhraní a služeb souvisejících s balíčkem správy zdrojového kódu.

- [Poskytované služby](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Popisuje službu správy zdrojového kódu poskytovanou prvkem správy zdrojového kódu VSPackage.

## <a name="related-sections"></a>Související oddíly
- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Popisuje, jak vytvořit zdrojového ovládacího prvku VSPackage, který poskytuje nejen funkce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] správy zdrojového kódu, ale lze jej přizpůsobit ui správy zdrojového kódu.
