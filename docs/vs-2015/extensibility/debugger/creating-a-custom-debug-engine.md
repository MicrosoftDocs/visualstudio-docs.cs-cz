---
title: Vytvoření vlastního ladicího stroje | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 516fda63a1a36e407a71cd6711ecdfabdc1e5e58
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784689"
---
# <a name="creating-a-custom-debug-engine"></a>Vytvoření vlastního ladicího stroje
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ladicí stroj (DE) je komponenta, která umožňuje ladění konkrétní za běhu architektury. Obvykle existuje pouze jedna implementace DE pro každé prostředí za běhu.  
  
> [!NOTE]
>  I když existují samostatné implementace DE pro příkazů jazyka Transact-SQL a JScript, sdílet jeden DE VBScript a JScript.  
  
 Zavedenými spolupracuje s překladač nebo operace systému k poskytování těchto služeb ladění jako ovládací prvek, zarážky a výraz zkušební spuštění. Tyto služby jsou implementované pomocí rozhraní DE a může způsobit, že ladicí program pro přechod mezi různé provozní režimy. Další informace najdete v tématu [provozní režimy](../../extensibility/debugger/operational-modes.md).  
  
 Vytváří se Zavedenými se skládá z následujících kroků:  
  
1.  Registrace Zavedenými pomocí sady Visual Studio  
  
2.  Povolení ladění programu  
  
3.  Ovládací prvek a stav zkušební spuštění  
  
4.  Odesílání událostí  
  
5.  Ukončení a odpojení  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Registrace vlastního ladicího stroje](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Popisuje kroky potřebné k registraci ladicího stroje pomocí sady Visual Studio, takže je možné.  
  
 [Povolení ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Vysvětluje, že před vaše DE můžete ladit program, musíte nejprve spusťte DE nebo připojit k existující program.  
  
 [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Tento článek popisuje, proč ladění aplikace vyžaduje implementaci funkce řízení provádění.  
  
 [Odesílání událostí](../../extensibility/debugger/sending-events.md)  
 Popisuje komunikaci ladicího programu a DE jako model událostí založené na modelu DCOM.  
  
 [Ukončení a odpojení](../../extensibility/debugger/termination-and-detaching.md)  
 Vysvětluje, jak dosáhnout normální ukončení, což znamená, že neexistují žádné zarážky, výjimky, chyby za běhu nebo nekonečné smyčky v aplikaci k ladění.  
  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumenty volání pořadí událostí, ke kterým dochází v relaci ladění.  
  
 [Postupy: Ladění vlastního ladicího stroje](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Vysvětluje, jak ladit vlastní DE.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřitelnost programu Visual Studio Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

