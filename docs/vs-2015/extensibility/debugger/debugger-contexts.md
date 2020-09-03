---
title: Kontexty ladicího programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 771a3cd8ae25173f3033b3a3229e516570f5dedc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200633"
---
# <a name="debugger-contexts"></a>Kontexty ladicího programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ladicí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] stroj (de) v ladění funguje současně v několika různých kontextech, a to následujícím způsobem:  
  
- Kontext kódu, který popisuje aktuální umístění v datovém proudu spuštění programu.  
  
- Kontext nebo pozice dokumentace, která popisuje aktuální pozici ve zdrojovém dokumentu.  
  
- Kontext vyhodnocení výrazu, který popisuje kontext, ve kterém bude provedeno vyhodnocení výrazu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Kontext kódu](../../extensibility/debugger/code-context.md)  
 Popisuje kontext kódu jako adresu v streamu instrukcí programu v dnešních architekturách za běhu versus netradiční jazyky, kde kód nemusí být reprezentován pokyny, ale jinými způsoby.  
  
 [Pozice dokumentu](../../extensibility/debugger/document-position.md)  
 Definuje pozici dokumentu v ladění sady Visual Studio prostřednictvím abstrakce pozice ve zdrojovém souboru, jak je známo rozhraní IDE.  
  
 [Kontext dokumentu](../../extensibility/debugger/document-context.md)  
 Popisuje, co kontext dokumentu představuje v ladění sady Visual Studio ve vztahu ke zdrojovému souboru. Také popisuje, jak obslužná rutina symbolů mapuje kontext kódu do kontextu dokumentace.  
  
 [Kontext vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-context.md)  
 Poskytuje informace o kontextu vyhodnocení výrazu v aplikaci Visual Studio. Například kontext vyhodnocení výrazu spojený s rámcem zásobníku poskytuje kontext pro vyhodnocení místních proměnných, parametrů metody a členů třídy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Koncepty ladění](../../extensibility/debugger/debugger-concepts.md)  
 Popisuje hlavní koncepty architektury ladění.  
  
 [Ladění součástí](../../extensibility/debugger/debugger-components.md)  
 Poskytuje přehled komponent pro ladění sady Visual Studio, které zahrnují modul ladění (DE), vyhodnocovací filtr výrazů (EE) a popisovač symbolů (SH).  
  
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)  
 Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocování výrazů.
