---
title: 'Návrhář postupu provádění-postupy: Přidání komentářů do pracovního postupu'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 77fb43671a45d5d53d2fe23fa3e4e7a9a98c4373
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815497"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Postupy: Přidání komentářů do pracovního postupu v návrháři postupu provádění

Aby bylo možné vytvářet větší a složitější pracovní postupy, .NET Framework 4,5 umožňuje vývojářům přidávat poznámky k následujícím typům položek v Návrháři:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Třídy odvozené z<xref:System.Activities.Statements.FlowNode>

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Obsah poznámky je uložen jako prostý text do souboru XAML přidruženého k pracovnímu postupu a může je potenciálně číst jiné. Buďte opatrní při zadávání citlivých informací do poznámky.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Přidání poznámky k aktivitě v Návrháři

1. V Návrháři pracovního postupu klikněte pravým tlačítkem myši na položku v Návrháři pracovních postupů a vyberte **poznámky**, **Přidat poznámku**.

1. Přidá text poznámky v zadaném prostoru.

   Položka zobrazuje ikonu poznámky. Po najetí myší na ikonu poznámky se zobrazí text poznámky.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Zobrazení poznámky v Návrháři aktivity

1. V Návrháři aktivity, který má poznámku zobrazenou mimo aktivitu, klikněte na ikonu **připnutí** ve formuláři pro poznámky.

   Poznámka se zobrazí v Návrháři aktivity. Na následujícím snímku obrazovky se v Návrháři aktivity zobrazí poznámka "spuštění aktivity v pracovním postupu".

   ![Poznámka zobrazená v Návrháři aktivit](../workflow-designer/media/annotationindesigner.png)

2. Chcete-li zobrazit anotaci mimo návrháře aktivity, najeďte myší na oblast poznámky v Návrháři aktivity a klikněte na ikonu **odepnout**

   ![Anotace zobrazená mimo návrháře aktivity](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Zobrazení nebo skrytí všech poznámek

1. Klikněte pravým tlačítkem na aktivitu, která má anotaci. Vyberte **poznámky**, **Zobrazit všechny poznámky**.

   Všechny poznámky se zobrazí v Návrháři aktivity.

1. Chcete-li zobrazit všechny poznámky mimo návrháře aktivity, klikněte pravým tlačítkem myši na aktivitu a vyberte možnost **poznámky**, **Skrýt všechny poznámky**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Úprava nebo odstranění poznámky pro aktivitu

1. Klikněte pravým tlačítkem na aktivitu, která má anotaci.

1. Vyberte **poznámky**, **upravte poznámku** nebo **odstraňte anotaci**.

   Poznámka se otevře pro úpravy nebo odstranění.

1. Pokud chcete odstranit všechny poznámky najednou, klikněte pravým tlačítkem myši na návrháře pracovních postupů a vyberte **Anotace**( **Odstranit všechny poznámky**).

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Přidání, úpravy a odstranění poznámky pro proměnnou nebo argument

1. Klikněte pravým tlačítkem na proměnnou nebo argument a vyberte Přidat poznámku.

1. Zadejte text poznámky. Proměnná nebo argument zobrazuje ikonu poznámky.

1. Klikněte pravým tlačítkem myši na proměnnou nebo argument s poznámkou. Vyberte Upravit poznámku.

   Poznámka se otevře pro úpravy.

1. Klikněte pravým tlačítkem myši na proměnnou nebo argument s poznámkou. Vyberte možnost Odstranit poznámku.

   Poznámka se odstraní.
