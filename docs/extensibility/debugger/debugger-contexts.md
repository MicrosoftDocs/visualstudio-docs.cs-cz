---
title: Kontexty ladicího programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738973"
---
# <a name="debugger-contexts"></a>Kontexty ladicího programu
Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění ladicí modul (DE) pracuje současně v několika odlišných kontextech, a to následovně:

- Kontext kódu, který popisuje aktuální umístění v proudu spuštění programu.

- Kontext dokumentace nebo pozice, která popisuje aktuální pozici v rámci zdrojového dokumentu.

- Kontext vyhodnocení výrazu, který popisuje kontext, ve kterém bude hodnocení výrazu probíhat.

## <a name="in-this-section"></a>V tomto oddílu
 [Kontext kódu](../../extensibility/debugger/code-context.md) Popisuje kontext kódu jako adresu v proudu instrukcí programu v dnešní chodové architektury versus netradiční jazyky, kde kód nemusí být reprezentován pokyny, ale některé jiné prostředky.

 [Pozice dokumentu](../../extensibility/debugger/document-position.md) Definuje pozici dokumentu v aplikaci Visual Studio ladění pomocí abstrakce pozice ve zdrojovém souboru, jak je známo ide.

 [Kontext dokumentu](../../extensibility/debugger/document-context.md) Popisuje, co kontext dokumentu představuje v aplikaci Visual Studio ladění ve vztahu ke zdrojovému souboru. Také popisuje, jak obslužná rutina symbolu mapuje kontext kódu do kontextu dokumentace.

 [Kontext vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-context.md) Obsahuje informace o kontextu vyhodnocení výrazu v sadě Visual Studio. Například kontext vyhodnocení výrazu přidružený k rámečku zásobníku poskytuje kontext pro vyhodnocení místních proměnných, parametrů metody a členů třídy.

## <a name="related-sections"></a>Související oddíly
 [Koncepty ladění](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní ladění architektonických konceptů.

 [Ladění součástí](../../extensibility/debugger/debugger-components.md) Obsahuje přehled součástí ladění sady Visual Studio, které zahrnují ladicí modul (DE), vyhodnocení výrazu (EE) a obslužnou rutinu symbolu (SH).

 [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md) Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocení výrazů.
