---
title: Ladění ve smíšeném režimu aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4170a63597611bb190a6b3cf365b6dbced1bc9ae
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389387"
---
# <a name="debugging-mixed-mode-applications"></a>Ladění aplikací ve smíšeném režimu
Aplikace pracující v kombinovaném režimu je libovolná aplikace, která kombinuje nativní kód (jazyk C++) se spravovaným kódem (například jazyk Visual Basic, Visual C# nebo C++, který běží na modulu CLR). Ladění aplikací ve smíšeném režimu je z velké části transparentní [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; není příliš odlišné od ladění režimu jedné aplikace. Existuje však několik důležitých informací.

## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Povolení příkazů Edit a Continue jazyka C++ v kombinovaném režimu ladění

Chcete-li upravit a pokračovat jazyka C++, naleznete v tématu [povolení a zákaz operace upravit a pokračovat](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Pokud chcete používat příkazy Edit a Continue (Upravit a pokračovat) jazyka C++ v sadě Visual Studio 2013, budete muset přejít na starší verzi modulu pro ladění. Zobrazit [přepnutí do spravovaného režimu kompatibility v sadě Visual Studio 2013](https://blogs.msdn.microsoft.com/devops/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013/) na blogu Microsoft Application Lifecycle Management.

## <a name="property-evaluation-in-mixed-mode-applications"></a>Vyhodnocení vlastnosti v aplikacích pracujících v kombinovaném režimu
 Vyhodnocení vlastností ladicím programem je v aplikaci pracující v kombinovaném režimu náročná operace. V důsledku toho se operace ladění, jako je například krokování, mohou zdát pomalé. Další informace najdete v tématu [krokování](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)). Pokud se při ladění v kombinovaném režimu setkáváte s nízkým výkonem, lze vyhodnocení vlastností vypnout v oknech ladicího programu.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [Resetovat nastavení](../ide/environment-settings.md#reset-settings).

### <a name="to-turn-off-property-evaluation"></a>Chcete-li vypnout vyhodnocení vlastností

1. Na **nástroje** nabídce zvolte **možnosti**.

2. V **možnosti** dialogovém okně Otevřít **ladění** a pak zvolte položku **Obecné** kategorie.

3. Zrušte **povolit vyhodnocování vlastností a jiných implicitních volání funkcí** zaškrtávací políčko.

   Vzhledem k tomu, že se nativní a spravované zásobníky volání liší, ladicí program nemůže vždy pro smíšený kód stanovit úplný zásobník volání. Když nativní kód volá spravovaný kód, lze zaznamenat některé nesrovnalosti. Další informace najdete v tématu [smíšený kód a chybějící informace v okně zásobník volání](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).

## <a name="see-also"></a>Viz také

- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)