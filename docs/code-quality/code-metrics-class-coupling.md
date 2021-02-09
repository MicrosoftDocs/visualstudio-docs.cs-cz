---
title: Metriky kódu – párování tříd
ms.date: 1/8/2021
description: Přečtěte si o metrikě párování tříd pro metriky kódu v aplikaci Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8320c460faf7532887364693080d38c0ff6baa6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860513"
---
# <a name="code-metrics---class-coupling"></a>Metriky kódu – párování tříd

Párování tříd také přechází název spojovacího bodu mezi objekty (CBO), jak je původně definováno v [CK94](#ck94). V podstatě je přebírání tříd měřítko, kolik tříd používá jedna třída. Vysoké číslo je chybné a pro tuto metriku je obvykle dobré mít nízké číslo. Překládání tříd se ukázalo jako přesné prediktivní selhání softwaru a nedávné studie ukázaly, že hodnota horní meze 9 je nejúčinnější [S2010](#s2010).

Podle dokumentace Microsoftu, párování tříd "měří spojení s jedinečnými třídami prostřednictvím parametrů, místních proměnných, návratových typů, volání metod, obecných instancí nebo instancí šablon, základních tříd, implementací rozhraní, polí definovaných pro externí typy a dekorace atributů. Dobrý návrh softwaru určuje, že typy a metody by měly mít vysokou soudržnost a malý spoj. Vysoké spojení indikuje návrh, který se obtížně opakovaně používá a udržuje z důvodu jejich nejrůznějších závislostí na jiných typech. "

Koncepce propojení a soudržnosti se jasně vztahují. Abychom tuto diskuzi na téma ponechali, nebudeme se dodávat do hloubky s využitím soudržnosti, která není [KKLS2000](#kkls2000):

"Služba Yourdon a Constantine byla představena jako" způsob, jakým jsou vnitřně vázané nebo související interní prvky modulu navzájem jiné " [YC79](#yc79). Modul má silnou soudržnost, pokud reprezentuje právě jeden úkol [...], a všechny jeho prvky přispívají k této jediné úloze. Popisují soudržnost jako atribut návrhu, nikoli kód, a atribut, který lze použít k předpovědi opětovné použitelnosti, udržovatelnosti a možnosti změny. "

## <a name="class-coupling-example"></a>Příklad párování tříd

Pojďme se podívat na spojení třídy v akci. Nejdřív vytvořte novou konzolovou aplikaci a vytvořte novou třídu s názvem Person s některými vlastnostmi a pak hned Vypočítejte metriky kódu:

![Párování tříd – příklad 1](media/class-coupling-example-1.png)

Všimněte si, že třída párování je 0, protože tato třída nepoužívá žádné jiné třídy. Nyní vytvořte další třídu s názvem PersonStuff s metodou, která vytvoří instanci Person a nastaví hodnoty vlastností. Znovu vypočítat metriky kódu:

![Spoj třídy – příklad 2](media/class-coupling-example-2.png)

Podívejte se, jak se hodnota párování tříd dostane? Všimněte si také, že bez ohledu na to, kolik vlastností nastavíte, je hodnota párování tříd pouze o 1, a ne jinou hodnotou. Párování tříd měří každou třídu pouze jednou pro tuto metriku bez ohledu na to, kolik je použito. Kromě toho můžete vidět, že `DoSomething()` má 1, ale konstruktor, `PersonStuff()` má pro svou hodnotu 0? V současné době není v konstruktoru k dispozici žádný kód, který používá jinou třídu.

Co když vložíte kód do konstruktoru, který používá jinou třídu? Tady je přehled toho, co získáte:

![Párování tříd – příklad 3](media/class-coupling-example-3.png)

Nyní konstruktor jasně obsahuje kód, který používá jinou třídu a metrika párování tříd tuto skutečnost zobrazuje. Opět uvidíte, že je celé pole pro párování tříd pro `PersonStuff()` 1 a `DoSomething()` je také 1, aby se zobrazilo, že pouze jedna externí třída se používá bez ohledu na to, kolik interního kódu ho používá.

Dále vytvořte další novou třídu. Dejte této třídě nějaký název a vytvořte v ní nějaké vlastnosti:

![Příklad spojení tříd – přidat novou třídu](media/class-coupling-example-add-new-class.png)

Nyní spotřebujte třídu v naší `DoSomething()` metodě v rámci `PersonStuff` třídy a znovu Vypočítejte metriky kódu:

![Párování tříd – příklad 4](media/class-coupling-example-4.png)

Jak vidíte, párování tříd pro třídu PersonStuff má až 2 a pokud přejdete na třídu, vidíte, že v ní je k této metodě nejvíce přihlašování, `DoSomething()` ale konstruktor stále používá pouze 1 třídu.  Pomocí těchto metrik můžete zobrazit celkové maximální číslo pro danou třídu a přejít k podrobnostem na základě jednotlivých členů.

## <a name="the-magic-number"></a>Magic Number

Stejně jako u cyklomatická složitosti neexistuje žádné omezení, které vyhovuje všem organizacím. [S2010](#s2010) však indikuje, že je optimální limit 9:

"Proto považujeme za prahové hodnoty [...] jako nejúčinnější. Tyto prahové hodnoty (pro jeden člen) jsou CBO = 9 [...]. (přidáno zdůrazněno)

## <a name="code-analysis"></a>analýza kódu

Analýza kódu zahrnuje kategorii pravidel udržovatelnosti. Další informace najdete v tématu [pravidla udržovatelnosti](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Pokud používáte starší verzi analýzy kódu, sada pravidel rozšířená návrhová pravidla obsahuje oblast udržovatelnosti:

![Rozšířená pravidla obecných zásad návrhu pro párování tříd](media/class-coupling-extended-design-guideline-rules.png)

V oblasti udržovatelnosti je pravidlo pro párování tříd:

![Pravidlo párování tříd](media/class-coupling-maintainability-area-rules.png)

Toto pravidlo vystavuje upozornění, když je přeřazení tříd nadměrné. Další informace najdete v tématu [CA1506: Vyhněte se nadměrnému párování tříd](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

Popis tohoto pravidla najdete v blogovém příspěvku o archivu archivovaného kódu: [metriky kódu jako zásady vrácení se změnami](/archive/blogs/codeanalysis/code-metrics-as-check-in-policy) a upozornění na popis prahové hodnoty *nad 80 pro třídu a vyšší než 30 pro metodu*.  Tyto hodnoty se zdají být neobvykle vysoké, ale nejméně poskytují krajní horní limit. Pokud se zobrazí toto upozornění, je něco skoro jistě špatné.

## <a name="citations"></a>Citací konkrétního

### <a name="ck94"></a>CK94

Chidamber, S. R. & Kemerer, C. F. (1994). Sada metrik pro objektově orientovaný návrh (transakce IEEE na Software Engineering, obj. 20, ne. 6). Získáno 14. května 2011 na webu University of pensylvánském: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., Lustman, F. a svatého-Denis, G. (2000). Přečtěte si další stížnost třídy: empirická studie pro průmyslové systémy (jednání dílny o kvantitativních přístupech Object-Oriented Software Engineering). Načteno 20. května 2011, z webu Université de Montréal [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Krishnan, M. S. (2003). Empirická analýza metrik CK pro složitost návrhu Object-Oriented: důsledky pro vady softwaru (IEEE transakcí při softwarovém inženýrství, obj. 29, ne. 4). Získáno 14. května 2011 z webu University of Massachusetts Dartmouth [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Kvantitativní šetření přijatelných úrovní rizika Object-Oriented metriky v systémech Open-Source (transakce IEEE na Software Engineering, obj. 36, ne. 2).

### <a name="yc79"></a>YC79

Edward Yourdon a Larry L. Constantine. Strukturovaný návrh. Prentice hala, Englewood výtahy, N.J., 1979.