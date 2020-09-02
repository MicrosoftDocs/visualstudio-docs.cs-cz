---
title: 'Postupy: Přidání komentářů k pracovnímu postupu v Návrhář postupu provádění | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d775c79cc7abdf6a66b1174ae625ca468f0764fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663453"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Postupy: Přidání komentářů do pracovního postupu v návrháři postupu provádění
Aby bylo možné vytvořit větší a složitější pracovní postupy, [!INCLUDE[net_v45](../includes/net-v45-md.md)] vývojářům umožňuje přidávat poznámky k následujícím typům položek v Návrháři:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Třídy odvozené z <xref:System.Activities.Statements.FlowNode>

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Obsah poznámky je uložen jako prostý text do souboru XAML přidruženého k pracovnímu postupu a může je potenciálně číst jiné. Buďte opatrní při zadávání citlivých informací do poznámky.

### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Přidání poznámky k aktivitě v Návrháři

1. V Návrháři pracovního postupu klikněte pravým tlačítkem myši na položku v Návrháři pracovních postupů a vyberte **poznámky**, **Přidat poznámku**.

2. Přidá text poznámky v zadaném prostoru.

3. Položka zobrazí ikonu poznámky. Po najetí myší na ikonu poznámky se zobrazí text poznámky.

     ![Aktivita sekvence znázorňující anotaci](../workflow-designer/media/annotation.png "Poznámka")

### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Zobrazení poznámky v Návrháři aktivity

1. V Návrháři aktivity, který má poznámku zobrazenou mimo aktivitu, klikněte na ikonu **připnutí** ve formuláři pro poznámky.

2. Poznámka se zobrazí v Návrháři aktivity. Na následujícím snímku obrazovky se v Návrháři aktivity zobrazí poznámka "spuštění aktivity v pracovním postupu".

     ![Poznámka zobrazená v Návrháři aktivit](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")

3. Chcete-li zobrazit anotaci mimo návrháře aktivity, najeďte myší na oblast poznámky v Návrháři aktivity a klikněte na ikonu **odepnout**

     ![Anotace zobrazená mimo návrh aktivity](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")

### <a name="showing-or-hiding-all-annotations"></a>Zobrazení nebo skrytí všech poznámek

1. Klikněte pravým tlačítkem na aktivitu, která má anotaci. Vyberte **poznámky**, **Zobrazit všechny poznámky**.

2. Všechny poznámky se zobrazí v Návrháři aktivity.

3. Chcete-li zobrazit všechny poznámky mimo návrháře aktivity, klikněte pravým tlačítkem myši na aktivitu a vyberte možnost **poznámky**, **Skrýt všechny poznámky**.

### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Úprava nebo odstranění poznámky pro aktivitu

1. Klikněte pravým tlačítkem na aktivitu, která má anotaci.

2. Vyberte **poznámky**, **upravte poznámku** nebo **odstraňte anotaci**.

3. Poznámka se otevře pro úpravy nebo odstranění.

4. Pokud chcete odstranit všechny poznámky najednou, klikněte pravým tlačítkem myši na návrháře pracovních postupů a vyberte **Anotace**( **Odstranit všechny poznámky**).

### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Přidání, úpravy a odstranění poznámky pro proměnnou nebo argument

1. Klikněte pravým tlačítkem na proměnnou nebo argument a vyberte Přidat poznámku.

2. Zadejte text poznámky. Proměnná nebo argument zobrazí ikonu poznámky.

3. Klikněte pravým tlačítkem myši na proměnnou nebo argument s poznámkou. Vyberte Upravit poznámku.

4. Poznámka se otevře pro úpravy.

5. Klikněte pravým tlačítkem myši na proměnnou nebo argument s poznámkou. Vyberte možnost Odstranit poznámku.

6. Poznámka se odstraní.