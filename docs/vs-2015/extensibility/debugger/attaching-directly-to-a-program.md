---
title: Připojení přímo k programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab49163fc1474b541df3bc1b54d336574761baa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147998"
---
# <a name="attaching-directly-to-a-program"></a>Připojení přímo k programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uživatelé, kteří chtějí ladit programy v procesu, který je již spuštěn, obvykle následují za tímto způsobem:  
  
1. V integrovaném vývojovém prostředí vyberte příkaz **ladit procesy** v nabídce **nástroje** .  
  
    Zobrazí se dialogové okno **procesy** .  
  
2. Vyberte proces a klikněte na tlačítko **připojit** .  
  
    Zobrazí se dialogové okno **připojit k procesu** , v němž jsou uvedeny všechny moduly ladění (des) nainstalované v počítači.  
  
3. Zadejte algoritmus DEs, který se použije k ladění vybraného procesu, a pak klikněte na **OK**.  
  
   Ladicí balíček spustí relaci ladění a předá do něj seznam DEs. Relace ladění zase předá tento seznam spolu s funkcí zpětného volání na vybraný proces a pak požádá o vytvoření výčtu spuštěných programů.  
  
   V rámci reakce na požadavek uživatele balíček ladění vytvoří instanci správce ladění relace (SDM) a předá do něj seznam zvolených algoritmů DEs. Společně se seznamem ladicí balíček předá rozhraní SDM rozhraní [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) . Ladicí balíček předá na vybraný proces seznam DEs voláním [IDebugProcess2:: Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Model SDM pak na portu zavolá [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) , aby se vytvořil výčet programů spuštěných v procesu.  
  
   Od tohoto okamžiku se každý ladicí stroj připojí k programu přesně tak, jak je popsáno v části [připojení po spuštění](../../extensibility/debugger/attaching-after-a-launch.md), se dvěma výjimkami.  
  
   V případě efektivity je algoritmus DEs implementovaný pro sdílení adresního prostoru se službou SDM seskupený tak, aby každý DE měl sadu programů, ke kterým se připojí. V tomto případě volání [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) volá [IDebugEngine2:: Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) a předá jí pole programů, ke kterým se připojí.  
  
   Druhou výjimkou je, že události spuštění odesílané nástrojem DE Attach do programu, který je již spuštěn, obvykle nezahrnují událost vstupního bodu.  
  
## <a name="see-also"></a>Viz také  
 [Posílání událostí po spuštění](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)
