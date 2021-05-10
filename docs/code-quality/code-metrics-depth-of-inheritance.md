---
title: Metriky kódu – hloubka dědičnosti
ms.date: 1/8/2021
description: Seznamte se s hloubkou metriky dědičnosti pro metriky kódu v aplikaci Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1d6ac085463087fc73aac4429488ab475e91c10f
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682659"
---
# <a name="code-metrics---depth-of-inheritance-dit"></a>Metriky kódu – hloubka dědičnosti (DIT)

V tomto článku se naučíte jedna z metrik navržená speciálně pro objektově orientované analýzy: hloubka dědičnosti. Hloubka dědičnosti, označovaná také jako hloubka stromu dědičnosti (DIT), je definována jako "maximální délka z uzlu do kořenového adresáře stromu" [CK](#ck). Můžete to zobrazit jednoduchým příkladem. Vytvořte nový projekt knihovny tříd a před psaním kódu Vypočítejte metriky kódu výběrem možnosti **analyzovat > výpočet metrik kódu pro řešení**.

![Hloubka dědičnosti – příklad 1](media/depth-of-inheritance-example-1.png)

Vzhledem k tomu, že všechny třídy dědí z `System.Object` , Hloubka je aktuálně 1. Pokud jste dědili z této třídy a prozkoumali novou třídu, můžete vidět výsledek:

![Hloubka dědičnosti – příklad 2](media/depth-of-inheritance-example-2.png)

Všimněte si, že čím nižší je uzel ve stromové struktuře ( `Class2` v tomto případě), tím větší je hloubka dědičnosti. Můžete pokračovat v vytváření podřízených objektů a způsobit, že se hloubka navýší tak, jak chcete.

## <a name="assumptions"></a>Předpoklady

Hloubka dědičnosti se vychází ze tří základních předpokladů [CK](#ck):

1. Hlubší je třída v hierarchii, což je větší počet metod, který bude pravděpodobně děděn, což ztěžuje jeho chování předpovědět.

2. Hlubší stromy zahrnují větší složitost návrhu, protože jsou zapojeny další třídy a metody.

3. Hlubší třídy ve stromu mají větší potenciál pro znovu použití zděděných metod.

Předpoklady 1 a 2 vám sdělí, že je větší číslo pro hloubku špatné. Pokud je to tam, kde skončil, měli byste být dobrý tvar; předpoklad 3 však označuje, že vyšší číslo pro hloubku je dobré pro možné opětovné použití kódu.

## <a name="analysis"></a>Analýza

Tady je postup čtení metriky hloubky:

- Nízké číslo pro hloubku

  Nízké číslo pro hloubku znamená méně složitosti, ale také možnost méně opakovaného použití kódu prostřednictvím dědičnosti.

- Vysoké číslo pro hloubku

  Vysoké číslo pro hloubku znamená více možností opakovaného použití kódu prostřednictvím dědičnosti, ale také vyšší složitost s vyšší pravděpodobností chyb v kódu.

## <a name="code-analysis"></a>analýza kódu

Analýza kódu zahrnuje kategorii pravidel udržovatelnosti. Další informace najdete v tématu [pravidla udržovatelnosti](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Pokud používáte starší verzi analýzy kódu, sada pravidel rozšířená návrhová pravidla obsahuje oblast udržovatelnosti:

![Hloubka sad pravidel pro pravidla návrhu dědičnosti](media/depth-of-inheritance-design-guidelines.png)

V oblasti udržovatelnosti je pravidlo dědičnosti:

![Hloubka pravidla udržovatelnosti dědičnosti](media/depth-of-inheritance-maintainability-rule.png)

Toto pravidlo vystavuje upozornění, když hloubka dědičnosti dosáhne 6 nebo vyšší, takže je dobrým pravidlem, které vám může zabránit nadměrnému dědění. Další informace o tomto pravidle najdete v tématu [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501).

## <a name="putting-it-all-together"></a>Společné umístění

Vysoká hodnota pro DIT znamená, že chyby jsou také vysoké a nízké hodnoty omezují potenciální chyby. Vysoké hodnoty pro DIT označují větší potenciál opětovného použití kódu prostřednictvím dědičnosti, nízké hodnoty navrhují méně opakované použití kódu, i když dědičnost využívá. Z důvodu nedostatku dat nejsou aktuálně přijímány standardní hodnoty pro hodnoty DIT. Dokonce i nedávno provedené studie nenalezly dostatečné množství dat k určení životaschopného čísla, které by bylo možné použít jako standardní číslo pro tuto metriku [Shatnawi](#shatnawi). I když není k dispozici žádný empirický důkaz, několik prostředků naznačuje, že by měl být v horním limitu DIT 5 nebo 6. Příklad naleznete v tématu [http://www.devx.com/architect/Article/45611](http://www.devx.com/architect/Article/45611) .

## <a name="citations"></a>Citací konkrétního

### <a name="ck"></a>Ck

Chida jejich, S. R. & Seymer, C. F. (1994). Sada metrik pro objektově orientovaný design (transakce IEEE v softwarovém inženýrství, vol. 20, Ne. 6). Načteno 14. května 2011 z webu University of Můžete použít: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="krishnan"></a>Krishnan

Subramramm, R. & S. (2003). Empirical Analysis of CK Metrics for Object-Oriented Design Complexity: Implications for Software Defects (IEEE Transactions on Software Engineering, Vol. 29, No. 4). Načteno 14. května 2011, původně získané z webu University of Massachusetts Dart webu [https://ieeexplore.ieee.org/abstract/document/1191795](https://ieeexplore.ieee.org/abstract/document/1191795)

### <a name="shatnawi"></a>Shatnawi

Shatnawi, R. (2010). Kvantitativní šetření přijatelných úrovní rizika metrik Object-Oriented v Open-Source Systems (IEEE Transactions on Software Engineering, Vol. 36, No. 2).