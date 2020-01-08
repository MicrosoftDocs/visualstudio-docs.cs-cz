---
title: Návrhář aktivity Návrhář postupu provádění-InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8660cd82f9d671da3b535ac228e8ce62c875dc07
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593197"
---
# <a name="invokemethod-activity-designer"></a>Návrhář aktivity InvokeMethod

Výraz **InvokeMethod** Designer slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.InvokeMethod>.

## <a name="the-invokemethod-activity"></a>Aktivita InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> volá veřejnou metodu zadaného objektu nebo typu.

### <a name="use-the-invokemethod-activity-designer"></a>Použití návrháře aktivity InvokeMethod

Přístup k Návrháři aktivit **InvokeMethod** v kategorii **primitivních** prvků sady **nástrojů** Návrhář aktivity **InvokeMethod** lze přetáhnout ze **sady nástrojů** a přetáhnout na Návrhář postupu provádění plochu, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazení návrháře aktivit vytvoří aktivitu <xref:System.Activities.Statements.InvokeMethod> s výchozí <xref:System.Activities.Activity.DisplayName%2A>ou InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivit **InvokeMethod** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-invokemethod-properties"></a>Vlastnosti InvokeMethod

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.InvokeMethod> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností a některé lze upravovat na Návrhář postupu provádění ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Popisný název aktivity <xref:System.Activities.Statements.InvokeMethod>. Výchozí hodnota je InvokeMethod.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je vhodné použít jeden.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Pravda|Název metody, která má být volána, když se aktivita spustí. Volaná metoda musí být deklarována jako **Public**. Tato vlastnost se dá upravovat na návrhové ploše a je povinná.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Nepravda|Kolekce parametrů volané metody Parametry musí být přidány do kolekce ve stejném pořadí, v jakém jsou uvedeny v signatuře metody. Chcete-li zobrazit dialogové okno **parametrů** , kde můžete nastavit tuto vlastnost, klikněte na tlačítko se třemi tečkami v poli **parametry** v mřížce vlastností. Chcete-li přidat parametry, klikněte na tlačítko **vytvořit argument** .|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Nepravda|Návratová hodnota volání metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Pravda|Určuje, zda je metoda volána asynchronně. Výchozí hodnota je **False** (Nepravda).|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Nepravda|Objekt, který obsahuje metodu, která má být volána. Tato vlastnost se dá upravit na návrhové ploše.<br /><br /> Musí být nastaven buď <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>, nebo <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Nepravda|Typ připojení <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Tuto vlastnost lze upravit na návrhové ploše. Tato vlastnost musí být nastavena pouze v případě, že je metoda volána jako statická.|

Chcete-li parametry předat C# jako **výstupní** parametr (například `Method1(out myParam))`, použijte místo **argumentu** **InOutArgument**

Metody s argumenty s názvem **TargetObject** nebo **Result** nelze vyvolat pomocí aktivity <xref:System.Activities.Statements.InvokeMethod>. Důvodem je, že <xref:System.Activities.Statements.InvokeMethod> aktivita registruje <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> a <xref:System.Activities.Statements.InvokeMethod.Result%2A> v <xref:System.Activities.Activity.CacheMetadata%2A>.

Algoritmus pro registraci parametrů v <xref:System.Activities.Activity.CacheMetadata%2A> je zobrazen v následujícím seznamu:

1. Zaregistrujte <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> argument.

2. Zaregistrujte <xref:System.Activities.Statements.InvokeMethod.Result%2A> argument.

3. Iterujte pomocí kolekce <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> a zaregistrujte každý argument.

Výsledná výjimka je typu <xref:System.Activities.InvalidWorkflowException> s následující zprávou: ' InvokeMethod ': proměnná, RuntimeArgument nebo argument DelegateArgument již existuje s názvem ' TargetObject '. Názvy musí být v rámci oboru prostředí jedinečné.

Toto omezení se nevztahuje na <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> a <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Nejedná se o argumenty pracovního postupu, a proto nejsou registrovány v kolekci <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> <xref:System.Activities.Statements.InvokeMethod> aktivity v metodě <xref:System.Activities.Activity.CacheMetadata%2A>.

## <a name="see-also"></a>Viz také:

- [Primitiva](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
