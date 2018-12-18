---
title: Návrhář postupu provádění – přepínač<T> návrháře aktivit
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40e5e735fb80e6071ad9e9423eecb0284a9823cd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878183"
---
# <a name="switcht-activity-designer"></a>Přepínač\<T > návrháře aktivit

<xref:System.Activities.Statements.Switch%601> Aktivita vyhodnotí zadaný výraz a spustí aktivita z kolekce aktivit, jejichž přidružené klíč odpovídá hodnotě získané z vyhodnocení.

**Přepínač < T\>**  Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.Activities.Statements.Switch%601> aktivity v Návrháři pracovních postupů.

## <a name="the-switchtactivity"></a>Přepínač\<T > aktivity

A <xref:System.Activities.Statements.Switch%601> obsahuje aktivity <xref:System.Activities.Statements.Switch%601.Expression%2A> a slovník <xref:System.Activities.Statements.Switch%601.Cases%2A>. Každý případ ve slovníku se skládá z dvojice, který obsahuje *klíč* a aktivitu, která slouží jako odpovídající *hodnota*. <xref:System.Activities.Statements.Switch%601> Aktivita vyhodnotí <xref:System.Activities.Statements.Switch%601.Expression%2A> a porovná je s jednotlivým klíčům. Pokud se najde shoda, bude odpovídající aktivita je provedena. Pouze jediná shoda je možné, protože slovník klíčů musí být jedinečný podle typu rovnosti určené rovnosti slovníku. Pokud není nalezena žádná shoda, <xref:System.Activities.Statements.Switch%601.Default%2A> provádění aktivity.

## <a name="how-to-use-the-switcht-activity-designer"></a>Jak použít přepínač\<T > návrháře aktivit

Přístup **přepínač\<T >** návrháře aktivit v **tok řízení** kategorii **nástrojů**. Po jeho umístěním do návrháře postupu provádění, zobrazí **vyberte typy** dialogového okna, umožníte uživateli zadat obecného typu *T* používané <xref:System.Activities.Statements.Switch%601> aktivity. Výchozí hodnota je **Int32**. Jednou obecného typu *T* byla vybrána, **přepínač < T\>**  návrháře se přidá do návrháře postupu provádění.

Toto jsou vlastnosti **přepínač < T\>**  návrháře. Všechny tyto vlastnosti můžete upravit v mřížce vlastností. Některé z nich můžete také upravit na plochu návrháře.

V následující tabulce jsou uvedeny nejužitečnější <xref:System.Activities.Statements.Switch%601> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje popisný název <xref:System.Activities.Statements.Switch%601> návrháře aktivit. Výchozí hodnota je přepínač < Int32\>. Hodnotu lze upravit v **vlastnosti** okno nebo přímo v hlavičce návrháře.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je osvědčeným postupem je použití jednoho.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Hodnota TRUE|Určuje výraz určený k porovnání s klíči v kolekci případy k určení takovém ke spuštění.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Určuje aktivita spustí, pokud není nalezena žádná shoda. Klikněte na tlačítko **přidat aktivitu** tlačítko v Návrháři můžete otevřít **výchozí** pole, ve kterém můžete vyřadit aktivity.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Určuje případy, který se má vyhodnotit. Chcete-li přidat případ, klikněte na tlačítko **přidat nový případ** tlačítko v dolní části **přepínač\<T >** návrháře. Tlačítko se změní na textové pole (– pole se seznamem při výběru obecného typu při přidávání přepínač\<T > je řetězec nebo výčet). Po přidání klíče **malá a velká hodnota** pole oblasti případu rozšiřuje a aktivitu můžete vyřadit, kde text nápovědy "Sem přetáhněte aktivitu" k definování logiky provádění pro případ.|

Lze přidat více případů tak dlouho, dokud se neduplikují případu klíče. V opačném případě dialogovým oknem chyby zobrazí oznámení, že již existuje zadaný klíč případu a, je nutné vybrat jiný klíč. V **přepínač\<T >** návrháře, může být pouze jeden případ oblasti v rozšířené zobrazení najednou. Pokud případu oblasti je v sbaleným zobrazením, kliknutím na oblasti případu umožňuje jeho rozšíření. Všimněte si, že pro případ sbalený návrháře zobrazuje zobrazovaný název aktivity v případě na pravé straně Pokud neexistuje žádný. V opačném případě se zobrazí **přidat aktivitu** tlačítko, které rozšiřuje tento případ, pokud klepnete na tlačítko a umožňuje přidat aktivitu.

Kliknutím na klávesu existující případu se změní klíč z popisek do textové pole tak, aby bylo možné upravit klíč případu.

Chcete-li odstranit případ 2 způsoby:

- Vyberte tento případ a odstraňte ho.

- Vyberte velikosti písmen, klikněte pravým tlačítkem a zobrazit kontextovou nabídku a vyberte **odstranit**.

Všimněte si, že je nutné vybrat případ samotný ho odstranit. Výběr a odstraněním aktivity v případě odstraní pouze aktivity tomu tak není.

## <a name="see-also"></a>Viz také:

- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)