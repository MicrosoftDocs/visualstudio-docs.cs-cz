---
title: Zápis běžné Vyhodnocovač výrazů modulu Runtime jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d93299702db0c56963eb8f404d05e8e67ab08b0
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276816"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Zápis běžné vyhodnocovač výrazů modulu runtime jazyka
> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka Chyba při vyhodnocování výrazu spravované](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Chyba při vyhodnocování výrazu (EE) je součástí ladicího stroje (DE), která zpracovává syntaxi a sémantiku programovací jazyk, který vytvořil laděného kódu. Výrazy musí být vyhodnocena v rámci kontextu programovací jazyk. Například v některých jazycích znamená výraz "A + B" "sum A a B." V jiných jazycích stejný výraz může znamenat "A nebo b" Díky tomu se samostatnou EE musí být napsané pro každý programovací jazyk, který generuje kód objektu k ladění v rozhraní IDE sady Visual Studio.  
  
 Některé aspekty ladění balíčku sady Visual Studio musí interpretovat kódu v rámci programovací jazyk. Například při provádění zastaví na zarážce, všechny výrazy, které uživatel zadal do **Watch** okna musí být vyhodnocen a zobrazí. Uživatel může změnit hodnotu místní proměnné tak, že zadáte výraz do **Watch** okno nebo do **okamžité** okna.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Common language runtime a výraz hodnocení](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Tento článek vysvětluje, že pokud provádíte integraci proprietární programovací jazyk v integrovaném vývojovém prostředí sady Visual Studio, zápis EE dokáže vyhodnocování výrazů v rámci speciální jazyk umožňuje zkompilovat pro jazyk Microsoft intermediate language (MSIL) aniž byste museli napsat ladicího stroje.  
  
 [Architektura vyhodnocovače výrazů](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Popisuje, jak požadovaná EE rozhraní implementace a volání common language runtime symbol zprostředkovatele (SP) a rozhraní vazače.  
  
 [Registrace vyhodnocovače výrazů](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Zaznamená, že EE musí registrovat jako objekt pro vytváření tříd se modul common language runtime a běhová prostředí sady Visual Studio.  
  
 [Implementace vyhodnocovače výrazů](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Popisuje, jak proces vyhodnocení výrazu obsahuje ladicí stroj (DE), poskytovatel symbolů (SP), objekt vazače a vyhodnocovací filtr výrazů (EE).  
  
 [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)  
 Popisuje, jak při pozastavení provádění ladit balíček volá DE k získání seznamu místních proměnných a argumentů.  
  
 [Vyhodnocení výrazu okna kukátka](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Popisuje, jakým způsobem volá DE k určení aktuální hodnoty každý výraz v svůj seznam ke zhlédnutí balíčku ladění sady Visual Studio.  
  
 [Změna hodnoty místní](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Vysvětluje, že v změna hodnoty lokální, má každý řádek v okně místních hodnot přidruženého objektu, který obsahuje název, typ a aktuální hodnoty místní hodnoty.  
  
 [Implementace vizualizérů typů a vlastních prohlížečů](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Vysvětluje, které rozhraní musí být implementováno jaká součást pro podporu vizualizérů typů a vlastních prohlížečů.  
  
## <a name="see-also"></a>Viz také:  
 [Rozšiřitelnost ladicího programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)