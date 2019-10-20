---
title: Přepnout &lt;T &gt; návrháře aktivit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb6d4eb189b75d6e401bca0cfe50a71081760478
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660104"
---
# <a name="switchlttgt-activity-designer"></a>Přepnout &lt;T návrháře aktivit &gt;
Aktivita <xref:System.Activities.Statements.Switch%601> vyhodnotí zadaný výraz a spustí aktivitu z kolekce aktivit, jejichž přidružený klíč odpovídá hodnotě získané z vyhodnocení.

 K vytvoření a konfiguraci <xref:System.Activities.Statements.Switch%601> aktivity v [!INCLUDE[wfd1](../includes/wfd1-md.md)] se používá **\<T >** designeru aktivity Switch.

## <a name="the-switchtactivity"></a>Aktivita Switch \<T >
 Aktivita <xref:System.Activities.Statements.Switch%601> obsahuje <xref:System.Activities.Statements.Switch%601.Expression%2A> a slovník <xref:System.Activities.Statements.Switch%601.Cases%2A>. Každý případ ve slovníku se skládá z páru, který obsahuje *klíč* a aktivitu, která slouží jako odpovídající *hodnota*. Aktivita <xref:System.Activities.Statements.Switch%601> vyhodnocuje <xref:System.Activities.Statements.Switch%601.Expression%2A> a porovná je s každým klíčem. Pokud se najde shoda, spustí se odpovídající aktivita. Může být pouze jedna shoda, protože klíče slovníku musí být jedinečné v závislosti na typu rovnosti definovaném porovnávacím slovníku. Pokud se nenajde shoda, <xref:System.Activities.Statements.Switch%601.Default%2A> aktivita se spustí.

## <a name="how-to-use-the-switcht-activity-designer"></a>Jak používat \<T přepínání > návrháře aktivit
 Nástroj **Switch \<T >** Designer se dá najít v kategorii **toku řízení** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v zobrazení) **.** nebo CTRL + ALT + X.) Po přetažení do [!INCLUDE[wfd2](../includes/wfd2-md.md)] se zobrazí dialog **vybrat typy** , který uživateli umožní zadat typ *t* , který se použije v aktivitě 1. Výchozí hodnota je **Int32**. Po výběru obecného typu *T* se do návrháře pracovních postupů přidá **přepínač \<T >** Designer.

 Níže jsou uvedené vlastnosti **přepínače \<T >** Designer. Všechny tyto vlastnosti lze upravit v mřížce vlastností. Některé z nich je také možné upravovat na návrhové ploše.

 Následující tabulka uvádí nejužitečnější vlastnosti <xref:System.Activities.Statements.Switch%601> a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje popisný název návrháře <xref:System.Activities.Statements.Switch%601> aktivity. Výchozí hodnota je Switch \<Int32 >. Hodnotu lze upravit v okně **vlastnosti** nebo přímo v záhlaví návrháře.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Podmínka|Určuje výraz, který se použije k porovnání s klíči v kolekci Cases, aby se určilo, který případ se má provést.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Určuje prováděnou aktivitu, pokud nebyla nalezena žádná shoda. Kliknutím na tlačítko **Přidat aktivitu** v Návrháři otevřete **výchozí** pole, ve kterém lze aktivitu vyřadit.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Určuje případy, které mají být vyhodnoceny. Chcete-li přidat případ, klikněte na tlačítko **Přidat nový případ** v dolní části **přepínače \<T >** Designer. Tlačítko se změní na textové pole (pole se seznamem, pokud je obecný typ vybraný při přidání přepínače \<T > je řetězec nebo výčet). Po přidání klíče do pole **hodnota případu** se oblast Case rozbalí a aktivita může být vynechána tam, kde text nápovědy "Sem přetáhněte aktivitu" pro definování logiky spuštění pro daný případ.|

 Více případů lze přidat, dokud klíče Case nejsou duplikovány. V opačném případě se v dialogovém okně chyby zobrazí zpráva, že zadaný klíč Case již existuje a že je nutné zvolit jiný klíč. V **\<T přepínači** v Návrháři > může být v jednom okamžiku v rozšířeném zobrazení jen jedna oblast Case. Pokud je oblast případu ve sbaleném zobrazení, po kliknutí na oblast případu ji zvětšíte. Všimněte si, že pro sbalený případ Návrhář zobrazuje zobrazovaný název aktivity v případu na pravé straně, pokud existuje. V opačném případě se zobrazí tlačítko **Přidat aktivitu** , které rozbalí případ, pokud na něj kliknete, a umožní vám přidat aktivitu.

 Kliknutím na klíč existujícího případu změníte klíč z popisku na textové pole, abyste mohli upravit klíč případu.

 Existují dva způsoby, jak odstranit případ:

1. Vyberte případ a odstraňte ho.

2. Vyberte případ, kliknutím pravým tlačítkem zobrazte kontextovou nabídku a vyberte **Odstranit**.

   Všimněte si, že je nutné vybrat případ, který jste si ho odstranili. Výběrem a odstraněním aktivity v případě, že pouze dojde k odstranění aktivity, nikoli případu.

## <a name="see-also"></a>Viz také
 [Tok řízení](../workflow-designer/control-flow-activity-designers.md)