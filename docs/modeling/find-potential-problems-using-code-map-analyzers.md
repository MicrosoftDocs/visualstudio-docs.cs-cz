---
title: Nalezení potenciálních problémů pomocí analyzátorů mapy kódu
description: Naučte se, jak můžete spouštět analyzátory na mapě kódu, abyste mohli identifikovat kód, který může být příliš složitý nebo který může být potřeba zlepšit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8817e50ae96a27f6b3b76e28262390271c1fdf4c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388851"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Nalezení potenciálních problémů pomocí analyzátorů mapy kódu

Spuštění analyzátorů v mapách kódu vám usnadní identifikaci kódu, který může být příliš složitý nebo který může být potřeba zlepšit. Můžete například použít tyto analyzátory:

|**Chcete-li najít kód, který má**|**Zkontrolujte tyto oblasti a zjistěte, zda**|
|-|-|
|Cykly nebo cyklické závislosti|Můžete je zjednodušit a zvážit, zda můžete tyto cykly přerušit.|
|Příliš mnoho závislostí|Provádějí příliš mnoho funkcí nebo určují dopad změny těchto oblastí. V mapě kódu ve správném formátu se zobrazí minimální počet závislostí. Aby bylo možné zjednodušit správu, změnu, testování a opakované použití kódu, zvažte, zda můžete tyto oblasti Refaktorovat, aby byly mnohem jasně definovány nebo zda lze sloučit kód, který provádí podobné funkce.|
|Žádné závislosti|Jsou nezbytné nebo zda byste měli tento kód odebrat.|

## <a name="analyze-code-maps"></a>Analyzovat mapy kódu

Na panelu nástrojů mapa zvolte   >  **analyzátory** rozložení a pak analyzátor, který chcete spustit:

|**MBSA**|**K identifikaci uzlů, které**|
|-|-|
|**Analyzátor cyklických odkazů**|Cyklické závislosti na sobě navzájem. **Poznámka:**  Cyklické závislosti, které jsou ve skupině **obecných typů** , se při rozbalení skupiny nezobrazují na mapě.|
|**Najít analyzátor Center**|Jsou v horním 25% uzlů s vysokou úrovní připojení<br /><br /> **Skrytí všech ostatních uzlů na mapě**<br /><br /> -Otevřete místní nabídku pro mapu, zvolte možnost **Upřesnit**, **Vybrat** a **Skrýt nevybrané**.<br />     Mapa skryje nevybrané uzly a analyzátor identifikuje nové uzly jako centra.|
|**Analyzátor neodkazované uzly**|Nemají odkazy z jiných uzlů. **Upozornění:**  Před za předpokladu, že se kód nepoužívá, ověřte každý z těchto případů. Některé závislosti, například závislosti XAML a závislosti za běhu, nelze v kódu nalézt staticky.|

Analyzátory mapování kódu budou po použití nadále spouštěny. Změníte-li mapu, všechny použité analyzátory budou automaticky znovu zpracovat aktualizované mapování. Chcete-li zastavit spuštění analyzátoru, na panelu nástrojů mapa vyberte možnost  >  **analyzátory** rozložení. Vypněte vybraný analyzátor.

> [!TIP]
> Pokud máte velmi velkou mapu, může spuštění analyzátoru způsobit výjimku z důvodu nedostatku paměti. Pokud k tomu dojde, upravte mapu tak, aby omezila svůj rozsah nebo vygenerovala menší hodnotu, a pak spusťte analyzátor.

## <a name="see-also"></a>Viz také

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
