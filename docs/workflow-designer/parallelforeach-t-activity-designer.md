---
title: Návrhář postupu provádění – ParallelForEach &lt;T – Návrhář aktivity &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b68cd543ed41408e7510708367c8e539c0702ea1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650094"
---
# <a name="parallelforeach-activity-designer"></a>Návrhář aktivity ParallelForEach

Aktivita <xref:System.Activities.Statements.ParallelForEach%601> vytvoří výčet prvků kolekce a provede vložený příkaz pro každý prvek kolekce paralelně, který je asynchronně ve stejném vlákně. Tuto aktivitu řízení toku použijte místo aktivity <xref:System.Activities.Statements.Sequence>, pokud se očekává, že se podřízené aktivity této aktivity dostanou nečinné.

Aktivita <xref:System.Activities.Statements.ParallelForEach%601> má vlastnost <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, která obsahuje Visual Basicho výrazu zadaného uživatelem. Aktivita <xref:System.Activities.Statements.ParallelForEach%601> vyhodnotí tuto vlastnost po dokončení každé větve. Pokud se vyhodnotí jako **true**, <xref:System.Activities.Statements.ParallelForEach%601> aktivita se dokončí bez provedení ostatních větví. Pokud se <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> nevyhodnotí jako **true**, pak se <xref:System.Activities.Statements.ParallelForEach%601> aktivita dokončí po dokončení všech jejích podřízených aktivit.

## <a name="the-parallelforeacht-activity"></a>Aktivita \> ParallelForEach < T

<xref:System.Activities.Statements.ParallelForEach%601> vytvoří výčet svých hodnot a naplánuje <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> pro každou hodnotu, na které se vytváří výčet. Naplánuje jenom <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Způsob provádění textu závisí na tom, zda <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nečinných.

Pokud se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nečinný, provede se v obráceném pořadí, protože naplánované aktivity jsou zpracovávány jako zásobník, nejprve se spustí poslední naplánovaná aktivita. Například pokud máte kolekci {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> a jako tělo použijte **WriteLine** jako text k zápisu hodnoty. V konzole máte 4, 3, 2, 1. Je to proto, že se **WriteLine** nepracuje, takže když se naplánuje 4 aktivity **WriteLine** , provedou se pomocí chování zásobníku (první v poslední době).

Pokud ale máte v <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> aktivity, které můžou jít nečinné, jako je aktivita <xref:System.ServiceModel.Activities.Receive> nebo aktivita <xref:System.Activities.Statements.Delay>. Pak není nutné čekat na jejich dokončení. <xref:System.Activities.Statements.ParallelForEach%601> přejde na další plánovaný subjekt aktivity a pokusí se ji spustit. Pokud je tato aktivita nečinná, <xref:System.Activities.Statements.ParallelForEach%601> se znovu přesune k dalšímu těle aktivity.

### <a name="using-the-parallelforeacht-activity-designer"></a>Použití návrháře aktivit > ParallelForEach \<T

Přístup k Návrháři aktivity **ParallelForEach \<T >** v kategorii **toku řízení** v **sadě nástrojů**.

Návrhář aktivity **ParallelForEach \<T >** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěna návrháři aktivit, například uvnitř aktivity **sekvence** . návrháře. Po přetažení do Návrhář postupu provádění vytvoří aktivitu <xref:System.Activities.Statements.ParallelForEach%601>, která ve výchozím nastavení obsahuje <xref:System.Activities.Activity.DisplayName%2A> **ParallelForEach < Int32 \>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T \> vlastnosti v Návrhář postupu provádění

Následující tabulka uvádí nejužitečnější vlastnosti <xref:System.Activities.Statements.ParallelForEach%601> aktivity a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje popisný zobrazovaný název návrháře aktivit v hlavičce. Výchozí hodnota je **ParallelForEach \<Int32 >** . Hodnota může být volitelně upravena v mřížce **vlastnosti** nebo přímo v hlavičce návrháře aktivit.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Aktivita, která se má spustit pro každou položku v kolekci. Chcete-li přidat aktivitu <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, přetáhněte aktivitu z panelu nástrojů do pole **text** v Návrháři aktivity v **\<T ParallelForEach >** a v části text nápovědy "Sem přetáhněte aktivitu".|
|**Pro TypeArgument**|Podmínka|Typ položek v kolekci <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> určených obecným parametrem *t*. Ve výchozím nastavení je **pro TypeArgument** nastaveno na hodnotu **Int32**. Chcete-li změnit typ T v Návrháři aktivit **\> ParallelForEach < T** , změňte hodnotu pole se seznamem **pro TypeArgument** v mřížce vlastností.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Podmínka|Kolekce položek, které se mají iterovat Chcete-li nastavit <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, zadejte výraz Visual Basic do pole **hodnoty** v Návrháři aktivity **ForEach < t \>** v poli s textem nápovědy "zadejte výraz VB" nebo v poli **hodnoty** v okně **vlastnosti** .|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Vyhodnoceno po dokončení každé iterace. Pokud se vyhodnotí jako true, naplánované probíhající iterace se zruší. Pokud tato vlastnost není nastavená, všechny naplánované příkazy se spustí až do dokončení.|

Ve výchozím nastavení je iterátor smyčky pojmenovaný Item. Název proměnné iterátoru můžete změnit v poli **foreach** v **ParallelForEach \<T >** designeru aktivity. Iterátor smyčky lze použít ve výrazech podřízených objektů aktivity <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Viz také:

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)