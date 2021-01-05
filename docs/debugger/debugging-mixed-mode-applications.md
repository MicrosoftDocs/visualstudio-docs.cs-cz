---
title: Ladění aplikací Mixed-Mode | Microsoft Docs
description: Ladění aplikace se smíšeným režimem, což je aplikace, která kombinuje nativní kód se spravovaným kódem, který běží v modulu CLR (Common Language Runtime) v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4137e7a73032a34276416b9640dd608b96b660a4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728327"
---
# <a name="debugging-mixed-mode-applications"></a>Ladění aplikací ve smíšeném režimu
Aplikace pracující v kombinovaném režimu je libovolná aplikace, která kombinuje nativní kód (jazyk C++) se spravovaným kódem (například jazyk Visual Basic, Visual C# nebo C++, který běží na modulu CLR). Ladění aplikací se smíšeným režimem je v podstatě transparentní v nástroji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ; není příliš odlišné od ladění aplikace v jednom režimu. Existuje však několik důležitých informací.

## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Povolení příkazů Edit a Continue jazyka C++ v kombinovaném režimu ladění

Pokud chcete povolit příkaz Upravit a pokračovat pro jazyk C++, přečtěte si téma [povolení a zakázání funkce upravit a pokračovat](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Pokud chcete používat příkazy Edit a Continue (Upravit a pokračovat) jazyka C++ v sadě Visual Studio 2013, budete muset přejít na starší verzi modulu pro ladění. Přečtěte si téma [Přepnutí do spravovaného režimu kompatibility v Visual Studio 2013](https://devblogs.microsoft.com/devops/switching-to-managed-compatibility-mode-in-visual-studio-2013/) na blogu Správa životního cyklu aplikací Microsoft.

## <a name="property-evaluation-in-mixed-mode-applications"></a>Vyhodnocení vlastnosti v aplikacích pracujících v kombinovaném režimu
 Vyhodnocení vlastností ladicím programem je v aplikaci pracující v kombinovaném režimu náročná operace. V důsledku toho se operace ladění, jako je například krokování, mohou zdát pomalé. Další informace najdete v tématu [krokování](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)). Pokud se při ladění v kombinovaném režimu setkáváte s nízkým výkonem, lze vyhodnocení vlastností vypnout v oknech ladicího programu.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

### <a name="to-turn-off-property-evaluation"></a>Chcete-li vypnout vyhodnocení vlastností

1. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

2. V dialogovém okně **Možnosti** otevřete složku **ladění** a vyberte kategorii **Obecné** .

3. Zrušte zaškrtnutí políčka **Povolit vyhodnocování vlastností a další volání implicitní funkce** .

   Vzhledem k tomu, že se nativní a spravované zásobníky volání liší, ladicí program nemůže vždy pro smíšený kód stanovit úplný zásobník volání. Když nativní kód volá spravovaný kód, lze zaznamenat některé nesrovnalosti. Další informace naleznete v části [smíšený kód a chybějící informace v okně zásobník volání](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).

## <a name="see-also"></a>Viz také

- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)