---
title: Vytvoření vlastního ladicího stroje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64829303"
---
# <a name="creating-a-custom-debug-engine"></a>Vytvoření vlastního ladicího stroje
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ladicí stroj (DE) je komponenta, která umožňuje ladění konkrétní architektury run-time. Obvykle je k dispozici pouze jedna DE Implementation pro každé prostředí za běhu.  
  
> [!NOTE]
> I když existují samostatné DE implementací pro Transact-SQL a JScript, VBScript a JScript sdílí jeden DE.  
  
 DE funguje s překladačem nebo operačním systémem pro poskytování takových služeb ladění jako řízení spouštění, zarážky a vyhodnocení výrazu. Tyto služby jsou implementovány prostřednictvím rozhraní DE a mohou způsobit přechod ladicího programu mezi různými provozními režimy. Další informace najdete v tématu [provozní režimy](../../extensibility/debugger/operational-modes.md).  
  
 Vytváření DE se skládá z následujících kroků:  
  
1. Registrace DE se sadou Visual Studio  
  
2. Povolení ladění programu  
  
3. Řízení provádění a vyhodnocení stavu  
  
4. Odesílání událostí  
  
5. Ukončení a odpojení  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Registrace vlastního ladicího stroje](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Vysvětluje kroky potřebné k registraci ladicího stroje se sadou Visual Studio, aby jej bylo možné použít.  
  
 [Povolení ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Vysvětluje, že před tím, než může příkaz DE ladit program, je třeba nejprve spustit příkaz DE nebo ho připojit k existujícímu programu.  
  
 [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Popisuje, proč ladění aplikace vyžaduje implementaci funkcí řízení spouštění.  
  
 [Odesílání událostí](../../extensibility/debugger/sending-events.md)  
 Popisuje komunikaci mezi ladicím programem a DE jako modelem události na základě modelu DCOM.  
  
 [Ukončení a odpojení](../../extensibility/debugger/termination-and-detaching.md)  
 Vysvětluje, jak dosáhnout normálního ukončení, což znamená, že neexistují žádné zarážky, výjimky, chyby za běhu nebo nekonečné smyčky v aplikaci, která se má ladit.  
  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumentuje pořadí volání událostí, ke kterým došlo v relaci ladění.  
  
 [Postupy: Ladění vlastního ladicího stroje](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Vysvětluje, jak ladit vlastní DE.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřitelnost programu Visual Studio Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
