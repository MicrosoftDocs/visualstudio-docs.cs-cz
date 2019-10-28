---
title: 'Postupy: definování instance metody | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e21900e87278ad500ee8497d1dd0c49350695d1
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981798"
---
# <a name="how-to-define-a-method-instance"></a>Postupy: definování instance metody
  Pro každou metodu v modelu je nutné definovat alespoň jednu instanci metody.

 Přidejte instanci metody pomocí okna **Podrobnosti metody služby BDC** . Když přidáte instanci metody, Visual Studio přidá prvek `<MethodInstance>` do XML souboru modelu v projektu. Další informace o atributech `<MethodInstance>` elementu naleznete v tématu [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

### <a name="to-define-a-method-instance"></a>Definování instance metody

1. V okně **Podrobnosti metody služby BDC** rozbalte uzel metody a potom rozbalte uzel **instance** .

2. V seznamu **přidat instanci metody** vyberte možnost **vytvořit instanci hledání**.

     Pod uzlem **instance** se zobrazí nová instance metody.

3. Na panelu nabídek vyberte možnost **zobrazit** > **okno Vlastnosti**.

4. V okně **vlastnosti** nastavte vlastnosti instance metody. Další informace o jednotlivých vlastnostech naleznete v tématu [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

## <a name="see-also"></a>Viz také:
- [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Postupy: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Postupy: definování deskriptoru typu pro parametr](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
