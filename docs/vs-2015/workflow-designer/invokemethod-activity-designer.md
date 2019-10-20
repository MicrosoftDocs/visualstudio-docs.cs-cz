---
title: Návrhář aktivity InvokeMethod | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fcfba979ba7fce4aeffab1fe9e9a5a3728e513af
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658989"
---
# <a name="invokemethod-activity-designer"></a>Návrhář aktivity InvokeMethod
Výraz **InvokeMethod** Designer slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.InvokeMethod>.

## <a name="the-invokemethod-activity"></a>Aktivita InvokeMethod
 @No__t_0 volá veřejnou metodu zadaného objektu nebo typu.

### <a name="using-the-invokemethod-activity-designer"></a>Pomocí návrháře aktivity InvokeMethod
 Návrhář aktivity **InvokeMethod** se dá najít v kategorii **primitivních** prvků na **panelu nástrojů**, ke kterému se dostanete kliknutím na kartu **panelu nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CRTL + ALT + X.)

 Návrhář aktivity **InvokeMethod** lze přetáhnout ze **sady nástrojů** a přetáhnout na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.InvokeMethod> s výchozí <xref:System.Activities.Activity.DisplayName%2A>ou InvokeMethod. @No__t_0 lze upravit v záhlaví návrháře aktivit **InvokeMethod** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-invokemethod-properties"></a>Vlastnosti InvokeMethod
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.InvokeMethod> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé mohou být upravovány na [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer povrchu.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.InvokeMethod>. Výchozí hodnota je InvokeMethod.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Podmínka|Název metody, která má být volána, když se aktivita spustí. Volaná metoda musí být deklarována jako **Public**. Tato vlastnost se dá upravit na návrhové ploše. Toto je povinná vlastnost.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Kolekce parametrů volané metody Parametry musí být přidány do kolekce ve stejném pořadí, v jakém jsou uvedeny v signatuře metody. V mřížce vlastností klikněte na tlačítko se třemi tečkami v poli **parametry** , zobrazí se dialogové okno **parametry** , které vám umožní nastavit tuto vlastnost. Chcete-li přidat parametry, klikněte na tlačítko **vytvořit argument** .|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Návratová hodnota volání metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Podmínka|Určuje, zda je metoda volána asynchronně. Výchozí hodnota je **false (NEPRAVDA**).|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Objekt, který obsahuje metodu, která má být volána. Tato vlastnost se dá upravit na návrhové ploše.<br /><br /> Musí být nastaven buď <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>, nebo <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Typ <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Tuto vlastnost lze upravit na návrhové ploše. Tato vlastnost musí být nastavena pouze v případě, že je metoda volána jako statická.|

 Chcete-li parametry předat C# jako **výstupní** parametr (například `Method1(out myParam)),` měli byste použít dílčí **argument** namísto **InOutArgument**

 Metody s argumenty s názvem **TargetObject** nebo **Result** nelze vyvolat pomocí aktivity <xref:System.Activities.Statements.InvokeMethod>. Důvodem je, že <xref:System.Activities.Statements.InvokeMethod> aktivita registruje <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> a <xref:System.Activities.Statements.InvokeMethod.Result%2A> v <xref:System.Activities.Activity.CacheMetadata%2A>.

 Algoritmus pro registraci parametrů v <xref:System.Activities.Activity.CacheMetadata%2A> je zobrazen v následujícím seznamu:

1. Zaregistrujte <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> argument.

2. Zaregistrujte <xref:System.Activities.Statements.InvokeMethod.Result%2A> argument.

3. Iterujte pomocí kolekce <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> a zaregistrujte každý argument.

   Výsledná výjimka je typu <xref:System.Activities.InvalidWorkflowException> s následující zprávou: ' InvokeMethod ': proměnná, RuntimeArgument nebo argument DelegateArgument již existuje s názvem ' TargetObject '. Názvy musí být v rámci oboru prostředí jedinečné.

   Toto omezení se nevztahuje na <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> a <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>, protože se nejedná o argumenty pracovního postupu, a proto nejsou registrovány v <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> kolekci <xref:System.Activities.Statements.InvokeMethod> aktivity v <xref:System.Activities.Activity.CacheMetadata%2A> metodě.

## <a name="see-also"></a>Viz také
 [Primitivy](../workflow-designer/primitives-activity-designers.md) [přiřazují](../workflow-designer/assign-activity-designer.md) [Zpožděné zpoždění](../workflow-designer/delay-activity-designer.md) [](../workflow-designer/writeline-activity-designer.md)