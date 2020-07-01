---
title: Automatické pozastavení funkce
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 236a95cd8d4af8da91199bf79e7c9fe3aa0d49af
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769482"
---
# <a name="automatic-feature-suspension"></a>Automatické pozastavení funkce

Pokud velikost dostupné systémové paměti klesne na 200 MB nebo méně, Visual Studio zobrazí v editoru kódu následující zprávu:

![Text výstrahy, která pozastavuje úplnou analýzu řešení](../code-quality/media/fsa_alert.png)

Když Visual Studio zjistí stav nedostatku paměti, automaticky pozastaví určité pokročilé funkce, aby bylo možné udržet stabilní. Visual Studio bude i nadále fungovat jako dřív, ale jeho výkon je degradován.

V podmínkách nedostatku paměti proběhne následující akce:

- Živá analýza kódu pro Visual C# a Visual Basic se zkracuje na minimální rozsah.

- Režim [uvolňování paměti](/dotnet/standard/garbage-collection/index) (GC) s nízkou latencí pro Visual C# a Visual Basic je zakázaný.

- Mezipaměti sady Visual Studio jsou vyprázdněné.

## <a name="improve-visual-studio-performance"></a>Zlepšení výkonu sady Visual Studio

Tipy a triky, jak zlepšit výkon sady Visual Studio při práci s velkými řešeními nebo s nízkými paměťovými podmínkami, najdete v tématu [požadavky na výkon pro velká řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>Živá analýza kódu se zkracuje na minimální rozsah

Ve výchozím nastavení se dynamická analýza kódu spouští pro otevřené dokumenty a projekty. Tento obor analýzy můžete přizpůsobit tak, aby se snížil na aktuální dokument nebo zvýšil na celé řešení. Další informace naleznete v tématu [How to: Configure Live Code Analysis Scope for Managed Code](./configure-live-code-analysis-scope-managed-code.md). V případě nedostatku paměti aplikace Visual Studio vynutí snížení rozsahu živých analýz na aktuální dokument. Můžete však znovu povolit svůj preferovaný rozsah analýzy výběrem tlačítka **znovu povolit** na informačním panelu, když se zobrazí nebo po restartování sady Visual Studio. Dialogové okno Možnosti vždy zobrazuje aktuální nastavení rozsahu analýzy kódu v reálném čase.

## <a name="gc-low-latency-disabled"></a>Nízká latence GC – vypnuto

Pokud chcete znovu povolit režim s nízkou latencí GC, restartujte Visual Studio. Ve výchozím nastavení Visual Studio umožňuje režim GC s nízkou latencí, kdykoli píšete, abyste zajistili, že váš zápis nebude blokovat žádné operace GC. Pokud ale stav nedostatku paměti způsobí, že Visual Studio zobrazí upozornění na automatické pozastavení, režim s nízkou latencí GC bude pro tuto relaci zakázán. Opětovné restartování sady Visual Studio – povolí výchozí chování GC. Další informace naleznete v tématu <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Vyprázdněné mezipaměti sady Visual Studio

Pokud budete pokračovat v aktuální vývojové relaci nebo restartujete aplikaci Visual Studio, všechny mezipaměti sady Visual Studio se okamžitě vyprázdní, ale začněte znovu naplnit. Vyprázdněné mezipaměti zahrnují mezipaměti pro následující funkce:

- Najít všechny odkazy

- Přejít na

- Přidat pomocí

Kromě toho jsou vymazány i mezipaměti používané pro interní operace sady Visual Studio.

> [!NOTE]
> Automatické upozornění na pozastavení funkcí probíhá pouze jednou pro jednotlivá řešení, nikoli na základě jednotlivých relací. To znamená, že pokud přepnete z Visual Basic do jazyka Visual C# (nebo naopak) a spustíte do jiného stavu nedostatku paměti, můžete získat další upozornění na automatické pozastavení funkcí.

## <a name="see-also"></a>Viz také:

- [Postupy: Konfigurace oboru dynamické analýzy kódu pro spravovaný kód](./configure-live-code-analysis-scope-managed-code.md)
- [Základy kolekce paměti](/dotnet/standard/garbage-collection/fundamentals)
- [Požadavky na výkon pro velká řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
