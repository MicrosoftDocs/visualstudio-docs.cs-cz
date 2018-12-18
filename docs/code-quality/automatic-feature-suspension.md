---
title: Automatické pozastavení funkce
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: b97a58a7f5ba3808c658b838de942e94c12b9b79
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049091"
---
# <a name="automatic-feature-suspension"></a>Automatické pozastavení funkce

Pokud dostupné systémové paměti klesne na 200 MB nebo méně, sada Visual Studio zobrazí následující zpráva v editoru kódu:

![Upozornění text pozastavení úplné analýzy řešení](../code-quality/media/fsa_alert.png)

Když Visual Studio zjistí ke stavu nedostatku paměti, automaticky pozastaví některé pokročilé funkce, které pomohou vypnutý stabilní. Visual Studio i nadále fungovat jako předtím, ale jeho výkon.

V ke stavu nedostatku paměti proveďte následující akce místo:

- Úplná analýza řešení pro Visual C# a Visual Basic je zakázaná.

- [Uvolňování paměti](/dotnet/standard/garbage-collection/index) režimu s nízkou latencí (GC) pro vizuál C# a Visual Basic je zakázaná.

- Visual Studio mezipamětí, vyprázdní.

## <a name="improve-visual-studio-performance"></a>Zlepšení výkonu sady Visual Studio

Tipy a triky pro zlepšení výkonu sady Visual Studio, když se zabývají velká řešení nebo nedostatku paměti najdete v tématu [faktory ovlivňující výkon u velkých řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Úplná analýza řešení pozastaveno

Ve výchozím nastavení je úplné analýzy řešení povolené v jazyce Visual Basic a zakázán pro jazyk Visual C#. Ale v ke stavu nedostatku paměti, úplné analýzy řešení je automaticky zakázána pro Visual Basic a Visual C#, bez ohledu na jejich nastavení v dialogovém okně Možnosti. Však můžete znovu povolit úplné analýzy řešení kliknutím **znovu povolit** v informačního panelu Pokud je zobrazeno, tak, že vyberete tlačítko **povolení úplné analýzy řešení** zaškrtávací políčko v dialogovém okně Možnosti, nebo podle restartování sady Visual Studio. Dialogové okno Možnosti vždy zobrazuje aktuální úplné řešení analýzy nastavení. Další informace najdete v tématu [postupy: povolení a zákaz analýzy celého řešení](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Uvolňování paměti s nízkou latencí zakázáno

Opětovné povolení režimu uvolňování paměti s nízkou latencí, restartujte aplikaci Visual Studio. Ve výchozím nastavení sada Visual Studio umožňuje režim s nízkou latencí uvolňování paměti pokaždé, když jsou psát, ujistěte se, že zadaný dotaz nebrání žádné operace uvolňování paměti. Pokud ke stavu nedostatku paměti způsobí, že Visual Studio zobrazit upozornění na automatické pozastavení, s nízkou latencí režimu uvolňování paměti zakázáno pro danou relaci. Restartování sady Visual Studio znovu povolí výchozí chování uvolňování paměti. Další informace naleznete v tématu <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio mezipamětí vyprázdněných

Je-li pokračovat v aktuální relaci vývoj nebo restartujte sadu Visual Studio, všechny mezipaměti sady Visual Studio jsou vyprázdněny okamžitě, ale začít znovu vytvořit. Vyprázdnění mezipaměti patří mezipaměť pro následující funkce:

- Najít všechny odkazy

- Přejděte na

- Přidání direktivy Using

Kromě toho jsou vymazány mezipamětí použít pro interní operace sady Visual Studio.

> [!NOTE]
> Funkce automatického pozastavení se vaše upozornění se vyskytuje jen jednou na základě každé řešení, ne na bázi relací. To znamená, že pokud přejděte z jazyka Visual Basic do jazyka Visual C# (nebo naopak) a spusťte do jiného ke stavu nedostatku paměti, můžete případně získat další funkce automatického pozastavení se vaše upozornění.

## <a name="see-also"></a>Viz také:

- [Postupy: Povolení a zakázání úplné analýzy řešení](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Základy kolekce paměti](/dotnet/standard/garbage-collection/fundamentals)
- [Faktory ovlivňující výkon u velkých řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)