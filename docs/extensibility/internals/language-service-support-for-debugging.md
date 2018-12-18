---
title: Jazyková podpora služby pro ladění | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59c044f6ffc3f2cdf0749f0192f4b8fa458b00cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128649"
---
# <a name="language-service-support-for-debugging"></a>Jazyková podpora služby pro ladění
Služba jazyka poskytne funkce, které podporují ladicí program prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> rozhraní. Tyto funkce patří ověřování zarážky a poskytuje seznam výrazů k **automobily** okno.  
  
 Ale musíte mít vyhodnocovací filtr výrazů k ladění jazyka. Vyhodnocení výrazu je zodpovědná za vyhodnocení výrazů k vytvoření hodnoty při ladění. Informace o implementaci vyhodnocovače výrazů CLR najdete v tématu:  
  
-   [Vyhodnocovače výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Ukázka vyhodnocování spravovaných výrazů](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Výstup kompilátoru  
 Typ kompilátoru Určuje, co je potřeba provést k implementaci ladění pro svůj jazyk. Pokud vaše kompilátoru cílem operačního systému Windows a zapisuje do souboru pdb, můžete ladit programy s nativním kódem ladění modul, který je integrován do sady Visual Studio. Pokud vaše kompilátor vytváří Microsoft (MSIL intermediate language), můžete ladit programy se spravovaným kódem ladění modul, který je taky integrovaná do sady Visual Studio. Pokud vaše kompilátoru používá vlastní operačního systému nebo jiné běhového prostředí, potřebujete napsat vlastní modul ladění.  
  
 Další informace o implementaci ladění pro váš jazyk najdete v tématu [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) v sadě Visual Studio ladění SDK.