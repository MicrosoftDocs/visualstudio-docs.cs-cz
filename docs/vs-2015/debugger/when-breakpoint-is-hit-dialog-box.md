---
title: Dialogové okno při volání zarážky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7cd140a22c435df0875c089a69476d3e1e61cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149410"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Dialogové okno Když je volána zarážka
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí tohoto dialogového okna můžete přizpůsobit akci, ke které dojde, když je dosaženo zarážky.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Tisk zprávy**  
 Vytiskne zprávu pomocí syntaxe DebuggerDisplay. Další informace najdete v tématu [použití atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Toto textové pole také podporuje speciální klíčová slova (například $ADDRESS), která lze použít samostatně nebo v rámci složených závorek DebuggerDisplay výrazu. K dispozici jsou uvedená klíčová slova v dialogovém okně.  
  
 **Pokračovat v provádění**  
 Tento ovládací prvek je povolen pouze v případě, že je vybrána **zpráva tisk zprávy** . Pomocí tohoto ovládacího prvku můžete použít zarážku jako zarážka s trasováním a trasovat tak provádění programu, a to místo přerušení, když je umístění dosaženo.  
  
## <a name="see-also"></a>Viz také  
 [Použití zarážek](../debugger/using-breakpoints.md)   
 [Používání atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
