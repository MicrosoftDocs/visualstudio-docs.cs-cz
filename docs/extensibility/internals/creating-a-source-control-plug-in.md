---
title: Vytváření modulu plug-in správy zdrojových kódů | Microsoft Docs
description: Naučte se, jak vytvořit modul plug-in správy zdrojového kódu, který přidá schopnost správy zdrojového kódu do integrovaného vývojového prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc302ee7327740380bb02e28c99e5117c926c7bc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056893"
---
# <a name="create-a-source-control-plug-in"></a>Vytvoření modulu plug-in správy zdrojového kódu
Sada Visual Studio SDK poskytuje prostředky, které umožňují přidat schopnost správy zdrojového kódu do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí (IDE). Umožňuje použít všechny knihovny DLL modulu plug-in, které jsou v souladu s rozhraním API modulu plug-in správy zdrojového kódu popsaným v této dokumentaci.

## <a name="in-this-section"></a>V této části
- [Začínáme](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Popisuje, jak nainstalovat modul plug-in správy zdrojových kódů a zvýrazní aktuálně dostupné verze rozhraní API modulu plug-in správy zdrojových kódů.

- [Architektura](../../extensibility/internals/source-control-plug-in-architecture.md)

 Pomocí diagramu architektury vysvětluje integraci modulu plug-in správy zdrojového kódu s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraním IDE.

- [Průvodce testováním](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Poskytuje pokyny, jak otestovat instalaci a provoz modulu plug-in správy zdrojového kódu.

## <a name="related-sections"></a>Související oddíly
- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Popisuje, jak vytvořit prvek VSPackage správy zdrojového kódu, který neposkytuje pouze funkce správy zdrojového kódu, ale nahrazuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelské rozhraní správy zdrojového kódu.

- [Moduly plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md)

 Poskytuje úplný seznam všech prvků v rozhraní API modulu plug-in správy zdrojového kódu.

- [Správa zdrojového kódu](../../extensibility/internals/source-control.md)

 Popisuje možnosti pro implementaci správy zdrojového kódu jako integrované funkce nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
