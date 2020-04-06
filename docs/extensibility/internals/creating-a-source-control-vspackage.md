---
title: Vytvoření balíčku VSPackage správy zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709193"
---
# <a name="create-a-source-control-vspackage"></a>Vytvoření zdrojového ovládacího prvku VSPackage
Tato dokumentace obsahuje odkazy na přehled architektury balíčku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]správy zdrojového kódu integrovaného s rozhraním API, které je definováno rozhraními, která mají být implementována, a na spotřebované služby a ukázku, která ilustruje jednoduchou implementaci balíčku správy zdrojového kódu.

 Pomocí správy zdrojového kódu VSPackage můžete vytvořit cestu hluboké [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integrace pro správou zdrojového kódu, která se integruje s aplikací . Umožňuje balíček obejít výchozí řízení zdrojového [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kódu u kterého hostované , reagovat na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] požadavky správy zdrojového kódu ze systému projektu a pracovat s součástmi, jako je **průzkumník řešení**. Umožňuje [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partnerům s mechanismem vytvořit VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] který lze integrovat s pomocí modelu služby.

## <a name="in-this-section"></a>V tomto oddílu
- [Začínáme](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Popisuje balíček správy zdrojového kódu, což je pokročilejší alternativa k modulu plug-in správy zdrojového kódu pro implementaci funkcí správy zdrojového kódu v . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

- [Architektura](../../extensibility/internals/source-control-vspackage-architecture.md)

 Představuje diagram a vysvětluje součásti balíčku správy zdrojového kódu.

- [Funkce](../../extensibility/internals/source-control-vspackage-features.md)

 Popisuje různé funkce balíčku správy zdrojového kódu.

- [Konstrukční prvky](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Popisuje strukturu VSPackage, který musí implementovat balíček správy zdrojového kódu pro hlubokou integraci.

## <a name="related-sections"></a>Související oddíly
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Popisuje, jak vytvořit modul plug-in správy zdrojového kódu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] který poskytuje funkce správy zdrojového kódu v uživatelském rozhraní správy zdrojového kódu.

- [Řízení zdrojového kódu](../../extensibility/internals/source-control.md)

 Popisuje možnosti pro implementaci správy zdrojového [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kódu jako integrované funkce aplikace .
