---
title: Návrhář aktivity Návrhář postupu provádění-InvokeMethod
description: Přečtěte si o aktivitě InvokeMethod a o tom, jak můžete pomocí návrháře aktivity InvokeMethod vytvořit a nakonfigurovat aktivitu InvokeMethod.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ba7234ee0c5a4ab8096c020cb44345f17830540
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931211"
---
# <a name="invokemethod-activity-designer"></a>Návrhář aktivity InvokeMethod

Výraz **InvokeMethod** Designer slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.InvokeMethod> aktivity.

## <a name="the-invokemethod-activity"></a>Aktivita InvokeMethod

<xref:System.Activities.Statements.InvokeMethod>Volá veřejnou metodu zadaného objektu nebo typu.

### <a name="use-the-invokemethod-activity-designer"></a>Použití návrháře aktivity InvokeMethod

Přístup k Návrháři aktivit **InvokeMethod** v kategorii **primitivních** prvků sady **nástrojů** Návrhář aktivity **InvokeMethod** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Vyřazení návrháře aktivit vytvoří <xref:System.Activities.Statements.InvokeMethod> aktivitu s výchozí hodnotou <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře aktivity **InvokeMethod** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-invokemethod-properties"></a>Vlastnosti InvokeMethod

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.InvokeMethod> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností a některé lze upravovat na Návrhář postupu provádění ploše.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.InvokeMethod> aktivity Výchozí hodnota je InvokeMethod.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je vhodné použít jeden.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Ano|Název metody, která má být volána, když se aktivita spustí. Volaná metoda musí být deklarována jako **Public**. Tato vlastnost se dá upravovat na návrhové ploše a je povinná.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Ne|Kolekce parametrů volané metody Parametry musí být přidány do kolekce ve stejném pořadí, v jakém jsou uvedeny v signatuře metody. Chcete-li zobrazit dialogové okno **parametrů** , kde můžete nastavit tuto vlastnost, klikněte na tlačítko se třemi tečkami v poli **parametry** v mřížce vlastností. Chcete-li přidat parametry, klikněte na tlačítko **vytvořit argument** .|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Ne|Návratová hodnota volání metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Ano|Určuje, zda je metoda volána asynchronně. Výchozí hodnota je **false (NEPRAVDA**).|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Ne|Objekt, který obsahuje metodu, která má být volána. Tato vlastnost se dá upravit na návrhové ploše.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> Je nutné nastavit buď nebo.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Ne|Typ <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> . Tuto vlastnost lze upravit na návrhové ploše. Tato vlastnost musí být nastavena pouze v případě, že je metoda volána jako statická.|

K předání parametrů jako **výstupní** parametr C# (například `Method1(out myParam))` , použití dílčího **argumentu** místo **InOutArgument**

Metody s argumenty s názvem **TargetObject** nebo **Result** nelze vyvolat pomocí <xref:System.Activities.Statements.InvokeMethod> aktivity. Důvodem je, že <xref:System.Activities.Statements.InvokeMethod> aktivita registruje <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> a <xref:System.Activities.Statements.InvokeMethod.Result%2A> v <xref:System.Activities.Activity.CacheMetadata%2A> .

Algoritmus pro registraci parametrů v <xref:System.Activities.Activity.CacheMetadata%2A> je zobrazen v následujícím seznamu:

1. <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>Argument Register

2. <xref:System.Activities.Statements.InvokeMethod.Result%2A>Argument Register

3. Iterujte pomocí <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> kolekce a zaregistrujte každý argument.

Výsledná výjimka je typu <xref:System.Activities.InvalidWorkflowException> s následující zprávou: ' InvokeMethod ': proměnná, RuntimeArgument nebo argument DelegateArgument již existuje s názvem ' TargetObject '. Názvy musí být v rámci oboru prostředí jedinečné.

Toto omezení se nevztahuje na <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> a <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> . Nejedná se o argumenty pracovního postupu, proto nejsou registrovány v <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> kolekci <xref:System.Activities.Statements.InvokeMethod> aktivity v <xref:System.Activities.Activity.CacheMetadata%2A> metodě.

## <a name="see-also"></a>Viz také

- [Primitiva](../workflow-designer/primitives-activity-designers.md)
- [Řadit](../workflow-designer/assign-activity-designer.md)
- [Zpoždění](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
