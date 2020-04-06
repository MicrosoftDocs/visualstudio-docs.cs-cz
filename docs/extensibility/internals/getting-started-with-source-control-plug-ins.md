---
title: Začínáme s moduly plug-in správy zdrojového kódu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: efc21e07830614d9d3041b2d2d231fd82c652114
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708350"
---
# <a name="get-started-with-source-control-plug-ins"></a>Začínáme s moduly plug-in správy zdrojového kódu
Chcete-li vytvořit modul plug-in správy zdrojového kódu, musíte vytvořit dll, která implementuje funkce definované [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v rozhraní PLUG-in správy zdrojového kódu a potom zaregistrovat dll s, aby byla k dispozici pro použití ve správě verze zdrojového kódu.

 Pro moduly plug-in správy zdrojového kódu jsou k dispozici tři verze rozhraní API modulu plug-in správy zdrojového kódu (verze 1.1, 1.2 a 1.3). Rozhraní API modulu plug-in správy zdrojového kódu zde je verze 1.3. Byl navržen tak, aby byl plně kompatibilní s moduly plug-in pro řízení zdrojů podporujícími verze 1.1 a 1.2. Co je nového v části [Rozhraní api plug-in správy zdrojového kódu verze 1.3,](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) podrobně popisuje nové funkce podporované v nejnovější verzi rozhraní API modulu plug-in správy zdrojového kódu.

## <a name="in-this-section"></a>V tomto oddílu
- [Postup: Instalace modulu plug-in pro řízení zdrojového kódu](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 Popisuje, jak vytvořit položky registru, které jsou nutné k připojení ke zdrojovému ovládacímu prvku DLL.

- [Co je nového v rozhraní Plug-in Plug-in API správy zdrojového kódu verze 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Poskytuje stručný přehled změn, které byly provedeny v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.3.

- [Co je nového v rozhraní Plug-in Plug-in API správy zdrojového kódu verze 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Poskytuje stručný přehled změn, které byly provedeny v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2.

## <a name="related-sections"></a>Související oddíly
- [Moduly plug-in pro směřuje zdroj](../../extensibility/source-control-plug-ins.md)

 Poskytuje úplný seznam všech prvků v rozhraní API modulu plug-in správy zdrojového kódu.

- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Definuje sadu Plug-in source Control SDK a popisuje zahrnuté prostředky.
