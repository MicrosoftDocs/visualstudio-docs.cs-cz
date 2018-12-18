---
title: 'Postupy: Přidání parametru k metodě | Microsoft Docs'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 196ac37cc9bc4f53cfa886b92c62c7a301c3451a
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756308"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Postupy: Přidání parametru k metodě
  Použijte parametr k předání informací do metodu nebo k vrácení informací z metody. Všechny metody musí mít minimálně jeden parametr. Další informace o tom, jak navrhnout parametr pro podporu typ metody, které chcete vytvořit, naleznete v části [navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Když přidáte parametr na metodu, Visual Studio přidá prvek parametru do XML soubor modelu ve vašem projektu. Další informace o atributech element parametru najdete v tématu [parametr](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Přidání parametru do metody  
  
1.  Přidání metody na entitu.  
  
2.  Na řádku nabídek zvolte **zobrazení** > **ostatní okna** > **podrobnosti o metodě BDC**.  
  
     **Podrobnosti o metodě BDC** otevře se okno. Další informace najdete v tématu [přehled nástrojů pro navrhování modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  V **podrobnosti o metodě BDC** okno, rozbalte uzel metody a potom rozbalte **parametry** uzlu.  
  
4.  V **přidat parametr** vyberte **vytvořit parametr**.  
  
     Nový parametr se zobrazí pod **parametry** uzlu.  
  
5.  Na řádku nabídek zvolte **zobrazení** > **vlastnosti – okno**.  
  
6.  V **vlastnosti** nastavte **název** vlastnost na libovolný název, který vám vyhovuje. Například pokud metoda vrátí zákazníků, můžete třeba pojmenovat metodu **GetCustomers**.  
  
7.  V **podrobnosti o metodě BDC** oken, otevřete seznam, který se zobrazí ve směru parametru a potom zvolte **v**, **InOut**, **Out**, nebo **vrátit**.  
  
     Další informace o směru zvolit typ metody, kterou vytváříte, najdete v části [návrhu modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Upravte popisovač typu parametru. Další informace najdete v tématu [postupy: definování deskriptoru typu pro parametr](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Viz také:
 [Přehled nástrojů pro navrhování modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Postupy: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Postupy: definování deskriptoru typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)   
 [Navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
