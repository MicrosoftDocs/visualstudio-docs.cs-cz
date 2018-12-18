---
title: 'Návrhář postupu provádění - postupy: Přidání komentářů do pracovního postupu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 43b17390f077238a6874784f186eb8add3819f6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883294"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Postupy: Přidání komentářů do pracovního postupu v Návrháři postupu provádění

Pro usnadnění vytváření rozsáhlejších, složitějších pracovních postupů, rozhraní .NET Framework 4.5 umožňuje vývojářům přidat poznámky pro následující typy položek v Návrháři:

-   <xref:System.Activities.Activity>

-   <xref:System.Activities.Statements.State>

-   <xref:System.Activities.Statements.Transition>

-   Třídy odvozené od <xref:System.Activities.Statements.FlowNode>

-   <xref:System.Activities.Variable>

-   <xref:System.Activities.Argument>

> [!IMPORTANT]
> Obsah poznámky jsou uložené jako prostý text do souboru XAML přidružené pracovní postup a může potenciálně číst jiní. Buďte opatrní při vstupu do citlivých informací do poznámky.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Přidání komentáře k aktivitě v Návrháři

1. V Návrháři postupu provádění, klikněte pravým tlačítkem na položku v pracovním postupu návrháře a vyberte **poznámky**, **přidat poznámku**.

1. Přidáte text poznámky v poskytnutém prostoru.

   Položka se zobrazuje ikona poznámky. Najede myší na ikonu poznámky se zobrazí text poznámky.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Zobrazení Poznámka v Návrháři aktivity

1. Návrhář aktivity, který má anotaci zobrazení se mimo aktivitu, klikněte **Pin** ikonu pro úpravy poznámky.

   Poznámka se zobrazí v Návrháři aktivity. Na snímku obrazovky níže zobrazí se v Návrháři aktivity poznámky "Spuštění aktivity v pracovním postupu".

   ![Poznámky se zobrazí v Návrháři aktivit](../workflow-designer/media/annotationindesigner.png)

2. Zobrazit poznámky mimo Návrhář aktivity, při najetí myší nad oblastí poznámky v Návrháři aktivity a klikněte na tlačítko **Odepnout** ikonu

   ![Poznámka zobrazena mimo návrháře aktivity](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Zobrazení nebo skrytí všechny poznámky

1. Klikněte pravým tlačítkem na aktivitu, která má anotaci. Vyberte **poznámky**, **zobrazit všechny poznámky**.

   Všechny poznámky se zobrazí v Návrháři aktivity.

1. Pokud chcete zobrazit všechny poznámky mimo návrháře aktivity, klikněte pravým tlačítkem na aktivitu a vyberte **poznámky**, **skrýt všechny poznámky**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Úpravy nebo odstranění poznámky pro aktivitu

1. Klikněte pravým tlačítkem na aktivitu, která má anotaci.

1. Vyberte **poznámky**, **upravit poznámku** nebo **odstranit poznámku**.

   Poznámka dojde po otevření k úpravám nebo odstranění.

1. Pokud chcete odstranit všechny poznámky najednou, klikněte pravým tlačítkem na pracovního postupu návrháře a vyberte **anotace**, **odstranit všechny poznámky**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Přidání, úpravy nebo odstranění poznámky pro proměnné nebo argumentu.

1. Klikněte pravým tlačítkem na proměnnou nebo argument a vyberte Přidat poznámky.

1. Zadejte text poznámky. Proměnné nebo argumentu zobrazuje ikonu poznámky.

1. Klikněte pravým tlačítkem myši na proměnnou nebo argument, který má anotaci. Vyberte Upravit poznámku.

   Poznámka je otevřen pro úpravy.

1. Klikněte pravým tlačítkem myši na proměnnou nebo argument, který má anotaci. Vyberte možnost odstranit poznámku.

   Poznámka se odstraní.