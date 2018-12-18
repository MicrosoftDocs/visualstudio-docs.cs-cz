---
title: 'Postupy: Přidání komentářů do pracovního postupu v Návrháři pracovních postupů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: c605ec087a4aa5bec3aecf91d9f0ac1c1a1fb42a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194607"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Postupy: Přidání komentářů do pracovního postupu v Návrháři postupu provádění
Pro usnadnění vytváření rozsáhlejších, složitějších pracovních postupů, [!INCLUDE[net_v45](../includes/net-v45-md.md)] umožňuje vývojářům přidat poznámky pro následující typy položek v Návrháři:  
  
-   <xref:System.Activities.Activity>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
-   Třídy odvozené od <xref:System.Activities.Statements.FlowNode>  
  
-   <xref:System.Activities.Variable>  
  
-   <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
>  Obsah poznámky jsou uložené jako prostý text do souboru XAML přidružené pracovní postup a může potenciálně číst jiní. Buďte opatrní při vstupu do citlivých informací do poznámky.  
  
### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Přidání komentáře k aktivitě v Návrháři  
  
1.  V Návrháři postupu provádění, klikněte pravým tlačítkem na položku v pracovním postupu návrháře a vyberte **poznámky**, **přidat poznámku**.  
  
2.  Přidáte text poznámky v poskytnutém prostoru.  
  
3.  Položka se zobrazí ikona poznámky. Ukazatel myši na ikonu poznámky se zobrazí text poznámky.  
  
     ![Pořadí aktivit znázorňující anotace](../workflow-designer/media/annotation.png "poznámky")  
  
### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Zobrazení Poznámka v Návrháři aktivity  
  
1.  Návrhář aktivity, který má anotaci zobrazení se mimo aktivitu, klikněte **Pin** ikonu pro úpravy poznámky.  
  
2.  Poznámka se zobrazí v Návrháři aktivity. Na snímku obrazovky níže zobrazí se v Návrháři aktivity poznámky "Spuštění aktivity v pracovním postupu".  
  
     ![Poznámky se zobrazí v Návrháři aktivit](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3.  Zobrazit poznámky mimo Návrhář aktivity, při najetí myší nad oblastí poznámky v Návrháři aktivity a klikněte na tlačítko **Odepnout** ikonu  
  
     ![Poznámka zobrazena mimo aktivity designe](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### <a name="showing-or-hiding-all-annotations"></a>Zobrazení nebo skrytí všechny poznámky  
  
1.  Klikněte pravým tlačítkem na aktivitu, která má anotaci. Vyberte **poznámky**, **zobrazit všechny poznámky**.  
  
2.  Všechny poznámky se zobrazí v Návrháři aktivity.  
  
3.  Pokud chcete zobrazit všechny poznámky mimo návrháře aktivity, klikněte pravým tlačítkem na aktivitu a vyberte **poznámky**, **skrýt všechny poznámky**.  
  
### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Úpravy nebo odstranění poznámky pro aktivitu  
  
1.  Klikněte pravým tlačítkem na aktivitu, která má anotaci.  
  
2.  Vyberte **poznámky**, **upravit poznámku** nebo **odstranit poznámku**.  
  
3.  Poznámka se po otevření k úpravám nebo odstraněn.  
  
4.  Pokud chcete odstranit všechny poznámky najednou, klikněte pravým tlačítkem na pracovního postupu návrháře a vyberte **anotace**, **odstranit všechny poznámky**.  
  
### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Přidání, úpravy nebo odstranění poznámky pro proměnné nebo argumentu.  
  
1.  Klikněte pravým tlačítkem na proměnnou nebo argument a vyberte Přidat poznámky.  
  
2.  Zadejte text poznámky. Ikona poznámky se zobrazí proměnné nebo argumentu.  
  
3.  Klikněte pravým tlačítkem myši na proměnnou nebo argument, který má anotaci. Vyberte Upravit poznámku.  
  
4.  Poznámka se otevře pro úpravy.  
  
5.  Klikněte pravým tlačítkem myši na proměnnou nebo argument, který má anotaci. Vyberte možnost odstranit poznámku.  
  
6.  Poznámka se odstraní.