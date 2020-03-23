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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8480eb57a08905c2a593adbab519ae793638888
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431238"
---
# <a name="automatic-feature-suspension"></a>Automatické pozastavení funkce

Pokud dostupná systémová paměť klesne na 200 MB nebo méně, visual studio zobrazí v editoru kódu následující zprávu:

![Výstražný text pozastavující úplnou analýzu řešení](../code-quality/media/fsa_alert.png)

Když Visual Studio zjistí stav nedostatku paměti, automaticky pozastaví některé pokročilé funkce, aby zůstal stabilní. Visual Studio pokračuje v práci jako dříve, ale jeho výkon je snížena.

V podmínkách nedostatku paměti probíhá následující akce:

- Analýza živého kódu pro visual c# a visual basic je snížena na minimální rozsah.

- [Uvolňování paměti](/dotnet/standard/garbage-collection/index) (GC) režim s nízkou latencí pro Visual C# a Visual Basic je zakázán.

- Mezipaměti sady Visual Studio jsou vyprázdněny.

## <a name="improve-visual-studio-performance"></a>Zlepšení výkonu visual studia

Tipy a triky, jak zlepšit výkon sady Visual Studio při práci s velkými řešeními nebo podmínkami nedostatku paměti, naleznete [v tématu Důležité informace o výkonu pro velká řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>Analýza živého kódu je omezena na minimální rozsah

Ve výchozím nastavení se analýza živého kódu provádí pro otevřené dokumenty a projekty. Tento obor analýzy můžete přizpůsobit tak, aby byl omezen na aktuální dokument nebo zvýšen na celé řešení. Další informace naleznete v [tématu Postup: Konfigurace oboru analýzy živého kódu pro spravovaný kód](./configure-live-code-analysis-scope-managed-code.md). V případě nedostatku paměti Visual Studio vynutí rozsah živé analýzy, které mají být sníženy na aktuální dokument. Můžete však znovu povolit upřednostňovaný obor analýzy výběrem tlačítka **Znovu povolit** na informačním panelu, když se zobrazí, nebo restartováním sady Visual Studio. Dialogové okno Možnosti vždy zobrazuje aktuální nastavení oboru analýzy živého kódu.

## <a name="gc-low-latency-disabled"></a>Zakázána nízká latence globálního katalogu

Chcete-li znovu povolit režim s nízkou latencí gc, restartujte aplikaci Visual Studio. Ve výchozím nastavení Visual Studio umožňuje gc režim s nízkou latencí při každém psaní, aby zajistily, že vaše psaní neblokuje žádné operace GC. Pokud však stav nedostatku paměti způsobí, že visual studio zobrazí upozornění na automatické pozastavení, režim s nízkou latencí GC je pro tuto relaci zakázán. Restartování sady Visual Studio znovu povolí výchozí chování GC. Další informace naleznete v tématu <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Vyprázdněné mezipaměti sady Visual Studio

Pokud budete pokračovat v aktuální relaci vývoje nebo restartovat Visual Studio, všechny mezipaměti sady Visual Studio jsou okamžitě vyprázdněny, ale začnou znovu naplnit. Vyprázdněné mezipaměti zahrnují mezipaměti pro následující funkce:

- Najít všechny reference

- Přejít na

- Přidat pomocí

Kromě toho mezipaměti používané pro interní operace sady Visual Studio jsou také vymazány.

> [!NOTE]
> Automatické pozastavení funkce upozornění dochází pouze jednou na základě řešení, nikoli na základě relace. To znamená, že pokud přepnete z jazyka Visual Basic na Visual C# (nebo naopak) a naběhnete do jiného stavu nedostatku paměti, můžete případně získat další upozornění na pozastavení automatické funkce.

## <a name="see-also"></a>Viz také

- [Postup: Konfigurace oboru analýzy živého kódu pro spravovaný kód](./configure-live-code-analysis-scope-managed-code.md)
- [Základy kolekce paměti](/dotnet/standard/garbage-collection/fundamentals)
- [Aspekty výkonu pro velká řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
