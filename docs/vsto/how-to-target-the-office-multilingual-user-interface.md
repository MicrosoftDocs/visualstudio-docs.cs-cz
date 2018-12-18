---
title: 'Postupy: cíle vícejazyčné uživatelské rozhraní Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b917479598b73f71a0f3092c874276a700717d6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262030"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Postupy: cíle vícejazyčné uživatelské rozhraní Office
  Multilingual User Interface (MUI) je funkce Microsoft Office, která dává možnost ke změně jazyka uživatelského rozhraní (UI) koncového uživatele. Koncový uživatel práce s anglickou uživatelského rozhraní můžete například změnit jazyk uživatelského rozhraní na španělština.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Pokud vaše aplikace bude používat uživatelé, kteří používají mnoha jazycích systému Office, můžete přidat kód, který automaticky změní jazyk řetězců uživatelského rozhraní s jazykem používá Office na počítači uživatele (Pokud má uživatel správnou prostředky nainstalovaná).  
  
## <a name="to-check-the-current-office-ui-setting"></a>Chcete-li zkontrolovat aktuální nastavení uživatelského rozhraní sady Office  
  
1.  Použití <xref:System.Threading.Thread.CurrentUICulture%2A> vlastnost aktuálního vlákna. Nastavení jazyka řetězců uživatelského rozhraní s jazykem používá verzi systému Office, která aktuálně běží na počítači uživatele.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Office cíl aplikací prostřednictvím primární spolupráce – sestavení](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md)  
  
  