---
title: Nalezení potenciálních problémů pomocí analyzátorů mapy kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6656ae4e5dc4acc0cb95b40fbb3eaa10b473d9e1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802392"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Nalezení potenciálních problémů pomocí analyzátorů mapy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spusťte analyzátory na mapách kódu, abyste mohli snadno identifikovat kód, který může být příliš složitý nebo který může být nutné zlepšování. Například můžete použít tyto analyzátory:  
  
|**Kód, který se má najít**|**Prozkoumat tyto oblasti zobrazíte, zda**|  
|-------------------------------|--------------------------------------------|  
|Smyčky nebo cyklické závislosti|Můžete zjednodušit jejich a zvažte, jestli můžete přerušit tyto cykly.|  
|Moc velký počet závislostí|Provádějí příliš mnoho funkcí nebo zjistit dopad změny těchto oblastí. Minimální číslo závislostí se bude zobrazovat mapu kódu ve správném formátu. Abyste mohli snadněji udržovat, změnit, testování a znovu použít, zvažte, jestli Refaktorovat tyto oblasti tak, aby větší přehlednost jsou definovány, nebo určuje, zda je možné sloučit kód, který provádí podobné funkce jako kód.|  
|Žádné závislosti.|Potřeby nebo zda byste měli odebrat tento kód.|  
  
## <a name="analyze-code-maps"></a>Analýza map kódu  
  
1. Na panelu nástrojů Mapa **rozložení**, **analyzátory**a potom analyzátor, který chcete spustit:  
  
   |**Analyzátor**|**K identifikaci uzlů, který**|  
   |------------------|--------------------------------|  
   |**Analyzátor cyklické odkazy**|Cyklické závislosti jsou na sobě navzájem. **Poznámka:** cyklické závislosti, které jsou v **obecných typů** skupiny nejsou zobrazeny na mapě, získáte rozbalením skupiny.|  
   |**Najít analyzátor rozbočovače**|Jsou v horním 25 % vysoce připojených uzlů<br /><br /> **Chcete-li skrýt všechny uzly na mapě**<br /><br /> -Otevřete místní nabídku pro mapu, zvolte **Upřesnit**, **vyberte**, **Skrýt nevybrané**.<br />     Na mapě skryje nevybraných uzlů a analyzátor identifikuje nových uzlů jako centra.|  
   |**Analyzátor neodkazované uzly**|Nemají odkazy z jiných uzlů. **Upozornění:** všech těchto případech před ověření za předpokladu, že kód se nepoužívá. Určité závislosti, jako je například XAML závislosti a závislosti za běhu nelze nalézt staticky v kódu.|  
  
   Analyzátorů mapy kódu bude nadále spuštěna po jejich použití. Pokud změníte na mapě, žádné použité Analyzátory se automaticky znovu zpracovat mapa aktualizovaná. Chcete-li zastavit spuštěný analyzátor, na panelu nástrojů mapy, zvolte **rozložení**, **analyzátory**. Vypněte vybrané analyzátor.  
  
> [!TIP]
>  Pokud máte mapu velmi velké, může způsobit spuštěný analyzátor nedostatku paměti výjimky. Pokud k tomu dojde, upravit mapu ke snížení jeho rozsah nebo vygenerovat menší a potom spustit Analyzátor.  
  
## <a name="see-also"></a>Viz také  
 [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)   
 [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)



