---
title: Návrhář postupu provádění starší verze stavu počítače | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 30eaf026d0558538c51b4cbda313e051348a5120
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49231683"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Používání starší verze návrháře postupu provádění stavového stroje
Při vytváření nového projektu pracovního postupu stavu počítače v [!INCLUDE[vs2010](../includes/vs2010-md.md)] , zaměřuje na buď [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], můžete použít buď **Konzolová aplikace pracovního postupu stavu počítače** nebo  **Stav počítače pracovního postupu knihovny** šablony starší verzi projektu. Pokud zvolíte některou z těchto šablon projektů stavu počítače, zobrazí se jako starší verzi pracovního postupu návrháře uživatelské rozhraní návrháře stav počítače. Informace o šablonách projektů starší verze stavu počítače najdete v tématu [postupy: vytvoření stavu počítače konzolových aplikací pracovních postupů (starší verze)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) a [postupy: vytvoření knihovny stavu počítače pracovního postupu (starší verze)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).  
  
 Pracovní postup stavového stroje se skládá ze sady stavy. Jeden stav je označena jako počáteční stav. Každý stav můžou získat sadu událostí. Na základě události, lze se přechod do jiného stavu. Pracovní postup stavového stroje může mít koncový stav. Při přechodu do konečného stavu, dokončení pracovního postupu.  
  
## <a name="state-machine-designer-views"></a>Návrhář zobrazení stavového stroje  
 Návrhář stavu počítače je volný tvar popisovačů návrháře, což znamená, že aktivity můžete přesunout volně na návrhové ploše. Návrhář stavu počítače má dvě zobrazení: *stavu* zobrazení a *založený na událostech* zobrazení.  
  
 Zobrazení stavu zobrazuje stav aktivity a aktivity založené na událostech, které mohou být obsaženy v rámci stavu aktivity. V tomto zobrazení přechodů z jednoho stavu do druhého jsou reprezentovány řádky, které rozšiřují z aktivity založené na událostech v jednoho stavu do jiného stavu. Přechody také vytvoříte nakreslení čáry. Chcete-li nakreslit přechodu, vyberte aktivity založené na událostech a vyberte jeden z manipulačních aktivity a přetáhněte ho. Tato akce nakreslí čáru. Tento řádek přiřazen cílový stav označující přechod mezi stavy.  
  
 Pro přístup k EventDriven zobrazení, klikněte dvakrát na aktivitu založený na událostech. Který se zobrazí Návrhář je podobné jako u sekvenčního pracovního postupu návrháře. V horní části návrháře zobrazí navigační panel hierarchii aktivit do aktivity založené na událostech, který se zobrazí. Kliknutím na libovolný prvek v hierarchii zobrazené můžete přejít zpět na zobrazení stavu. Pokud byl nakreslen přechod z jednoho stavu do druhého v zobrazení stavu, a pokud zobrazujete EventDriven zobrazení této aktivity, stavu aktivity jako sadu je přidána do aktivity založené na událostech pro vás. Pokud změníte vlastnosti nastavení stavu aktivity, se projeví v zobrazení stavu.  
  
## <a name="state-machine-workflow-activities"></a>Aktivity pracovního postupu stavového stroje  
 Následující tabulka popisuje klíčové aktivity, které se používají v Návrháři postupu provádění stavu počítače.  
  
|Název panelu nástrojů|Aktivita|Popis|  
|------------------|--------------|-----------------|  
|**Stav**|[Umístit aktivitu StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Představuje stav stavového stroje může obsahovat další **umístit aktivitu StateActivity** aktivity. Další informace najdete v tématu [pomocí aktivity umístit aktivitu StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Určuje přechod na nový stav. Další informace najdete v tématu [pomocí aktivity SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|**Aktivitu typu StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Provede, když se zadá do stavu; může obsahovat jiné aktivity. Další informace najdete v tématu [pomocí aktivity aktivitu typu StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**Aktivitu typu StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Provede obsažené aktivity při opuštění [umístit aktivitu StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) aktivity. Další informace najdete v tématu [pomocí aktivity StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Používá se pro stavy, které využívají externí události, která spustí provádění. **EventDrivenActivity** aktivita musí mít aktivitu, která implementuje [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) rozhraní jako první podřízená aktivita. Další informace najdete v tématu [pomocí aktivitu EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
  
 Je hlavní součást pracovní postup stavového stroje [umístit aktivitu StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) aktivity. Jak se události mají zachytávat v různých fázích pracovní postup stavového stroje, různých stavů jsou zadány pro zpracování úloh, které jsou spojeny s událostmi. Pracovní postup může po celou dobu životnosti pracovního postupu, nechte a zadejte několik různých stavů. Tyto stavy připojit k sobě navzájem pomocí [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) aktivity.  
  
 Při přetažení nový **umístit aktivitu StateActivity** na návrhovou plochu pracovního postupu můžete přidat [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [ StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), nebo další **umístit aktivitu StateActivity** aktivitám v podobě podřízené aktivity.  
  
> [!CAUTION]
>  Při vytváření pracovních postupů pomocí návrháře postupu provádění stavu počítače, je třeba sledovat struktura pracovního postupu při návrhu se **Osnova dokumentu** zobrazení okna. Zobrazení struktury pracovní postup stavového stroje v **Osnova dokumentu** zobrazení okna zrcadlí logické rozložení aktivit v souboru označení pracovního postupu. Fyzické rozložení aktivit pracovního postupu, jak se objeví na návrhové ploše nemusí zrcadlí logické rozložení aktivit v souboru označení pracovního postupu.  
>   
>  Chcete-li otevřít **Osnova dokumentu** okno na **zobrazení** nabídky, přejděte **ostatní Windows**a pak vyberte **Osnova dokumentu**.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření konzolových aplikací pracovních postupů stavového stroje (starší verze)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)   
 [Postupy: vytvoření knihovny pracovních postupů stavového stroje (starší verze)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)   
 [Pracovní postupy stavového stroje](http://go.microsoft.com/fwlink?LinkID=65016)   
 [Použití aktivity umístit aktivitu StateActivity](http://go.microsoft.com/fwlink?LinkID=65083)   
 [Použití aktivity StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006)   
 [Použití aktivity StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008)   
 [Použití aktivity SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082)   
 [Použití aktivity EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)