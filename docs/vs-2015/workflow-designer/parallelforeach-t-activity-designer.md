---
title: '&lt; &gt; Návrhář aktivity ParallelForEach T | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c659e941a8503a0d5ff601fea23fcec69b2bbcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672603"
---
# <a name="parallelforeachlttgt-activity-designer"></a>&lt; &gt; Návrhář aktivity ParallelForEach T
<xref:System.Activities.Statements.ParallelForEach%601>Aktivita vytvoří výčet prvků kolekce a provede vložený příkaz pro každý prvek kolekce paralelně, který je asynchronně ve stejném vlákně. Tuto aktivitu řízení toku použijte místo aktivity, <xref:System.Activities.Statements.Sequence> Pokud se očekává, že se podřízené aktivity této aktivity dostanou nečinné.

 <xref:System.Activities.Statements.ParallelForEach%601>Aktivita má <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> vlastnost, která obsahuje výraz zadaný uživatelem [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . <xref:System.Activities.Statements.ParallelForEach%601>Aktivita vyhodnotí tuto vlastnost po dokončení každé větve. Pokud se vyhodnotí jako **true**, <xref:System.Activities.Statements.ParallelForEach%601> aktivita se dokončí bez provedení ostatních větví. Pokud se <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> nevyhodnotí jako **true**, aktivita se <xref:System.Activities.Statements.ParallelForEach%601> dokončí po dokončení všech jejích podřízených aktivit.

## <a name="the-parallelforeacht-activity"></a>Aktivita ParallelForEach \<T>
 <xref:System.Activities.Statements.ParallelForEach%601> Vytvoří výčet svých hodnot a naplánuje <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> pro každou hodnotu, na které se vytváří výčet. Pouze plánuje <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> . Způsob provádění textu závisí na tom, zda je <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nečinný.

 Pokud se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nejedná o nečinný, provede se v obráceném pořadí, protože naplánované aktivity jsou zpracovávány jako zásobník, nejprve se spustí poslední naplánovaná aktivita. Například v případě, že máte kolekci v nástroji {1,2,3,4} <xref:System.Activities.Statements.ParallelForEach%601> a použijte jako tělo k zápisu hodnoty **WriteLine** . V konzole máte 4, 3, 2, 1. Je to proto, že se **WriteLine** nepracuje, takže když se naplánuje 4 aktivity **WriteLine** , provedou se pomocí chování zásobníku (první v poslední době).

 Ale v případě, že máte aktivity <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> , které můžou jít nečinné, jako je <xref:System.ServiceModel.Activities.Receive> aktivita nebo <xref:System.Activities.Statements.Delay> aktivita. Pak není nutné čekat na jejich dokončení. <xref:System.Activities.Statements.ParallelForEach%601> přejde na další plánovaný subjekt aktivity a pokusí se ji spustit. Pokud se tato aktivita přestane vymezit, <xref:System.Activities.Statements.ParallelForEach%601> přejde znovu na další aktivitu těla.

### <a name="using-the-parallelforeacht-activity-designer"></a>Pomocí \<T> Návrháře aktivity ParallelForEach
 Návrhář **aktivity \<T> ParallelForEach** se dá najít v kategorii **toku řízení** na **panelu nástrojů**, ke které se dostanete tak, že kliknete na kartu **panel nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).)

 Návrhář **aktivity \<T> ParallelForEach** lze přetáhnout ze **sady nástrojů** a na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěna návrháři aktivit, například uvnitř návrháře aktivity **sekvence** . Po jejím odstranění se [!INCLUDE[wfd2](../includes/wfd2-md.md)] vytvoří <xref:System.Activities.Statements.ParallelForEach%601> aktivita, která ve výchozím nastavení obsahuje hodnotu <xref:System.Activities.Activity.DisplayName%2A> **ParallelForEach \<Int32> .**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach \<T> vlastnosti v Návrhář postupu provádění
 Následující tabulka uvádí nejužitečnější <xref:System.Activities.Statements.ParallelForEach%601> vlastnosti aktivity a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje popisný zobrazovaný název návrháře aktivit v hlavičce. Výchozí hodnota je **ParallelForEach \<Int32> **. Hodnota může být volitelně upravena v mřížce **vlastnosti** nebo přímo v hlavičce návrháře aktivit.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|Ne|Aktivita, která se má spustit pro každou položku v kolekci. Chcete-li přidat <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> aktivitu, přetáhněte aktivitu ze sady nástrojů do pole **text** v Návrháři aktivity **ParallelForEach \<T> ** s textem nápovědy "Sem přetáhněte aktivitu".|
|**Pro TypeArgument**|Ano|Typ položek v <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> kolekci určené obecným parametrem *T*. Ve výchozím nastavení je **pro TypeArgument** nastaveno na hodnotu **Int32**. Chcete-li změnit typ T v Návrháři aktivity **ParallelForEach \<T> ** , změňte hodnotu pole se seznamem **pro TypeArgument** v mřížce vlastností.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Ano|Kolekce položek, které se mají iterovat Chcete-li nastavit <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> , zadejte [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] výraz do pole **hodnoty** v Návrháři aktivity **foreach \<T> ** v poli s textem nápovědy "zadejte výraz VB" nebo v poli **hodnoty** v okně **vlastnosti** .|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Vyhodnoceno po dokončení každé iterace. Pokud se vyhodnotí jako true, naplánované probíhající iterace se zruší. Pokud tato vlastnost není nastavená, všechny naplánované příkazy se spustí až do dokončení.|

 Ve výchozím nastavení je iterátor smyčky pojmenovaný Item. Název proměnné iterátoru můžete změnit v poli **foreach** v Návrháři aktivity **ParallelForEach \<T> ** . Iterátor smyčky lze použít ve výrazech v podřízených objektech <xref:System.Activities.Statements.ParallelForEach%601> aktivity.

## <a name="see-also"></a>Viz také
 [Sekvence](../workflow-designer/sequence-activity-designer.md) [paralelního](../workflow-designer/parallel-activity-designer.md) [řízení toku](../workflow-designer/control-flow-activity-designers.md)