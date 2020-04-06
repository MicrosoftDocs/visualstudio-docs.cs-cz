---
title: Vytvoření modulu plug-in správy zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709174"
---
# <a name="create-a-source-control-plug-in"></a>Vytvoření modulu plug-in správy zdrojového kódu
Sada Visual Studio SDK poskytuje prostředky, které umožňují [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] přidat možnost ide správy zdrojového kódu do integrovaného vývojového prostředí. Umožňuje používat libovolnou datovou dll modulu Plug LL, která je v souladu s rozhraním API modulu plug-in správy zdrojového kódu uvedeným v této dokumentaci.

## <a name="in-this-section"></a>V tomto oddílu
- [Začínáme](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Popisuje, jak nainstalovat modul plug-in správy zdrojového kódu a zvýrazní aktuálně dostupné verze rozhraní API pro řízení zdrojového kódu.

- [Architektura](../../extensibility/internals/source-control-plug-in-architecture.md)

 Používá diagram architektury k vysvětlení integrace modulu plug-in správy zdrojového kódu s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ide.

- [Průvodce testováním](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Obsahuje pokyny k testování instalace a provozu modulu plug-in správy zdrojového kódu.

## <a name="related-sections"></a>Související oddíly
- [Vytvoření zdrojového ovládacího prvku VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Popisuje, jak vytvořit zdrojového ovládacího prvku VSPackage, který nejen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje funkce správy zdrojového kódu, ale nahrazuje ui správy zdrojového kódu.

- [Moduly plug-in pro směřuje zdroj](../../extensibility/source-control-plug-ins.md)

 Poskytuje úplný seznam všech prvků v rozhraní API modulu plug-in správy zdrojového kódu.

- [Řízení zdrojového kódu](../../extensibility/internals/source-control.md)

 Popisuje možnosti pro implementaci správy zdrojového [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kódu jako integrované funkce aplikace .
