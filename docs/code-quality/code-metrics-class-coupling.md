---
title: Metriky kódu – Párování tříd
ms.date: 1/8/2021
description: Přečtěte si o metrikách párování tříd pro metriky kódu v Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0853b807d3287eb584e76d9640ac98f930edb1a7
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666806"
---
# <a name="code-metrics---class-coupling"></a>Metriky kódu – Párování tříd

Párování tříd také prochází názvem Párování mezi objekty (CBO), jak bylo původně definováno společností [CK94](#ck94). V podstatě je párování tříd měřítkem toho, kolik tříd používá jedna třída. Vysoké číslo je špatné a s touto metrikou je obvykle dobré nízké číslo. Ukázalo se, že párování tříd je přesným předpovědí selhání softwaru, a nedávné studie ukázaly, že horní limitní hodnota 9 je nejefektivnější hodnotou [S2010.](#s2010)

Podle dokumentace Microsoftu párování tříd "měří párování s jedinečnými třídami prostřednictvím parametrů, místních proměnných, návratových typů, volání metod, obecných nebo šablonových instancí, základních tříd, implementací rozhraní, polí definovaných u externích typů a dekorování atributů. Dobrý návrh softwaru určuje, že typy a metody by měly mít vysokou a nízká párování. Vysoká párování indikuje návrh, který se obtížně opakovaně používá a udržuje kvůli mnoha vzájemným závislostem na jiných typech."

Koncepty párování a souviset jsou jasně spojené. V této diskuzi o tomto tématu se nebudeme podrobně seznamovat s jinými než stručnou definicí z [KKLS2000:](#kkls2000)

"Module modulem se vám a Yourdone představil jako "jak pevně vázané nebo související vnitřní prvky modulu jsou mezi sebou" [YC79](#yc79). Modul má silnou podchytu, pokud představuje právě jeden úkol a všechny jeho prvky přispívají k tomuto jedinému úkolu. Popisují popis popisování jako atributu návrhu, nikoli kódu, a atribut, který lze použít k předpovídání opětovné použitelnosti, udržovatelnosti a měnitelnosti.

## <a name="class-coupling-example"></a>Příklad párování tříd

Podívejme se na párování tříd v akci. Nejprve vytvořte novou konzolovou aplikaci a vytvořte novou třídu Person s některými vlastnostmi a pak okamžitě vypočítejte metriky kódu:

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

Jak vidíte, párování tříd pro třídu PersonStuff má až 2 a pokud přejdete na třídu, vidíte, že v ní je k této metodě nejvíce přihlašování, `DoSomething()` ale konstruktor stále používá pouze 1 třídu.  Pomocí těchto metrik můžete zobrazit celkový maximální počet pro danou třídu a přejít k podrobnostem jednotlivých členů.

## <a name="the-magic-number"></a>Magické číslo

Stejně jako u cyclomaticky složité složitosti neexistuje žádný limit, který by byl vhodný pro všechny organizace. [S2010](#s2010) ale značí, že limit 9 je optimální:

"Proto uvažujeme prahové hodnoty jako nejúčinnější. Tyto prahové hodnoty (pro jednoho člena) jsou CBO = 9". (zvýraznění přidáno)

## <a name="code-analysis"></a>analýza kódu

Analýza kódu zahrnuje kategorii Pravidla udržovatelnosti. Další informace najdete v tématu [Pravidla udržovatelnosti.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) Při použití starší verze analýzy kódu obsahuje sada pravidel Rozšířené pokyny k návrhu oblast udržovatelnosti:

![Pravidla rozšířených obecných pokynů pro návrh párování tříd](media/class-coupling-extended-design-guideline-rules.png)

Uvnitř oblasti udržovatelnosti je pravidlo pro párování tříd:

![Pravidlo párování tříd](media/class-coupling-maintainability-area-rules.png)

Toto pravidlo zobrazí upozornění, když je párování tříd nadměrné. Další informace najdete v tématu [CA1506: Vyhněte se nadměrnému párování tříd](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

## <a name="citations"></a>Citace

### <a name="ck94"></a>CK94

Chida jejich, S. R. & Seymer, C. F. (1994). Sada metrik pro objektově orientovaný návrh (transakce IEEE na Software Engineering, obj. 20, ne. 6). Získáno 14. května 2011 na webu University of pensylvánském: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., Lustman, F. a svatého-Denis, G. (2000). Přečtěte si další stížnost třídy: empirická studie pro průmyslové systémy (jednání dílny o kvantitativních přístupech Object-Oriented Software Engineering). Načteno 20. května 2011, z webu Université de Montréal [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Krishnan, M. S. (2003). Empirická analýza metrik CK pro složitost návrhu Object-Oriented: důsledky pro vady softwaru (IEEE transakcí při softwarovém inženýrství, obj. 29, ne. 4). Získáno 14. května 2011 z webu University of Massachusetts Dartmouth [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Kvantitativní šetření přijatelných úrovní rizika Object-Oriented metriky v systémech Open-Source (transakce IEEE na Software Engineering, obj. 36, ne. 2).

### <a name="yc79"></a>YC79

Edward Yourdon a Larry L. Constantine. Strukturovaný návrh. Prentice hala, Englewood výtahy, N.J., 1979.