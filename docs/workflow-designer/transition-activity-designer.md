---
title: Návrhář aktivity přechodu Návrhář postupu provádění
description: Přečtěte si, jak můžete pomocí návrháře přechodu aktivity nakonfigurovat přechod mezi dvěma stavy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: cedc9c7b6f402ad3f5f2c40e21c29e2a0d1ad2e6
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433723"
---
# <a name="transition-activity-designer"></a>Návrhář aktivity Transition

<xref:System.Activities.Statements.Transition>Představuje přechod mezi dvěma stavy.

## <a name="using-the-transition-activity-designer"></a>Pomocí návrháře aktivity přechodu

Návrhář aktivity přechodu umožňuje nakonfigurovat přechod mezi dvěma stavy.

### <a name="transition-properties-in-the-workflow-designer"></a>Vlastnosti přechodu v Návrhář postupu provádění

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Transition> vlastnosti, které lze nastavit pomocí návrháře pracovních postupů, a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|Nepravda|Určuje popisný název <xref:System.Activities.Statements.Transition> návrháře aktivit. Výchozí hodnota je **T1**. Hodnotu lze upravit v mřížce vlastností, v záhlaví rozbaleného návrháře přechodu a v hlavičce oddílu Action v rozbaleném návrháři přechodu. <xref:System.Activities.Activity.DisplayName%2A>Používá se v navigaci s popisem cesty, které se zobrazí v horní části návrháře pracovních postupů.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|Nepravda|Je-li k dispozici, určuje výraz, který se musí vyhodnotit na **hodnotu true** před předáním řízení do cílového stavu. Tento stav lze upravit v mřížce vlastností a v rozšířeném návrháři přechodu. V pořadí, ve kterém se zobrazují v Návrháři přechodu, se vyhodnocuje více podmínek sdíleného přechodu. **Poznámka:**  Všimněte si, že pokud je <xref:System.Activities.Statements.Transition.Condition%2A> Přechod z přechodu na **hodnotu false** (nebo všechny podmínky přechodu na sdílený Trigger vyhodnoceny na **hodnotu false** ), přechod nebude proveden a všechny aktivační události pro všechny přechody ze stavu budou přeplánovány. V tomto kurzu nemůžete k této situaci dojít kvůli způsobu konfigurace podmínek (máme konkrétní akce, ať už je odhad správný nebo nesprávný).|
|**Zdroj**|Pravda|Určuje stav, ze kterého pochází tento přechod. Kliknutím na název zdrojového stavu přepnete zobrazení návrháře do rozšířeného zobrazení daného stavu. Tato hodnota je nastavena, když je vytvořen přechod a nelze jej změnit.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|Nepravda|Určuje aktivitu, jejíž dokončení iniciuje přechod. Chcete-li nastavit tuto aktivitu, přetáhněte aktivitu ze **sady nástrojů** a přetáhněte ji do oddílu **triggeru** přechodu.|
|<xref:System.Activities.Statements.Transition.Action%2A>|Nepravda|Určuje aktivitu, která se spustí po dokončení aktivity triggeru a v případě, že je <xref:System.Activities.Statements.Transition.Condition%2A> k dispozici, se vyhodnotí jako **true**. Tato aktivita se spustí při přechodu do cílového stavu, když se <xref:System.Activities.Statements.State.Exit%2A> spustí aktivita pro stav zdroje, pokud je k dispozici. Při rozbalení návrháře přechodu lze tuto hodnotu nastavit přetažením aktivity z **panelu nástrojů** a jejím přesunutím do části **Akce** přechodu. Pro jeden přechod může existovat více akcí. Jednotlivé akce lze rozbalit a uzavřít a lze je seřadit kliknutím na šipku nahoru nebo dolů, která se zobrazí na akci v případě, že je v přechodu provedena více akcí.|
|**Cíl**|Pravda|Označuje stav, po který se stavový stroj přechází po dokončení přechodu. To odpovídá <xref:System.Activities.Statements.Transition.To%2A> Vlastnosti přechodu v objektovém modelu. Kliknutím na název cílového stavu přepnete zobrazení návrháře do rozšířeného zobrazení daného stavu. Tato hodnota je nastavena, když je vytvořen přechod a lze jej změnit přetažením šipky, která propojuje přechod do cílového stavu v návrháři.|

### <a name="creating-transitions"></a>Vytváření přechodů

Přechody jsou vytvářeny přetažením čáry z jednoho stavu do druhého nebo vyřazením stavu na trojúhelníky, které se zobrazí, když je jeden stav přetažen v jiném stavu. Chcete-li vytvořit přechod přetažením ukazatele myši na hranici zdrojového stavu a přetažením čáry ze zdrojového stavu do cílového stavu. Pokud chcete vytvořit přechod, přetáhněte cílový stav a najeďte ho na zdrojový stav a přetáhněte ho na jeden ze čtyř trojúhelníků, které se zobrazí kolem zdrojového stavu. Cílový stav může být buď nový stav přetažený ze **sady nástrojů** , nebo existující stav přetažený z návrháře pracovních postupů.

> [!NOTE]
> Jeden stav stavového počítače může mít až 76 přechodů vytvořených pomocí návrháře pracovních postupů. Omezení přechodů pro stav pracovních postupů vytvořených mimo návrháře je omezeno pouze systémovými prostředky.

Přechody sdílených triggerů jsou sadou přechodů, které sdílejí stejnou aktivační událost. Sdílená aktivační událost umožňuje podmíněný průběh do cílového stavu na základě vyhodnocení výrazů nakonfigurovaných pro několik přechodů, které sdílejí společnou aktivační událost. Chcete-li do přechodu přidat další akce a vytvořit sdílený přechod, klikněte na kroužek, který indikuje začátek požadovaného přechodu a přetáhněte ho do požadovaného stavu. Nový přechod bude sdílet stejný Trigger jako počáteční přechod, ale bude mít jedinečnou podmínku a akci. Sdílené přechody je také možné vytvořit v Návrháři přechodu kliknutím na **přidat přechod sdílené triggery** v dolní části návrháře přechodu a pak výběrem požadovaného cílového stavu z rozevíracího seznamu **dostupné stavy pro připojení** .

## <a name="see-also"></a>Viz také

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Stav](../workflow-designer/state-activity-designer.md)
