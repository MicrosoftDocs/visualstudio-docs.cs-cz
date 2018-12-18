---
title: Automatické pozastavení funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c8aee8f4ef46d3621bf569b260d943180abd7ad5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178175"
---
# <a name="automatic-feature-suspension"></a>Automatické pozastavení funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Pokud dostupné systémové paměti klesne na 200MB nebo méně, Visual Studio zobrazí následující zpráva v editoru kódu.

 ![Pozastavení úplné analýzy řešení textu výstrahy](../code-quality/media/fsa-alert.png "FSA_Alert")

 Když Visual Studio zjistí ke stavu nedostatku paměti, automaticky pozastaví některé pokročilé funkce, které pomohou vypnutý stabilní. Když to pokročilé funkce pozastavení se vaše upozornění se zobrazí, Visual Studio budou nadále fungovat jako předtím, ale budou mírně snížený jeho výkon.

 V ke stavu nedostatku paměti, dojde k následujícímu:

-   Úplná analýza řešení pro Visual C# a Visual Basic je zakázaná.

-   [Uvolňování paměti](http://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) režimu s nízkou latencí (GC) pro Visual C# a Visual Basic jsou zakázané.

-   Visual Studio mezipamětí, vyprázdní.

## <a name="improve-visual-studio-performance"></a>Zlepšení výkonu sady Visual Studio
 Tipy a triky pro zlepšení výkonu sady Visual Studio, když se zabývají velká řešení nebo nedostatku paměti najdete v tématu [faktory ovlivňující výkon u velkých řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Úplná analýza řešení pozastaveno
 Ve výchozím nastavení je úplné analýzy řešení povolené v jazyce Visual Basic a zakázán pro jazyk Visual C#. Ale v ke stavu nedostatku paměti, úplné analýzy řešení je automaticky zakázána pro Visual Basic a Visual C#, bez ohledu na jejich nastavení v dialogovém okně Možnosti. Však můžete znovu povolit úplné analýzy řešení kliknutím **znovu povolit** v informačního panelu Pokud je zobrazeno, tak, že vyberete tlačítko **povolení úplné analýzy řešení** zaškrtávací políčko v dialogovém okně Možnosti, nebo podle restartování sady Visual Studio. Dialogové okno Možnosti vždy zobrazuje aktuální úplné řešení analýzy nastavení. Další informace najdete v tématu [postupy: povolení a zákaz analýzy celého řešení](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Uvolňování paměti s nízkou latencí zakázáno
 Opětovné povolení režimu uvolňování paměti s nízkou latencí, restartujte aplikaci Visual Studio.  Ve výchozím nastavení sada Visual Studio umožňuje režim s nízkou latencí uvolňování paměti pokaždé, když jsou psát, ujistěte se, že zadaný dotaz nebrání žádné operace uvolňování paměti. Pokud ke stavu nedostatku paměti způsobí, že Visual Studio zobrazit upozornění na automatické pozastavení, s nízkou latencí režimu uvolňování paměti zakázáno pro danou relaci. Restartování sady Visual Studio znovu povolit chování výchozí uvolňování paměti. Další informace naleznete v tématu <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio mezipamětí vyprázdněných

Všechny sady Visual Studio mezipaměti jsou vyprázdněny okamžitě, ale začne znovu vytvořit, je-li pokračovat v aktuální relaci vývoj nebo restartujte sadu Visual Studio. Vyprázdnění mezipaměti zahrnují mezipaměť pro následující funkce.

-   Najít všechny odkazy

-   Přejděte na

-   Přidání direktivy Using

Kromě toho jsou vymazány mezipamětí použít pro interní operace sady Visual Studio.

> [!NOTE]
> Funkce automatického pozastavení se vaše upozornění se vyskytuje jen jednou na základě každé řešení, ne na bázi relací. To znamená, že pokud přejděte z jazyka Visual Basic do jazyka Visual C# (nebo naopak) a spusťte do jiného ke stavu nedostatku paměti, můžete případně získat další funkce automatického pozastavení se vaše upozornění.

## <a name="see-also"></a>Viz také:

- [Postupy: Povolení a zakázání úplné analýzy řešení](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Základy kolekce paměti](http://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Faktory ovlivňující výkon u velkých řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)