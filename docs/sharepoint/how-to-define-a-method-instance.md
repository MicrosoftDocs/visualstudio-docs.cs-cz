---
title: 'Postupy: definování Instance metody | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e6dd6c0d7676c6b3c2071f0fcb07e8073313633
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120158"
---
# <a name="how-to-define-a-method-instance"></a>Postupy: definování instance metody
  Je nutné zadat alespoň jednu instanci metoda pro každou metodu v modelu.  
  
 Přidání instance metody pomocí **podrobnosti o metodě BDC** okno. Když přidáte instance metody, přidá aplikace Visual Studio `<MethodInstance>` element XML soubor modelu ve vašem projektu. Další informace o atributy `<MethodInstance>` elementu, najdete v části [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>K definování instance metody  
  
1.  V **podrobnosti o metodě BDC** okno, rozbalte uzel metody a potom rozbalte **instance** uzlu.  
  
2.  V **přidat instanci metoda** vyberte **vytvořit instanci vyhledávací**.  
  
     Nové instance metody se zobrazí pod **instance** uzlu.  
  
3.  Na řádku nabídek zvolte **zobrazení** > **vlastnosti – okno**.  
  
4.  V **vlastnosti** nastavte vlastnosti instance metody. Další informace o jednotlivých vlastnostech najdete v tématu [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>Viz také:
 [Přehled nástrojů pro navrhování modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Postupy: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Postupy: Přidání parametru k metodě](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Postupy: definování deskriptoru typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
