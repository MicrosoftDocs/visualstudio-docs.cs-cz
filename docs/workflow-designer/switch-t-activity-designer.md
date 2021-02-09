---
title: '&lt;Návrhář aktivity T Návrhář postupu provádění-Switch &gt;'
description: Naučte se používat <T> Návrháře aktivity Switch k vytvoření a konfiguraci <T> aktivity přepnutí v Návrhář postupu provádění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 35dcc390dcf58e02a2c7c1fa2dba62840d433785
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882307"
---
# <a name="switcht-activity-designer"></a>Návrhář aktivity Switch\<T>

<xref:System.Activities.Statements.Switch%601>Aktivita vyhodnotí zadaný výraz a spustí aktivitu z kolekce aktivit, jejichž přidružený klíč odpovídá hodnotě získané z vyhodnocení.

Editor aktivity **Switch<\> T** se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Switch%601> aktivity v Návrhář postupu provádění.

## <a name="the-switchtactivity"></a>Aktivita Switch \<T>

<xref:System.Activities.Statements.Switch%601>Aktivita obsahuje <xref:System.Activities.Statements.Switch%601.Expression%2A> slovník a slovníku <xref:System.Activities.Statements.Switch%601.Cases%2A> . Každý případ ve slovníku se skládá z páru, který obsahuje *klíč* a aktivitu, která slouží jako odpovídající *hodnota*. Tato <xref:System.Activities.Statements.Switch%601> Aktivita vyhodnotí <xref:System.Activities.Statements.Switch%601.Expression%2A> a porovná je s každým klíčem. Pokud se najde shoda, spustí se odpovídající aktivita. Může být pouze jedna shoda, protože klíče slovníku musí být jedinečné v závislosti na typu rovnosti definovaném porovnávacím slovníku. Pokud se nenajde žádná shoda, <xref:System.Activities.Statements.Switch%601.Default%2A> aktivita se spustí.

## <a name="how-to-use-the-switcht-activity-designer"></a>Jak používat \<T> Návrháře aktivity Switch

Přihlaste se k Návrháři aktivity **Switch \<T>** v kategorii **tok řízení** v **sadě nástrojů**. Po přetažení do Návrhář postupu provádění se zobrazí dialogové okno **vybrat typy** , které uživateli umožní zadat typ *T* použitý v <xref:System.Activities.Statements.Switch%601> aktivitě. Výchozí hodnota je **Int32**. Po výběru obecného typu *t* se do návrháře pracovních postupů přidá **přepínač<\> T** Designer.

Níže jsou uvedené vlastnosti **přepínače<T \>** Designer. Všechny tyto vlastnosti lze upravit v mřížce vlastností. Některé z nich je také možné upravovat na návrhové ploše.

V následující tabulce jsou uvedeny nejužitečnější <xref:System.Activities.Statements.Switch%601> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje popisný název <xref:System.Activities.Statements.Switch%601> návrháře aktivit. Výchozí hodnota je Switch<Int32 \> . Hodnotu lze upravit v okně **vlastnosti** nebo přímo v záhlaví návrháře.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Ano|Určuje výraz, který se použije k porovnání s klíči v kolekci Cases, aby se určilo, který případ se má provést.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Určuje prováděnou aktivitu, pokud nebyla nalezena žádná shoda. Kliknutím na tlačítko **Přidat aktivitu** v Návrháři otevřete **výchozí** pole, ve kterém lze aktivitu vyřadit.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Určuje případy, které mají být vyhodnoceny. Chcete-li přidat případ, klikněte na tlačítko **Přidat nový případ** v dolní části **Návrháře \<T> přepínače** . Tlačítko se změní na textové pole (pole se seznamem, pokud je obecný typ vybraný při přidávání přepínače \<T> řetězec nebo výčet). Po přidání klíče do pole **hodnota případu** se oblast Case rozbalí a aktivita může být vynechána tam, kde text nápovědy "Sem přetáhněte aktivitu" pro definování logiky spuštění pro daný případ.|

Více případů lze přidat, dokud klíče Case nejsou duplikovány. V opačném případě se v dialogovém okně chyby zobrazí zpráva, že zadaný klíč Case již existuje a že je nutné zvolit jiný klíč. V Návrháři **přepínače \<T>** může být v jednom okamžiku v rozšířeném zobrazení pouze jedna oblast Case. Pokud je oblast případu ve sbaleném zobrazení, po kliknutí na oblast případu ji zvětšíte. Všimněte si, že pro sbalený případ Návrhář zobrazuje zobrazovaný název aktivity v případu na pravé straně, pokud existuje. V opačném případě se zobrazí tlačítko **Přidat aktivitu** , které rozbalí případ, pokud na něj kliknete, a umožní vám přidat aktivitu.

Kliknutím na klíč existujícího případu změníte klíč z popisku na textové pole, abyste mohli upravit klíč případu.

Existují dva způsoby, jak odstranit případ:

- Vyberte případ a odstraňte ho.

- Vyberte případ, kliknutím pravým tlačítkem zobrazte kontextovou nabídku a vyberte **Odstranit**.

Všimněte si, že je nutné vybrat případ, který jste si ho odstranili. Výběrem a odstraněním aktivity v případě, že pouze dojde k odstranění aktivity, nikoli případu.

## <a name="see-also"></a>Viz také

- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
