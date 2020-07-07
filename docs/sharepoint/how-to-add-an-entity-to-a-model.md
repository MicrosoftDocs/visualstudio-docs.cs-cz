---
title: 'Postupy: Přidání entity do modelu | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b80f39494b98014a75d4265f228906be2ff45188
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016679"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Postupy: Přidání entity do modelu
  Pokud chcete vytvořit entitu, přidejte ovládací prvek entity z **panelu nástrojů sady** Visual Studio do návrháře služby připojení obchodních dat.

### <a name="to-add-an-entity-to-the-model"></a>Přidání entity do modelu

1. Vytvořte projekt služby BDC nebo otevřete existující projekt služby BDC. Další informace najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).

2. V **sadě nástrojů**ze skupiny **BusinessDataCatalog** přidejte ovládací prvek **entity** do návrháře.

     Nová entita se zobrazí v návrháři. Visual Studio přidá `<Entity>` prvek do XML souboru modelu služby BDC v projektu. Další informace o atributech elementu entity najdete v tématu [entita](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14)).

3. V Návrháři otevřete místní nabídku pro entitu, zvolte možnost **Přidat**a pak zvolte možnost **identifikátor**.

     V entitě se zobrazí nový identifikátor.

    > [!NOTE]
    > Název entity a identifikátor můžete změnit v okně **vlastnosti** .

4. Definujte pole entity ve třídě. Můžete buď přidat novou třídu do projektu, nebo použít existující třídu vytvořenou pomocí jiných nástrojů, jako je například Návrhář relací objektů (Návrhář O/R). Následující příklad ukazuje třídu entity s názvem kontakt.

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>Viz také:
- [Postupy: Přidání metody autora](../sharepoint/how-to-add-a-creator-method.md)
- [Postupy: Přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)
- [Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)
- [Postupy: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)
