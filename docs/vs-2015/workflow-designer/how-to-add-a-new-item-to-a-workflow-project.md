---
title: 'Postupy: Přidání nové položky do projektu pracovního postupu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 004f079576b792fb76d596ee8ebac3f6f96f316e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656635"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Postupy: Přidání nové položky do projektu pracovního postupu
Po vytvoření projektu pracovního postupu můžete přidat aktivity pracovního postupu, návrháře a další známé [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] položky do projektu.

 V následující tabulce jsou uvedeny [!INCLUDE[wf](../includes/wf-md.md)] položky, které můžete přidat do projektu pracovního postupu.

|Name|Popis|
|----------|-----------------|
|Aktivita|Aktivita, která se skládá z jiných činností. Výběrem této položky se do projektu přidá stejný soubor XAML, který byste získali při výběru šablony **knihovny aktivit** pro nový projekt. [!INCLUDE[crabout](../includes/crabout-md.md)] v tomto postupu naleznete v tématu [How to: Create a Library for Activity Library](../workflow-designer/how-to-create-an-activity-library.md).|
|Návrhář aktivit|Návrhář pro přizpůsobení prostředí aktivity v době návrhu. Výběr této položky přidá do projektu stejné soubory, jako byste získali při výběru šablony **knihovny návrháře aktivit** pro nový projekt. [!INCLUDE[crabout](../includes/crabout-md.md)] v tomto postupu naleznete v tématu [How to: Create a Designer Designer Library](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Aktivita kódu|Aktivita s logikou provádění zapsanou v kódu. Soubor zdrojového kódu s přepsáním metody <xref:System.Activities.CodeActivity.Execute%2A> je již pro vás vygenerován.|
|Služba pracovního postupu WCF|Služba [!INCLUDE[indigo2](../includes/indigo2-md.md)] sestavená pomocí aktivit pracovního postupu. Výběr této položky přidá stejné soubory do projektu, jak byste získali při výběru šablony **aplikace služby pracovního postupu WCF** pro nový projekt. [!INCLUDE[crabout](../includes/crabout-md.md)] v tomto postupu naleznete v tématu [How to: Create a Application Workflow Service](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Přidání nové položky do projektu pracovního postupu

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku...** .

     Otevře se dialogové okno **Přidat novou položku** .

2. V podokně **Nainstalované šablony** vyberte možnost Skupina **pracovních postupů** .

3. Vyberte jednu ze čtyř položek. V předchozí tabulce jsou uvedeny dostupné výběry.

4. Do pole **název** v dolní části dialogového okna zadejte vhodný název položky.

5. Kliknutím na tlačítko **Přidat** přidejte položku do projektu aktuálního pracovního postupu.

## <a name="see-also"></a>Viz také
 [Vytvoření projektu pracovního postupu](../workflow-designer/creating-a-workflow-project.md)