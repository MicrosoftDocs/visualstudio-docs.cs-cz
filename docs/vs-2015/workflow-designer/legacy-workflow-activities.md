---
title: Aktivity starších verzí pracovních postupů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6ff21a431e380a281ce1261215367b89c4ecf1a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205396"
---
# <a name="legacy-workflow-activities"></a>Aktivity starších verzí pracovních postupů
[!INCLUDE[wf](../includes/wf-md.md)] obsahuje výchozí sadu aktivit, které poskytují funkce pro tok řízení, podmínky, zpracování událostí, správu stavu a komunikaci s aplikacemi a službami. Při návrhu pracovních postupů, můžete použít aktivity poskytnuté systémem, které jsou poskytovány [!INCLUDE[wfd1](../includes/wfd1-md.md)], nebo můžete vytvořit vlastní vlastní aktivity.  
  
 Následující tabulce jsou uvedeny [!INCLUDE[wf2](../includes/wf2-md.md)] sadu aktivit out-of-box framework. Mnoho, ale ne všechny tyto aktivity jsou reprezentované prostřednictvím návrháře aktivit, které lze přistupovat z **nástrojů** z [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Chcete-li vytvořit aktivitu, přetáhněte jeho návrháře z **nástrojů** a umístěte jej na návrhové ploše.  
  
|Aktivita|Popis|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Používá se **aktivita typu HandleExternalEventActivity** aktivity pro vstupní a výstupní komunikaci s místní službou. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Původně obsahovaly vyčištění logiku pro složené aktivity zrušena dříve, než všechny složené aktivity dětí po dokončení provádění. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Pomocí aktivitu typu CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Umožňuje přidat kódu jazyka Visual Basic nebo C# do svého pracovního postupu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Aktivita verze [aktivitu typu SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Aktivita verze **aktivity typu TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[Aktivita typu CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Umožňuje volat kód vrátit zpět nebo jako kompenzaci za operace již provádí pracovní postup, když dojde k chybě. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivita typu CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Obálka pro jeden nebo více aktivit, které provádějí kompenzaci za dokončené aktivity typu TransactionScopeActivity [!INCLUDE[crdefault](../includes/crdefault-md.md)] [pomocí aktivitu typu CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[Skupina ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Provede podřízené aktivity na základě podmínky, které platí pro [aktivitou skupiny ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) aktivity samotného a na základě podmínek, které platí samostatně pro každý podřízený prvek. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivitou skupiny ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[Aktivitu typu DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Umožňuje vytvářet zpoždění v pracovním postupu, které jsou založeny na interval časového limitu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity typu DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Zabalí jednu nebo víc aktivit, které jsou spouštěny, když dojde k určité události. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[Aktivitu typu EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Poskytuje rozhraní pro přidružení událostí s aktivitou. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivitu typu EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[Aktivitu EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Spustí jeho hlavní podřízená aktivita současně se [aktivitu typu EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity typu EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[Typu FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Použít ke zpracování výjimky typu, který zadáte. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity typu FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[Typu FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Představuje složenou aktivitu, která má uspořádaný seznam podřízených aktivit typu [typu FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity typu FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[Aktivita typu HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Použít ve spojení s [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) aktivity pro vstupní a výstupní komunikaci s místní službou. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivita typu HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[Aktivita typu IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Testuje podmínku v každé větvi a provádí aktivity na první větev, pro který se rovná podmínka **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivita typu IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Představuje větvení [aktivita typu IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[Typu InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Umožňuje pracovního postupu k vyvolání webové služby. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity typu InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[Aktivitu typu InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Umožňuje pracovního postupu, který má být vyvolán jiný pracovní postup. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivitu typu InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[Aktivita typu ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Složená aktivita, která obsahuje pouze [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) podřízené aktivity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivita typu ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[Aktivita typu ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Poskytuje způsob, jak naplánovat nejmíň dva podřízené **aktivitu typu SequenceActivity** větví aktivity pro zpracování ve stejnou dobu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivitě typu ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[Aktivitě PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Použijte k vyjádření kolekce pravidel. Pravidlo obsahuje podmínky a výsledné akce. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivitě PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[Aktivitou typu ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Vytvoří více instancí o jednu podřízenou aktivitu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivitou typu ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[Aktivitu typu SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Poskytuje jednoduchý způsob, jak propojit více aktivit pro sekvenční provádění. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivitu typu SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Určuje přechod na nový stav. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[Umístit aktivitu StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Představuje stav pracovní postup stavového stroje. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity umístit aktivitu StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Používané [umístit aktivitu StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) aktivity jako kontejner pro podřízené aktivity, které jsou spouštěny při opuštění **umístit aktivitu StateActivity** aktivity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Používané [umístit aktivitu StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) aktivity jako kontejner pro podřízené aktivity, které jsou spouštěny, když zadáte **umístit aktivitu StateActivity** aktivity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[Aktivita typu SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Pozastaví operaci svůj pracovní postup pro povolení zásah v případě určitý chybový stav, který vyžaduje pozornost. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivita typu SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Provádí obsažené aktivity postupně v synchronizované doméně. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Umožňuje okamžitě ukončení operace pracovního postupu v případě chybového stavu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Umožňuje zachytit výjimky firmy jako součást procesu metadata pro pracovní postup. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[Aktivita typu TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Poskytuje rozhraní pro transakce a zpracování výjimek. Další informace najdete v tématu [pomocí aktivity typu TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[Aktivita WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Umožňuje modelovat výskyt chyby webové služby. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity Aktivita WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[Aktivita WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Přijímá data z webové služby. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivitu WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[Aktivita WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Odpoví na požadavek webové služby provedena do pracovního postupu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivita WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[Aktivita typu WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Povolí pracovní postup opakovat až do splnění podmínky. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Použití aktivity aktivita typu WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] o vytváření vlastních aktivit najdete v tématu [vývoj vlastních aktivit](http://go.microsoft.com/fwlink?LinkID=65023) a [pomocí starší verze návrháře aktivit](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zobrazení aktivit (starší verze)](../workflow-designer/activity-views-legacy.md)  
 Popisuje různé návrhové zobrazení aktivit.  
  
 [Postupy: Přidání aktivit do panelu nástrojů (starší verze)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Ukazuje, jak přidat aktivity do panelu nástrojů.  
  
 [Postupy: Vytvoření podmínky deklarativního pravidla (starší verze)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Ukazuje postup vytvoření podmínky deklarativního pravidla.  
  
 [Postupy: Vytvoření sady pravidel aktivit zásad (starší verze)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Ukazuje postup vytvoření sady pravidel aktivit zásad.  
  
 [Postupy: Implementace operace kontraktu technologie WCF (starší verze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Zobrazuje kroky k implementaci [!INCLUDE[indigo2](../includes/indigo2-md.md)] smlouvy operace.  
  
 [Postupy: Vyvolání operace kontraktu technologie WCF (starší verze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Ukazuje postup vyvolání [!INCLUDE[indigo2](../includes/indigo2-md.md)] smlouvy operace.  
  
## <a name="see-also"></a>Viz také  
 [Aktivity Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Vývoj pracovních postupů](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Vývoj aktivit pracovního postupu](http://go.microsoft.com/fwlink?LinkID=65023)