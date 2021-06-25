---
title: Kontexty ladicího | Microsoft Docs
description: 'Zjistěte, jak Visual Studio modul ladění funguje v různých kontextech: kontextu kódu, kontextu dokumentace nebo pozici a kontextu vyhodnocení výrazu.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5103561a420c3836f60a22790335522a83798966
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903668"
---
# <a name="debugger-contexts"></a>Kontexty ladicího programu
Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění funguje ladicí modul současně v několika různých kontextech, a to následujícím způsobem:

- Kontext kódu, který popisuje aktuální umístění v datovém proudu provádění programu.

- Kontext nebo pozice dokumentace, která popisuje aktuální pozici ve zdrojovém dokumentu.

- Kontext vyhodnocení výrazu, který popisuje kontext, ve kterém se bude vyhodnocení výrazu odehrát.

## <a name="in-this-section"></a>V této části
 [Kontext kódu](../../extensibility/debugger/code-context.md) Probírá kontext kódu jako adresu ve streamu instrukcí programu v dnešní architektuře run-time v porovnání s netradičními jazyky, kde kód nemusí být reprezentován instrukcemi, ale některými dalšími prostředky.

 [Pozice dokumentu](../../extensibility/debugger/document-position.md) Definuje pozici dokumentu Visual Studio ladění pomocí abstrakce pozice ve zdrojovém souboru, kterou integrované vývojové prostředí (IDE) označuje.

 [Kontext dokumentu](../../extensibility/debugger/document-context.md) Popisuje, co kontext dokumentu představuje Visual Studio ladění ve vztahu ke zdrojovému souboru. Popisuje také, jak obslužná rutina symbolů mapuje kontext kódu na kontext dokumentace.

 [Kontext vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-context.md) Poskytuje informace o kontextu vyhodnocení výrazu v Visual Studio. Například kontext vyhodnocení výrazu přidružený k rámu zásobníku poskytuje kontext pro vyhodnocení místních proměnných, parametrů metody a členů třídy.

## <a name="related-sections"></a>Související oddíly
 [Koncepty ladění](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní koncepty architektury ladění.

 [Ladění komponent](../../extensibility/debugger/debugger-components.md) Poskytuje přehled komponent ladění Visual Studio, mezi které patří ladicí modul (DE), vyhodnocovač výrazů (EE) a obslužná rutina symbolů (SH).

 [Ladění úloh](../../extensibility/debugger/debugging-tasks.md) Obsahuje odkazy na různé úlohy ladění, například spuštění programu a vyhodnocení výrazů.
