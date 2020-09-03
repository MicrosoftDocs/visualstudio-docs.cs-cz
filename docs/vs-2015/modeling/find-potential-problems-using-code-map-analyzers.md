---
title: Nalezení potenciálních problémů pomocí analyzátorů mapy kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc5d185640c9623a2213aaf7ad50fa68a088b15c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669620"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Nalezení potenciálních problémů pomocí analyzátorů mapy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spuštění analyzátorů v mapách kódu vám usnadní identifikaci kódu, který může být příliš složitý nebo který může být potřeba zlepšit. Můžete například použít tyto analyzátory:

|**Chcete-li najít kód, který má**|**Zkontrolujte tyto oblasti a zjistěte, zda**|
|-------------------------------|--------------------------------------------|
|Cykly nebo cyklické závislosti|Můžete je zjednodušit a zvážit, zda můžete tyto cykly přerušit.|
|Příliš mnoho závislostí|Provádějí příliš mnoho funkcí nebo určují dopad změny těchto oblastí. V mapě kódu ve správném formátu se zobrazí minimální počet závislostí. Aby bylo možné zjednodušit správu, změnu, testování a opakované použití kódu, zvažte, zda můžete tyto oblasti Refaktorovat, aby byly mnohem jasně definovány nebo zda lze sloučit kód, který provádí podobné funkce.|
|Žádné závislosti|Jsou nezbytné nebo zda byste měli tento kód odebrat.|

## <a name="analyze-code-maps"></a>Analyzovat mapy kódu

1. Na panelu nástrojů mapa zvolte **rozložení**, **analyzátory**a pak analyzátor, který chcete spustit:

   |**MBSA**|**K identifikaci uzlů, které**|
   |------------------|--------------------------------|
   |**Analyzátor cyklických odkazů**|Cyklické závislosti na sobě navzájem. **Poznámka:**  Cyklické závislosti, které jsou ve skupině **obecných typů** , se při rozbalení skupiny nezobrazují na mapě.|
   |**Najít analyzátor Center**|Jsou v horním 25% uzlů s vysokou úrovní připojení<br /><br /> **Skrytí všech ostatních uzlů na mapě**<br /><br /> -Otevřete místní nabídku pro mapu, zvolte možnost **Upřesnit**, **Vybrat**a **Skrýt nevybrané**.<br />     Mapa skryje nevybrané uzly a analyzátor identifikuje nové uzly jako centra.|
   |**Analyzátor neodkazované uzly**|Nemají odkazy z jiných uzlů. **Upozornění:**  Před za předpokladu, že se kód nepoužívá, ověřte každý z těchto případů. Některé závislosti, například závislosti XAML a závislosti za běhu, nelze v kódu nalézt staticky.|

   Analyzátory mapování kódu budou po použití nadále spouštěny. Změníte-li mapu, všechny použité analyzátory budou automaticky znovu zpracovat aktualizované mapování. Chcete-li zastavit spuštění analyzátoru, na panelu nástrojů mapa vyberte možnost **rozložení**, **analyzátory**. Vypněte vybraný analyzátor.

> [!TIP]
> Pokud máte velmi velkou mapu, může spuštění analyzátoru způsobit výjimku z důvodu nedostatku paměti. Pokud k tomu dojde, upravte mapu tak, aby omezila svůj rozsah nebo vygenerovala menší hodnotu, a pak spusťte analyzátor.

## <a name="see-also"></a>Viz také
 [Mapování závislostí ve vašich řešeních](../modeling/map-dependencies-across-your-solutions.md) [použití map kódu k ladění](../modeling/use-code-maps-to-debug-your-applications.md) [metod mapy aplikací v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
