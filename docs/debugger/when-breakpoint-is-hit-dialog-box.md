---
title: Dialogové okno při volání zarážky | Microsoft Docs
description: Použijte, pokud je dosaženo zarážky k určení akce při přerušení. Můžete určit, že se má zpráva vytisknout, a toto spuštění bude pokračovat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bfb5099bd0fab17cd983af4e16a435fd192a1668
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883867"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Dialogové okno Když je volána zarážka
Pomocí tohoto dialogového okna můžete přizpůsobit akci, ke které dojde, když je dosaženo zarážky.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Tisk zprávy** Vytiskne zprávu pomocí syntaxe DebuggerDisplay. Další informace najdete v tématu [použití atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Toto textové pole také podporuje speciální klíčová slova (například $ADDRESS), která lze použít samostatně nebo v rámci složených závorek DebuggerDisplay výrazu. K dispozici jsou uvedená klíčová slova v dialogovém okně.

 **Pokračovat v provádění** Tento ovládací prvek je povolen pouze v případě, že je vybrána **zpráva tisk zprávy** . Pomocí tohoto ovládacího prvku můžete použít zarážku jako zarážka s trasováním a trasovat tak provádění programu, a to místo přerušení, když je umístění dosaženo.

## <a name="see-also"></a>Viz také
- [Použití zarážek](../debugger/using-breakpoints.md)
- [Používání atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)