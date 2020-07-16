---
title: 'IDebugProgram2:: Execute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 676a3a7d184c1f34cafcfc2b2a4dd7a1c3f81a95
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387327"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pokračuje v běhu tohoto programu ze stavu Zastaveno. Veškerý předchozí stav spuštění (například krok) je vymazán a program se spustí znovu.  
  
> [!NOTE]
> Tato metoda je zastaralá. Místo toho použijte metodu [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) .  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Když uživatel spustí spuštění z zastaveného stavu v jiném vlákně programu, je tato metoda volána v tomto programu. Tato metoda je volána také v případě, že uživatel vybere příkaz **Start** z nabídky **ladění** v rozhraní IDE. Implementace této metody může být jednoduchá jako volání metody [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) v aktuálním vlákně v programu.  
  
> [!WARNING]
> Neodesílat událost zastavení nebo okamžitou (synchronní) událost k [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) během zpracování tohoto volání; v opačném případě může ladicí program přestat reagovat.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Událostí](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Obnovit](../../../extensibility/debugger/reference/idebugthread2-resume.md)
