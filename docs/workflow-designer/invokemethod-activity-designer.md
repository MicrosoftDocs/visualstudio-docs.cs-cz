---
title: Návrhář postupu provádění – Návrhář aktivity InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ac82e36d3abc942e0c5492cc4d7acf347eba36c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839567"
---
# <a name="invokemethod-activity-designer"></a>Návrhář aktivity InvokeMethod

**InvokeMethod** Návrhář slouží k vytvoření a konfigurace <xref:System.Activities.Statements.InvokeMethod> aktivity.

## <a name="the-invokemethod-activity"></a>Aktivity InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> Volá veřejná metoda zadaného objektu nebo typu.

### <a name="use-the-invokemethod-activity-designer"></a>Použijte Návrhář aktivity InvokeMethod

Přístup **InvokeMethod** návrháře aktivit v **primitiv** kategorii **nástrojů**. **InvokeMethod** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění, pokud už aktivity jsou obvykle umístěny, například jako uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazení Návrhář aktivity vytvoří <xref:System.Activities.Statements.InvokeMethod> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> z InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A> Můžete upravovat v záhlaví **InvokeMethod** Návrhář aktivity nebo v **DisplayName** pole mřížku vlastností.

### <a name="the-invokemethod-properties"></a>Vlastnosti InvokeMethod

Následující tabulka ukazuje <xref:System.Activities.Statements.InvokeMethod> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností a můžete upravit některé na plochu návrháře postupu provádění.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název <xref:System.Activities.Statements.InvokeMethod> aktivity. Výchozí hodnota je InvokeMethod.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, doporučujeme použít jednu.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Hodnota TRUE|Název metody, která volá se, když tato aktivity spustí. Volané metody musí být deklarována jako **veřejné**. Tuto vlastnost lze na návrhové ploše upravovat a je povinný.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Kolekce parametrů volané metody. Parametry musí být přidán do kolekce ve stejném pořadí, ve kterém jsou uvedeny v podpisu metody. Chcete-li zobrazit **parametry** dialogové okno, kde můžete nastavit tuto vlastnost, klikněte na tlačítko se třemi tečkami v **parametry** pole mřížku vlastností. Klikněte na tlačítko **vytvořit Argument** tlačítko Přidat parametry.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Návratová hodnota volání metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Hodnota TRUE|Určuje, zda je metoda volána asynchronně. Výchozí hodnota je **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Objekt, který obsahuje metodu volání. Tato vlastnost se dá upravit na plochu návrháře.<br /><br /> Buď <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> nebo <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> je potřeba nastavit.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Typ <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Tato vlastnost se dá upravit na návrhové ploše. Tato vlastnost musí nastavit jen v případě, že metoda je statická.|

Pro předání parametrů jako C# **si** parametr (například `Method1(out myParam))`, použijte **výstupní argument OutArgument** místo **InOutArgument**

Metody s argumenty volat **TargetObject** nebo **výsledek** nelze volat pomocí <xref:System.Activities.Statements.InvokeMethod> aktivity. Důvodem je, že <xref:System.Activities.Statements.InvokeMethod> aktivity registrů <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> a <xref:System.Activities.Statements.InvokeMethod.Result%2A> v <xref:System.Activities.Activity.CacheMetadata%2A>.

Algoritmus pro registraci parametry v <xref:System.Activities.Activity.CacheMetadata%2A> je znázorněno v následujícím seznamu:

1.  Zaregistrujte <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> argument.

2.  Zaregistrujte <xref:System.Activities.Statements.InvokeMethod.Result%2A> argument.

3.  Iterovat přes <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> kolekce a zaregistrovat každý argument.

Výsledný výjimka je typu <xref:System.Activities.InvalidWorkflowException> s následující zprávou: 'InvokeMethod': Proměnná argumentu RuntimeArgument nebo DelegateArgument již existuje s názvem "TargetObject". Názvy musí být v rámci oboru prostředí jedinečné.

Toto omezení neplatí pro <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> a <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Nejste argumentů pracovního postupu a proto nejsou registrovány v <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> kolekce <xref:System.Activities.Statements.InvokeMethod> aktivity v <xref:System.Activities.Activity.CacheMetadata%2A> metody.

## <a name="see-also"></a>Viz také:

- [Primitiva](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)