---
title: Použití starší verze stavového počítače Návrhář postupu provádění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bab07b8ba0b71bd880135518ff9ff5fc697d54c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302809"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Používání starší verze návrháře postupu provádění stavového stroje
Když vytváříte nový projekt pracovního postupu stavového stroje v [!INCLUDE[vs2010](../includes/vs2010-md.md)], který cílí na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], můžete použít buď **konzolovou aplikaci stavového pracovního postupu** , nebo šablonu projektu **stavová knihovna pracovního postupu stavového stroje** . Zvolíte-li jednu z těchto šablon projektu stavového počítače, zobrazí se Návrhář stavového počítače jako starší uživatelské rozhraní návrháře pracovních postupů. Informace o šablonách projektu se starší verzí stavů najdete v tématu [How to: Create a Application Workflow State Applications Console (starší verze)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) a [How to: Create a State Machine Workflows Library (starší verze)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Pracovní postup stavového stroje se skládá ze sady stavů. Jeden stav je označený jako počáteční stav. Každý stav může přijmout určitou sadu událostí. V závislosti na události lze přechod provést do jiného stavu. Pracovní postup stavového počítače může mít konečný stav. Při přechodu do konečného stavu se pracovní postup dokončí.

## <a name="state-machine-designer-views"></a>Zobrazení návrháře stavového stroje
 Návrhář stavového stroje je volný tvar, což znamená, že aktivity lze na návrhové ploše volně pohybovat. Návrhář stavového počítače má dvě zobrazení: zobrazení *stavu* a zobrazení založené *na událostech* .

 Zobrazení stavu ukazuje aktivity stavu a aktivity řízené událostmi, které mohou být obsaženy v rámci aktivity stavu. V tomto zobrazení jsou přechody z jednoho stavu do druhého zastoupeny řádky, které se rozšířily od aktivity řízené událostmi v jednom stavu do jiného stavu. Přechody můžete vytvořit také tak, že čáru nakreslíte sami. Chcete-li nakreslit přechod, vyberte aktivitu založenou na událostech a potom vyberte jeden z popisovačů aktivity a přetáhněte jej. Tato akce nakreslí čáru. Tento řádek je pak připojen k cílovému stavu, který označuje přechod mezi stavy.

 Chcete-li získat přístup k zobrazení řízenému událostmi, poklikejte na aktivitu založenou na událostech. Návrhář, který se zobrazí, je podobný návrháři sekvenčního pracovního postupu. V horní části návrháře zobrazuje navigační panel hierarchii aktivit až po zobrazenou aktivitu řízenou událostmi. Zpět na zobrazení stavu můžete přejít kliknutím na libovolný prvek v zobrazené hierarchii. Pokud jste nakreslili přechod z jednoho stavu do druhého v zobrazení stav a pokud zobrazujete zobrazení řízené událostmi této aktivity, do aktivity řízené událostmi se přidá aktivita nastavená stavová aktivita. Pokud změníte vlastnosti aktivity nastavit stav, projeví se zpátky v zobrazení stav.

## <a name="state-machine-workflow-activities"></a>Aktivity pracovního postupu stavového stroje
 Následující tabulka popisuje klíčové aktivity, které se používají v Návrháři pracovních postupů stavového stroje.

|Název sady nástrojů|Aktivita|Popis|
|------------------|--------------|-----------------|
|**State**|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Představuje stav stavového stroje; může obsahovat další aktivity **StateActivity** . Další informace najdete v tématu [použití aktivity StateActivity](https://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Určuje přechod do nového stavu. Další informace najdete v tématu [použití aktivity SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Provede se při zadání stavu. může obsahovat další aktivity. Další informace najdete v tématu [použití aktivity StateInitialization](https://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Provede obsažené aktivity, když opustí aktivitu [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) . Další informace najdete v tématu [použití aktivity StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Používá se pro stavy, které jsou závislé na externí události pro spuštění provádění. Aktivita **EventDrivenActivity** musí mít aktivitu, která implementuje rozhraní [IEventActivity](https://go.microsoft.com/fwlink?LinkID=65032) jako první podřízenou aktivitu. Další informace najdete v tématu [použití aktivity EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65068).|

 Hlavní komponentou pracovního postupu stavového stroje je aktivita [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) . Když jsou události zachyceny v různých fázích pracovního postupu stavového stroje, jsou pro zpracování úkolů přidružených k událostem zadány různé stavy. Během životnosti pracovního postupu může pracovní postup opustit a zadat několik různých stavů. Tyto stavy se vzájemně připojují pomocí aktivity [SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041) .

 Když přetáhnete novou **StateActivity** na návrhovou plochu pracovního postupu, můžete přidat [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)nebo další aktivity **StateActivity** jako podřízené aktivity.

> [!CAUTION]
> Když k vytváření pracovních postupů použijete návrháře pracovního postupu stavového stroje, musíte monitorovat strukturu pracovního postupu, který navrhujete, pomocí okna zobrazení **Osnova dokumentu** . Zobrazení struktury pracovního postupu stavového stroje v okně zobrazení **Osnova dokumentu** zrcadlí logické rozložení aktivit v souboru označení pracovního postupu. Fyzické rozložení aktivit pracovního postupu, jak se zobrazuje na návrhové ploše, nemusí zrcadlit logické rozložení aktivit v souboru značek pracovního postupu.
>
> Chcete-li otevřít okno **Osnova dokumentu** , v nabídce **zobrazení** přejděte na položku **ostatní okna**a vyberte položku **Osnova dokumentu**.

## <a name="see-also"></a>Viz také
 [Postupy: vytváření konzolových aplikací pracovního postupu stavového stroje (starší verze)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) postupy: vytvoření pracovních postupů stavového stroje [(starší verze)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [pracovní postup stavového stroje](https://go.microsoft.com/fwlink?LinkID=65016) [pomocí aktivity StateActivity](https://go.microsoft.com/fwlink?LinkID=65083) pomocí aktivity [StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65006) [pomocí aktivity](https://go.microsoft.com/fwlink?LinkID=65008) [SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65082) [pomocí aktivity EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65068)