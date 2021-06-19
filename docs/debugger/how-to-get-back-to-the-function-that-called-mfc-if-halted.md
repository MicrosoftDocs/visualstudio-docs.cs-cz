---
title: Vraťte se zpět k funkci, která volala MFC, pokud se | Microsoft Docs
description: Porozumíte tomu, jak se vrátit zpět k funkci, která volala MFC, pokud je provádění zastaveno v Visual Studio ladicím programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 31bbb064aad5a43738b2f345cf31a20767c55e69
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384678"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Postupy: Přechod zpět na funkci, která volala MFC při zastavení.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Pokud chcete nastavení změnit, zvolte **v nabídce Nástroje** možnost Nastavení importu a exportu.  Další informace najdete v tématu [Resetování nastavení.](../ide/environment-settings.md#reset-settings)

Pokud jste  v nabídce  Ladění použili příkaz Break k zastavení programu a skončili v MFC a jste si jisti, že problém je ve vašem kódu, můžete použít okno Zásobník volání a vrátit se zpět ke své funkci. Další informace najdete v tématu [Postupy: Použití okna zásobníku volání.](../debugger/how-to-use-the-call-stack-window.md)

Někdy se váš kód může přerušit v pumpě zpráv. V takovém případě není v zásobníku volání žádný uživatelský kód. Pokud se chcete tomuto problému vyhnout, můžete místo příkazu **Break** použít zarážky (například s podmínkami a počty přístupů). Další informace najdete v tématu [Zarážky a tracepointy](/previous-versions/ktf38f66(v=vs.100)).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Přejděte do funkce, ze které byla volána knihovna MFC.

- Použijte okno **Zásobník** volání.

## <a name="see-also"></a>Viz také

- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)