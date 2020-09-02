---
title: Řízení provádění a vyhodnocení stavu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6476c925f37d70ab45bae129a8b8a379ee519c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152773"
---
# <a name="execution-control-and-state-evaluation"></a>Řízení provádění a vyhodnocení stavu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ladění aplikace vyžaduje implementaci takových funkcí řízení spouštění jako krokování do funkcí, zastavení na zarážekch a pokračování v provádění. Ladění sady Visual Studio zakládá své řízení provádění na události odesílané mezi komponentami ladicího programu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Řízení programu](../../extensibility/debugger/program-control.md)  
 Uvádí následující rutiny, které se vyskytují na úrovni programu: nastavení dalšího příkazu, spuštění, krokování, pokračování, pozastavení a obnovení.  
  
 [Metody související se zarážkou](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definuje vázané a nedokončené typy zarážek, které podporuje Visual Studio.  
  
 [Vyhodnocení zásobníku volání](../../extensibility/debugger/call-stack-evaluation.md)  
 Popisuje implementaci metod, které umožňují zobrazení rámců zásobníku volání v průběhu režimu přerušení.  
  
 [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Vysvětluje, jakým způsobem se při analýze a vyhodnocení výrazu zadaného do jednoho z oken rozhraní IDE účastní funkce ladění (DE), vyhodnocení výrazu (EE) a správce ladění relací.  
  
 [Události ovládacích prvků](../../extensibility/debugger/control-events.md)  
 Popisuje rozhraní používané k posílání událostí během kontrolovaného provádění programu.
