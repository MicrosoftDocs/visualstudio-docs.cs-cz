---
title: Podpora jazykové služby pro ladění | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707438"
---
# <a name="language-service-support-for-debugging"></a>Podpora služby jazyka pro ladění
Služba jazyka může poskytovat funkce, které podporují ladicí program prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> rozhraní. Tyto funkce zahrnují ověřování zarážek a poskytnutí seznamu výrazů do okna **Automatické** hodnoty.

 Pro ladění jazyka ale musíte mít vyhodnocovací filtr výrazů. Vyhodnocovací filtr výrazů zodpovídá za vyhodnocení výrazů pro vytváření hodnot během ladění. Informace o implementaci vyhodnocovacích vyhodnocení výrazu CLR najdete v těchto tématech:

- [Vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Výstup kompilátoru
 Typ kompilátoru Určuje, co je třeba provést k implementaci ladění pro váš jazyk. Pokud se váš kompilátor zaměřuje na operační systém Windows a zapisuje soubor. pdb, můžete ladit programy pomocí modulu ladění nativního kódu, který je integrovaný do sady Visual Studio. Pokud váš kompilátor vytváří jazyk MSIL (Microsoft Intermediate Language), můžete ladit programy pomocí modulu ladění spravovaného kódu, který je také integrován do sady Visual Studio. Pokud je váš kompilátor cílen na proprietární operační systém nebo jiné běhové prostředí, musíte napsat vlastní modul ladění.

 Další informace o implementaci ladění pro váš jazyk naleznete v tématu [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) v sadě Visual Studio Debugging SDK.
