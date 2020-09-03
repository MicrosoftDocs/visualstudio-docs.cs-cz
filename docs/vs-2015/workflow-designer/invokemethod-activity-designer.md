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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658989"
---
# <a name="invokemethod-activity-designer"></a>Návrhář aktivity InvokeMethod
Výraz **InvokeMethod** Designer slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.InvokeMethod> aktivity.

## <a name="the-invokemethod-activity"></a>Aktivita InvokeMethod
 <xref:System.Activities.Statements.InvokeMethod>Volá veřejnou metodu zadaného objektu nebo typu.

### <a name="using-the-invokemethod-activity-designer"></a>Pomocí návrháře aktivity InvokeMethod
 Návrhář aktivity **InvokeMethod** se dá najít v kategorii **primitivních** prvků na **panelu nástrojů**, ke kterému se dostanete kliknutím **na kartu panel nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CRTL + ALT + X).

 Návrhář aktivity **InvokeMethod** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.InvokeMethod> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře aktivity **InvokeMethod** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-invokemethod-properties"></a>Vlastnosti InvokeMethod
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.InvokeMethod> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na [!INCLUDE[wfd2](../includes/wfd2-md.md)] návrhové ploše.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.InvokeMethod> aktivity Výchozí hodnota je InvokeMethod.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Ano|Název metody, která má být volána, když se aktivita spustí. Volaná metoda musí být deklarována jako **Public**. Tato vlastnost se dá upravit na návrhové ploše. Toto je povinná vlastnost.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Ne|Kolekce parametrů volané metody Parametry musí být přidány do kolekce ve stejném pořadí, v jakém jsou uvedeny v signatuře metody. V mřížce vlastností klikněte na tlačítko se třemi tečkami v poli **parametry** , zobrazí se dialogové okno **parametry** , které vám umožní nastavit tuto vlastnost. Chcete-li přidat parametry, klikněte na tlačítko **vytvořit argument** .|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Ne|Návratová hodnota volání metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Ano|Určuje, zda je metoda volána asynchronně. Výchozí hodnota je **false (NEPRAVDA**).|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Ne|Objekt, který obsahuje metodu, která má být volána. Tato vlastnost se dá upravit na návrhové ploše.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> Je nutné nastavit buď nebo.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Ne|Typ <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> . Tuto vlastnost lze upravit na návrhové ploše. Tato vlastnost musí být nastavena pouze v případě, že je metoda volána jako statická.|

 K předání parametrů jako **výstupní** parametr jazyka C# (například `Method1(out myParam)),` byste měli použít dílčí **argument** místo **InOutArgument**

 Metody s argumenty s názvem **TargetObject** nebo **Result** nelze vyvolat pomocí <xref:System.Activities.Statements.InvokeMethod> aktivity. Důvodem je, že <xref:System.Activities.Statements.InvokeMethod> aktivita registruje <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> a <xref:System.Activities.Statements.InvokeMethod.Result%2A> v <xref:System.Activities.Activity.CacheMetadata%2A> .

 Algoritmus pro registraci parametrů v <xref:System.Activities.Activity.CacheMetadata%2A> je zobrazen v následujícím seznamu:

1. <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>Argument Register

2. <xref:System.Activities.Statements.InvokeMethod.Result%2A>Argument Register

3. Iterujte pomocí <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> kolekce a zaregistrujte každý argument.

   Výsledná výjimka je typu <xref:System.Activities.InvalidWorkflowException> s následující zprávou: ' InvokeMethod ': proměnná, RuntimeArgument nebo argument DelegateArgument již existuje s názvem ' TargetObject '. Názvy musí být v rámci oboru prostředí jedinečné.

   Toto omezení se nevztahuje na <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> a, <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> protože nejsou argumenty pracovního postupu, a proto nejsou registrovány v <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> kolekci <xref:System.Activities.Statements.InvokeMethod> Activity v <xref:System.Activities.Activity.CacheMetadata%2A> metodě.

## <a name="see-also"></a>Viz také
 [Primitivy](../workflow-designer/primitives-activity-designers.md) [přiřazují](../workflow-designer/assign-activity-designer.md) [Zpožděné zpoždění](../workflow-designer/delay-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)