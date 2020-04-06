---
title: Podpora jazykových služeb pro ladění | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707438"
---
# <a name="language-service-support-for-debugging"></a>Podpora služby jazyka pro ladění
Služba jazyka může poskytovat funkce, které podporují <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> ladicí program prostřednictvím rozhraní. Mezi tyto funkce patří ověřování zarážek a poskytování seznamu výrazů do okna **Autos.**

 Však musíte mít vyhodnocení výrazu ladit váš jazyk. Vyhodnocení výrazu je zodpovědný za vyhodnocení výrazy vytvářet hodnoty při ladění. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu:

- [Vyhodnocení výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Výstup kompilátoru
 Typ kompilátoru určuje, co je třeba provést k implementaci ladění pro váš jazyk. Pokud kompilátor cílí na operační systém Windows a zapíše soubor PDB, můžete ladit programy pomocí nativního ladicího modulu kódu, který je integrován do sady Visual Studio. Pokud kompilátor vytváří zprostředkující jazyk Microsoftu (MSIL), můžete ladit programy pomocí modulu ladění spravovaného kódu, který je také integrován do sady Visual Studio. Pokud váš kompilátor cílí na proprietární operační systém nebo jiné prostředí runtime, musíte napsat vlastní ladicí modul.

 Další informace o implementaci ladění pro váš jazyk naleznete v [tématu Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) v sadě Visual Studio Ladění SDK.
