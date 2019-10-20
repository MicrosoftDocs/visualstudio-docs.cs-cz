---
title: Automatické pozastavení funkce
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd399d78ac43085d89958ba358954f9e6cefe521
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606529"
---
# <a name="automatic-feature-suspension"></a>Automatické pozastavení funkce

Pokud velikost dostupné systémové paměti klesne na 200 MB nebo méně, Visual Studio zobrazí v editoru kódu následující zprávu:

![Text výstrahy, která pozastavuje úplnou analýzu řešení](../code-quality/media/fsa_alert.png)

Když Visual Studio zjistí stav nedostatku paměti, automaticky pozastaví určité pokročilé funkce, aby bylo možné udržet stabilní. Visual Studio bude i nadále fungovat jako dřív, ale jeho výkon je degradován.

V podmínkách nedostatku paměti proběhne následující akce:

- Úplná analýza řešení pro vizuál C# a Visual Basic je zakázaná.

- Režim [uvolňování paměti](/dotnet/standard/garbage-collection/index) (GC) s nízkou latencí pro C# vizuál a Visual Basic je zakázaný.

- Mezipaměti sady Visual Studio jsou vyprázdněné.

## <a name="improve-visual-studio-performance"></a>Zlepšení výkonu sady Visual Studio

Tipy a triky, jak zlepšit výkon sady Visual Studio při práci s velkými řešeními nebo s nízkými paměťovými podmínkami, najdete v tématu [požadavky na výkon pro velká řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Úplná analýza řešení je pozastavená.

Ve výchozím nastavení je úplná analýza řešení povolená pro Visual Basic a zakázaná C#pro Visual. V případě nedostatku paměti se ale úplná analýza řešení automaticky zakáže pro Visual Basic i vizuál C#bez ohledu na jejich nastavení v dialogovém okně Možnosti. Úplnou analýzu řešení však můžete znovu povolit kliknutím na tlačítko **znovu povolit** na informačním panelu, když v dialogovém okně Možnosti zaškrtnete políčko **Povolit úplnou analýzu řešení** , nebo restartováním sady Visual Studio. Dialogové okno Možnosti vždy zobrazuje aktuální nastavení úplné analýzy řešení. Další informace najdete v tématu [Postup: povolení a zákaz úplné analýzy řešení](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Nízká latence GC – vypnuto

Pokud chcete znovu povolit režim s nízkou latencí GC, restartujte Visual Studio. Ve výchozím nastavení Visual Studio umožňuje režim GC s nízkou latencí, kdykoli píšete, abyste zajistili, že váš zápis nebude blokovat žádné operace GC. Pokud ale stav nedostatku paměti způsobí, že Visual Studio zobrazí upozornění na automatické pozastavení, režim s nízkou latencí GC bude pro tuto relaci zakázán. Opětovné restartování sady Visual Studio – povolí výchozí chování GC. Další informace najdete v tématu <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Vyprázdněné mezipaměti sady Visual Studio

Pokud budete pokračovat v aktuální vývojové relaci nebo restartujete aplikaci Visual Studio, všechny mezipaměti sady Visual Studio se okamžitě vyprázdní, ale začněte znovu naplnit. Vyprázdněné mezipaměti zahrnují mezipaměti pro následující funkce:

- Najít všechny odkazy

- Přejít na

- Přidat pomocí

Kromě toho jsou vymazány i mezipaměti používané pro interní operace sady Visual Studio.

> [!NOTE]
> Automatické upozornění na pozastavení funkcí probíhá pouze jednou pro jednotlivá řešení, nikoli na základě jednotlivých relací. To znamená, že pokud přepnete z Visual Basic do C# vizuálu (nebo naopak) a spustíte do jiného stavu nedostatku paměti, můžete získat další upozornění na automatické pozastavení funkcí.

## <a name="see-also"></a>Viz také:

- [Postupy: Povolení a zakázání úplné analýzy řešení](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Základy kolekce paměti](/dotnet/standard/garbage-collection/fundamentals)
- [Požadavky na výkon pro velká řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
