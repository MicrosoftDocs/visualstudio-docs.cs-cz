---
title: Vytvoření balíčku VSPackage správy zdrojového kódu | Microsoft Docs
description: Naučte se vytvořit balíček VSPackage správy zdrojového kódu, který vytváří hloubkovou integrační cestu pro správu zdrojového kódu pro integraci se sadou Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 69e526cea292544c725abc7ffb54d0b29ad88403
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305591"
---
# <a name="create-a-source-control-vspackage"></a>Vytvoření balíčku VSPackage správy zdrojového kódu
Tato dokumentace obsahuje odkazy na přehled architektury balíčku pro správu zdrojového kódu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , který je integrovaný s, rozhraní API definované rozhraními, která se mají implementovat, a služby, které se mají využít, a ukázku, která ilustruje jednoduchou implementaci balíčku správy zdrojového kódu.

 Pomocí balíčku VSPackage správy zdrojového kódu můžete vytvořit hloubkovou integrační cestu pro správu zdrojového kódu, se kterou chcete integrovat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Umožňuje balíčku obejít výchozí uživatelské rozhraní správy zdrojového kódu hostované nástrojem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , reagovat na požadavky na správu zdrojového kódu v systému projektu a interagovat s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komponentami, jako je **Průzkumník řešení**. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umožňuje partnerům pomocí mechanismu vytvořit VSPackage, který se dá integrovat s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] použitím modelu služby.

## <a name="in-this-section"></a>V této části
- [Začínáme](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Popisuje balíček správy zdrojového kódu, což je pokročilejší alternativa k modulu plug-in správy zdrojových kódů pro implementaci funkcí správy zdrojového kódu v nástroji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Architektura](../../extensibility/internals/source-control-vspackage-architecture.md)

 Prezentuje diagram a vysvětluje komponenty balíčku správy zdrojového kódu.

- [Funkce](../../extensibility/internals/source-control-vspackage-features.md)

 Popisuje různé funkce balíčku správy zdrojového kódu.

- [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Popisuje strukturu VSPackage, kterou musí balíček správy zdrojového kódu implementovat pro rozsáhlou integraci.

## <a name="related-sections"></a>Související oddíly
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Popisuje, jak vytvořit modul plug-in správy zdrojového kódu, který poskytuje funkce správy zdrojového kódu v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelském rozhraní správy zdrojového kódu (UI).

- [Správa zdrojového kódu](../../extensibility/internals/source-control.md)

 Popisuje možnosti pro implementaci správy zdrojového kódu jako integrované funkce nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
