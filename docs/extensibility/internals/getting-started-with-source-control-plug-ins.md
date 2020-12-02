---
title: Začínáme se moduly plug-in správy zdrojových kódů | Microsoft Docs
description: Přečtěte si o vytváření modulu plug-in správy zdrojových kódů, který implementuje funkce definované v rozhraní API modulu plug-in správy zdrojového kódu pro použití ve správě verzí zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1524e4c4f08b272fd17973597d558efdabec41af
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480496"
---
# <a name="get-started-with-source-control-plug-ins"></a>Začínáme se moduly plug-in správy zdrojového kódu
Chcete-li vytvořit modul plug-in správy zdrojových kódů, je nutné vytvořit knihovnu DLL, která implementuje funkce definované v rozhraní API modulu plug-in správy zdrojového kódu, a poté pro registraci knihovny DLL pomocí nástroje, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ji bylo možné použít ve správě verzí zdrojového kódu.

 Pro moduly plug-in správy zdrojových kódů jsou k dispozici tři verze rozhraní API modulu plug-in správy zdrojových kódů (verze 1,1, 1,2 a 1,3). Rozhraní API pro modul plug-in správy zdrojových kódů popsané tady je verze 1,3. Byla navržena tak, aby byla plně kompatibilní s moduly plug-in správy zdrojového kódu podporujícími verze 1,1 a 1,2. V části [novinky v modulu plug-in správy zdrojových kódů rozhraní API verze 1,3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) najdete nové funkce podporované v nejnovější verzi rozhraní API modulu plug-in správy zdrojového kódu.

## <a name="in-this-section"></a>V této části
- [Postupy: Instalace modulu plug-in správy zdrojových kódů](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 Popisuje, jak provést položky registru, které jsou vyžadovány pro připojení knihovny DLL správy zdrojového kódu.

- [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu verze 1,3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Poskytuje stručný přehled změn, které byly provedeny v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1,3.

- [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu verze 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Poskytuje stručný přehled změn, které byly provedeny v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1,2.

## <a name="related-sections"></a>Související oddíly
- [Moduly plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md)

 Poskytuje úplný seznam všech prvků v rozhraní API modulu plug-in správy zdrojového kódu.

- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Definuje sadu SDK modulu plug-in správy zdrojových kódů a popisuje zahrnuté prostředky.
