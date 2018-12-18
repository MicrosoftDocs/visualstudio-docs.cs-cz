---
title: ParallelForEach&lt;T&gt; Návrhář aktivity | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: eb97ba6abb40c34d03e612c346e2c721719024de
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216395"
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach&lt;T&gt; návrháře aktivit
<xref:System.Activities.Statements.ParallelForEach%601> Aktivita vytváří výčet prvků kolekce a provede vloženým příkazem pro každý prvek kolekce paralelně, který je asynchronně ve stejném vlákně. Tuto aktivitu toku řízení místo použijte <xref:System.Activities.Statements.Sequence> aktivitu, pokud se očekává, že podřízené aktivity této aktivity přejít nečinnosti.  
  
 <xref:System.Activities.Statements.ParallelForEach%601> Má aktivita <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> vlastnost, která obsahuje uživatelem zadaný [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] výrazu. <xref:System.Activities.Statements.ParallelForEach%601> Aktivita vyhodnotí tuto vlastnost po dokončení každé větve. Pokud je vyhodnocen jako **true**, pak bude <xref:System.Activities.Statements.ParallelForEach%601> dokončení aktivity bez provedení další větve. Pokud <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> nevyhodnocuje na **true**, pak bude <xref:System.Activities.Statements.ParallelForEach%601> aktivity se dokončí po dokončení všech jeho podřízených aktivit.  
  
## <a name="the-parallelforeacht-activity"></a>ParallelForEach\<T > aktivity  
 <xref:System.Activities.Statements.ParallelForEach%601> Vytvoří výčet jeho hodnoty a plány <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> pro každou hodnotu výčtu na. Pouze plány <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Jak se provádí tělo závisí na tom, zda <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> přejde nečinnosti.  
  
 Pokud <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nepřekračuje nečinný, se provede v obráceném pořadí protože naplánované aktivity jsou zpracovány jako zásobník, nejprve spustí poslední naplánované aktivity. Například, pokud máte kolekci {1,2,3,4}v <xref:System.Activities.Statements.ParallelForEach%601> a použít **WriteLine** jako text pro zápis hodnoty navýšení kapacity. Máte 4, 3, 2, 1 tisknout v konzole. Důvodem je, že **WriteLine** nepřekračuje nečinnosti, po 4 **WriteLine** získali naplánované aktivity, jsou provedeny pomocí chování zásobníku (první dovnitř poslední ven).  
  
 Ale pokud máte činnosti <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> , který můžete přejít nečinný, jako je <xref:System.ServiceModel.Activities.Receive> aktivity nebo <xref:System.Activities.Statements.Delay> aktivity. Není proč čekat na jejich dokončení. <xref:System.Activities.Statements.ParallelForEach%601> Přejde na další naplánované aktivitu tělo a zkuste ji spustit. Pokud se nepovede, která aktivitu nečinnosti, <xref:System.Activities.Statements.ParallelForEach%601> přesune na znovu na další aktivitu tělo.  
  
### <a name="using-the-parallelforeacht-activity-designer"></a>Použití ParallelForEach\<T > návrháře aktivit  
 **ParallelForEach\<T >** návrháře aktivit najdete v **tok řízení** kategorii **nástrojů**, který přistupuje po kliknutí  **Panel nástrojů** karty na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo CTRL + ALT + X.)  
  
 **ParallelForEach\<T >** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrch bez ohledu na to návrháři aktivit jsou obvykle umístěny, pro například, uvnitř **pořadí** návrháře aktivit. Po vyřazení do [!INCLUDE[wfd2](../includes/wfd2-md.md)], vytváří <xref:System.Activities.Statements.ParallelForEach%601> aktivitu, která ve výchozím nastavení obsahuje <xref:System.Activities.Activity.DisplayName%2A> z **ParallelForEach\<Int32 >.**  
  
### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach\<T > vlastnosti v Návrháři postupu provádění  
 V následující tabulce jsou uvedeny nejužitečnější <xref:System.Activities.Statements.ParallelForEach%601> vlastnosti aktivit a popisuje, jak se používají v návrháři.  
  
|Název vlastnosti|Požadováno|Použití|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje popisný Zobrazovaný název návrháře aktivit v záhlaví. Výchozí hodnota je **ParallelForEach\<Int32 >**. Hodnota může volitelně můžete upravit v **vlastnosti** mřížky nebo přímo v hlavičce návrháře aktivit.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Aktivity ke spuštění pro každou položku v kolekci. Chcete-li přidat <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> aktivity, rozevírací aktivitu z panelu nástrojů do **tělo** pole na **ParallelForEach\<T >** Návrhář aktivity s text nápovědy "Aktivity Sem přetáhněte".|  
|**TypeArgument**|Hodnota TRUE|Typ položky v <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> kolekci specifikované souborem obecný parametr *T*. Ve výchozím nastavení **TypeArgument** je nastavena na **Int32**. Chcete-li změnit typ T v **ParallelForEach\<T >** Návrhář aktivity, změňte hodnotu **TypeArgument** – pole se seznamem v mřížce vlastností.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Hodnota TRUE|Kolekce položek, které chcete iterovat. Chcete-li nastavit <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, zadejte [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] výrazu v **hodnoty** pole na **ForEach\<T >** návrháře aktivit v poli s text nápovědy "Zadejte výraz jazyka" nebo v **Hodnoty** pole na **vlastnosti** okna.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Vyhodnocuje po každé iteraci dokončí. Pokud je vyhodnocen jako true, pak plánované čekající na zrušení iterací. Pokud není tato vlastnost nastavena, všechny plánované příkazy spustit až do dokončení.|  
  
 Ve výchozím nastavení iterace smyčky je název položky. Můžete změnit název proměnné iterátoru v **ForEach** pole **ParallelForEach\<T >** návrháře aktivit. Iterace smyčky můžete použít ve výrazech v podřízených položek <xref:System.Activities.Statements.ParallelForEach%601> aktivity.  
  
## <a name="see-also"></a>Viz také  
 [Pořadí](../workflow-designer/sequence-activity-designer.md)   
 [paralelní](../workflow-designer/parallel-activity-designer.md)   
 [Tok řízení](../workflow-designer/control-flow-activity-designers.md)