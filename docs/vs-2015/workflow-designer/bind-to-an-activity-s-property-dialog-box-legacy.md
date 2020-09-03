---
title: Vytvořit propojení s vlastností aktivity&#39;s (starší verze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f88d7ebe714fcdc9bf404e1cf58c4c86cf37047d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851471"
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Dialogové okno vazba na vlastnost&#39;s aktivitou (starší verze)
Toto téma popisuje, jak používat dialogové okno **vytvořit vazby do vlastnosti aktivity** ve starší verzi [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Použijte starší verze, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Pokud potřebujete cílit buď na, [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Typ instance vlastnosti závislosti může být vázán na veřejnou vlastnost nebo událost jiné aktivity. Další informace o vytváření vazeb aktivit najdete v tématu [použití vlastností závislosti](https://msdn2.microsoft.com/library/bb675255.aspx).

 Vyberte vlastnost, pro kterou chcete vytvořit vazby, pomocí dialogového okna **vazba na vlastnost této aktivity** . Toto dialogové okno otevřete kliknutím na tři tečky **[...]** na konci textového pole vybrané vlastnosti v okně **vlastnosti** , nebo kliknutím na ikonu modrého vykřičníku, která se zobrazí vedle názvu vlastnosti v prohlížeči vlastností.

 Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **vazba k vlastnosti aktivity** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Vytvořit propojení s existujícím členem**|V podokně stromového zobrazení vyberte člena, se kterým chcete vytvořit propojení. V podokně stromového zobrazení se zobrazí zpráva, která označuje, zda je člen platný typ pro vytvoření vazby nebo nikoli. Kliknutím na tlačítko **OK** se naváže na vybraného platného člena.|
|**Vytvořit propojení s novým členem**|Vytvořte nové pole člena nebo vlastnost, ke které se má vytvořit vazba. Zadejte **nový název člena**. Zvolte, zda chcete vytvořit vlastnost závislosti nebo veřejné pole, a vyberte možnost **vytvořit pole** nebo **vytvořit vlastnost**. Kliknutím na tlačítko **OK** vytvořte nového člena.|

## <a name="see-also"></a>Viz také
 [Použití vlastností aktivity](https://msdn2.microsoft.com/library/bb628510.aspx) [pomocí vlastnosti závislostí](https://msdn2.microsoft.com/library/bb675255.aspx) [starší verze návrháře pro programovací model Windows Workflow Foundation nápovědu k uživatelskému rozhraní](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)
