---
title: Automatické pozastavení funkcí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c80ba76ba2da978c9cb475299ba0fc9e614120
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655151"
---
# <a name="automatic-feature-suspension"></a>Automatické pozastavení funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Pokud vaše dostupná systémová paměť spadá do 200 MB nebo méně, Visual Studio zobrazí následující zprávu v editoru kódu.

 ![Text výstrahy, která pozastavuje úplnou analýzu řešení](../code-quality/media/fsa-alert.png "FSA_Alert")

 Když Visual Studio zjistí stav nedostatku paměti, automaticky pozastaví určité pokročilé funkce, aby bylo možné udržet stabilní. Pokud se zobrazí toto upozornění k rozšířenému pozastavení funkcí, Visual Studio bude nadále fungovat jako předtím, ale jeho výkon bude mírně snížen.

 V případě stavu nedostatek paměti dojde k následujícímu:

- Úplná analýza řešení pro Visual C# a Visual Basic je zakázaná.

- Režim [uvolňování paměti](https://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) (GC) s nízkou latencí pro Visual C# a Visual Basic jsou zakázané.

- Mezipaměti sady Visual Studio jsou vyprázdněné.

## <a name="improve-visual-studio-performance"></a>Zlepšení výkonu sady Visual Studio
 Tipy a triky, jak zlepšit výkon sady Visual Studio při práci s velkými řešeními nebo s nízkými paměťovými podmínkami, najdete v tématu [požadavky na výkon pro velká řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Úplná analýza řešení je pozastavená.
 Ve výchozím nastavení je úplná analýza řešení povolena pro Visual Basic a zakázanou pro jazyk Visual C#. V případě nedostatku paměti je však kompletní analýza řešení automaticky zakázána pro Visual Basic i Visual C# bez ohledu na jejich nastavení v dialogovém okně Možnosti. Úplnou analýzu řešení však můžete znovu povolit kliknutím na tlačítko **znovu povolit** na informačním panelu, když v dialogovém okně Možnosti zaškrtnete políčko **Povolit úplnou analýzu řešení** , nebo restartováním sady Visual Studio. Dialogové okno Možnosti vždy zobrazuje aktuální nastavení úplné analýzy řešení. Další informace najdete v tématu [Postup: povolení a zákaz úplné analýzy řešení](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Nízká latence GC – vypnuto
 Pokud chcete znovu povolit režim s nízkou latencí GC, restartujte Visual Studio.  Ve výchozím nastavení Visual Studio umožňuje režim GC s nízkou latencí, kdykoli píšete, abyste zajistili, že váš zápis nebude blokovat žádné operace GC. Pokud ale stav nedostatku paměti způsobí, že Visual Studio zobrazí upozornění na automatické pozastavení, režim s nízkou latencí GC bude pro tuto relaci zakázán. Restartování sady Visual Studio znovu aktivuje výchozí chování GC. Další informace naleznete v tématu <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Vyprázdněné mezipaměti sady Visual Studio

Všechny mezipaměti sady Visual Studio se hned vyprázdní, ale pokud budete pokračovat v aktuální vývojové relaci nebo restartovat Visual Studio, začne se znovu naplnit. Vyprázdněné mezipaměti zahrnují mezipaměti pro následující funkce.

- Najít všechny odkazy

- Přejít na

- Přidat pomocí

Kromě toho jsou vymazány i mezipaměti používané pro interní operace sady Visual Studio.

> [!NOTE]
> Automatické upozornění na pozastavení funkcí probíhá pouze jednou pro jednotlivá řešení, nikoli na základě jednotlivých relací. To znamená, že pokud přepnete z Visual Basic do jazyka Visual C# (nebo naopak) a spustíte do jiného stavu nedostatku paměti, můžete získat další upozornění na automatické pozastavení funkcí.

## <a name="see-also"></a>Viz také

- [Postupy: Povolení a zakázání úplné analýzy řešení](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Základy kolekce paměti](https://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Požadavky na výkon pro velká řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)