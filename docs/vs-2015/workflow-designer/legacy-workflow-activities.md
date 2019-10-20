---
title: Starší verze aktivit pracovního postupu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f4f1110424aefc1771c0dc7600fb9996bff0e892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658944"
---
# <a name="legacy-workflow-activities"></a>Aktivity starších verzí pracovních postupů
[!INCLUDE[wf](../includes/wf-md.md)] obsahuje výchozí sadu aktivit, které poskytují funkce pro řízení toku, podmínky, zpracování událostí, správu stavu a komunikaci s aplikacemi a službami. Při navrhování pracovních postupů můžete použít aktivity poskytované systémem, které jsou poskytovány [!INCLUDE[wfd1](../includes/wfd1-md.md)], nebo můžete vytvořit vlastní aktivity.

 V následující tabulce je uvedena sada aktivit připraveného pro [!INCLUDE[wf2](../includes/wf2-md.md)] Framework. Mnohé, ale ne všechny, z těchto aktivit jsou zastoupeny návrháři aktivity, ke kterým je možné přistoupit ze sady **nástrojů** [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Chcete-li vytvořit aktivitu, přetáhněte jejího návrháře z **panelu nástrojů** a přetáhněte jej na návrhovou plochu.

|Aktivita|Popis|
|--------------|-----------------|
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Používá se s aktivitou **Aktivita typu HandleExternalEventActivity** pro vstupní a výstupní komunikaci s místní službou. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Slouží k zahrnutí logiky čištění pro složenou aktivitu, která byla zrušena před dokončením provádění všech podřízených objektů složené aktivity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Umožňuje přidat Visual Basic nebo C# kód do pracovního postupu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Aktivita nadřazená verze [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Aktivita nadřazená verze **aktivitě typu TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|
|[Aktivita typu CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Umožňuje volat kód k vrácení zpět nebo kompenzaci operací, které jsou již provedeny pracovním postupem, když dojde k chybě. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivita typu CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Obálka pro jednu nebo více aktivit, které provádějí kompenzaci pro dokončenou aktivitu aktivitě typu TransactionScopeActivity [!INCLUDE[crdefault](../includes/crdefault-md.md)][pomocí aktivity CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|
|[Aktivitou skupiny ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Provede podřízené aktivity na základě podmínky, která se vztahuje na vlastní aktivitu [aktivitou skupiny ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) a na základě podmínek, které platí samostatně pro každou podřízenou položku. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivitou skupiny ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|
|[Aktivitu typu DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Umožňuje sestavovat zpoždění v pracovním postupu, které jsou založeny na intervalu časového limitu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivitu typu DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Zalomí jednu nebo více aktivit, které se spustí, když dojde k zadané události. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Poskytuje rozhraní pro přidružení událostí k aktivitě. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Provede svoji hlavní podřízenou aktivitu souběžně s [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|
|[Aktivitu typu FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Slouží k zpracování výjimky typu, který zadáte. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivitu typu FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Představuje složenou aktivitu, která má seřazený seznam podřízených aktivit typu [aktivitu typu FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|
|[Aktivita typu HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Používá se ve spojení s aktivitou [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) pro vstupní a výstupní komunikaci s místní službou. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivita typu HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Testuje podmínku v každé větvi a provádí aktivity na první větvi, pro kterou je podmínka rovna hodnotě **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Představuje větev [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Umožňuje vašemu pracovnímu postupu vyvolat webovou službu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|
|[Aktivitu typu InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Umožňuje vašemu pracovnímu postupu vyvolat jiný pracovní postup. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivitu typu InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|
|[Aktivita typu ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Složená aktivita, která obsahuje pouze podřízené aktivity [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) . [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivita typu ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|
|[Aktivita typu ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Poskytuje způsob, jak naplánovat zpracování dvou nebo více podřízených větví aktivit **SequenceActivity** ve stejnou dobu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivita typu ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|
|[Sady](http://go.microsoft.com/fwlink?LinkID=65019)|Slouží k reprezentaci kolekce pravidel. Pravidlo se skládá z podmínek a výsledných akcí. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity sady](http://go.microsoft.com/fwlink?LinkID=65004).|
|[Aktivita ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Vytvoří více instancí jedné podřízené aktivity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity Aktivita ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Poskytuje jednoduchý způsob, jak propojit více aktivit dohromady pro následné spuštění. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Určuje přechod do nového stavu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Představuje stav pracovního postupu stavového stroje. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Používá se v aktivitě [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) jako kontejner pro podřízené aktivity, které se provádějí při ukončování aktivity **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Používá se v aktivitě [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) jako kontejner pro podřízené aktivity, které jsou spouštěny při vstupu do aktivity **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|
|[Aktivita typu SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Pozastaví operaci pracovního postupu, aby umožnil zásah v případě některých chybových stavů, které vyžadují zvláštní pozornost. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivita typu SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Provede obsažené aktivity postupně v synchronizované doméně. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Umožňuje okamžitě ukončit operaci pracovního postupu v případě chybového stavu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Umožňuje zachytit podnikové výjimky vyvolané jako součást metadat procesu pro pracovní postup. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|
|[Aktivitě typu TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Poskytuje rozhraní pro transakce a zpracování výjimek. Další informace najdete v tématu [použití aktivity aktivitě typu TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|
|[Aktivita WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Umožňuje modelovat výskyt chyby webové služby. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivita WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|
|[Provedení](http://go.microsoft.com/fwlink?LinkID=65047)|Přijímá data z webové služby. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|
|[Typu](http://go.microsoft.com/fwlink?LinkID=65048)|Odpoví na požadavek webové služby, který byl proveden na pracovní postup. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|
|[Aktivita typu WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Umožňuje vašemu pracovnímu postupu cyklovat, dokud není splněna podmínka. [!INCLUDE[crdefault](../includes/crdefault-md.md)][použití aktivity aktivita typu WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] vytváření vlastních aktivit najdete v tématu [vývoj vlastních aktivit](http://go.microsoft.com/fwlink?LinkID=65023) a [používání starší verze návrháře aktivit](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>V tomto oddílu
 [Zobrazení aktivit (starší verze)](../workflow-designer/activity-views-legacy.md) Popisuje různá návrhová zobrazení aktivit.

 [Postupy: přidání aktivit do sady nástrojů (starší verze)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Ukazuje, jak přidat aktivity do sady nástrojů.

 [Postupy: vytvoření podmínky deklarativního pravidla (starší verze)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Zobrazuje kroky pro vytvoření podmínky deklarativního pravidla.

 [Postupy: vytvoření sady pravidel sady (starší verze)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Zobrazuje kroky pro vytvoření sady pravidel sady.

 [Postupy: implementace operace kontraktu WCF (starší verze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Zobrazuje kroky pro implementaci operace [!INCLUDE[indigo2](../includes/indigo2-md.md)] kontraktu.

 [Postupy: volání operace kontraktu WCF (starší verze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Zobrazuje kroky pro vyvolání operace kontraktu [!INCLUDE[indigo2](../includes/indigo2-md.md)].

## <a name="see-also"></a>Viz také
 [Programovací model Windows Workflow Foundation aktivity](http://go.microsoft.com/fwlink?LinkID=65005) [vyvíjející pracovní postupy](http://go.microsoft.com/fwlink?LinkID=65010) při [vývoji aktivit pracovního postupu](http://go.microsoft.com/fwlink?LinkID=65023)