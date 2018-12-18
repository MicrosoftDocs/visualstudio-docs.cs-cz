---
title: Rozšíření systému projektu služby SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 028e7aab10ae1ee1de452e69c8148dac099039d0
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326784"
---
# <a name="extend-the-sharepoint-project-system"></a>Rozšíření systému projektu služby SharePoint
  Řešení služby SharePoint můžete vytvořit pomocí sadu šablony projektů a šablon položek v sadě Visual Studio. Tyto šablony požadavkům mnoho vývojové scénáře, ale může v některých případech, kde není poskytují funkce, které budete potřebovat zjistíte. V těchto případech můžete rozšíření systému projektu služby SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Přehled systému projektu služby SharePoint
 Systém projektu služby SharePoint je založen na základní součásti *SharePoint – položky projektu*. Položky projektu služby SharePoint představuje jediné přizpůsobení SharePoint, například definice seznamu, webové části nebo typ obsahu.  
  
 Projektu služby SharePoint je projekt sady Visual Studio, která zahrnuje jednu nebo více položek projektu služby SharePoint. Projekty SharePoint obsahovat také další součásti, které definují způsob seskupení položek projektu do funkce a balíčky pro nasazení.  
  
 Další informace o obsahu SharePoint – položky projektu a projektů služby SharePoint, naleznete v části [položky vytvářet šablony a šablony projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Postup rozšíření systému projektu služby SharePoint
 Systému projektu služby SharePoint můžete rozšířit následujícími způsoby:  
  
-   Definování vlastních typů položek projektu služby SharePoint a přidružit je k nové položky šablony nebo šablony projektů v sadě Visual Studio. Můžete například definovat typu položky projektu služby SharePoint pro vytvoření vlastní akce ani pole. Další informace najdete v tématu [definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Rozšíření typů položek projektu služby SharePoint, které již jsou nainstalovány v sadě Visual Studio. Například můžete přidat položky místní nabídky do položky projektu v **Průzkumníku řešení** a přizpůsobit položku projekt, když vývojář vybere položku nabídky. Další informace najdete v tématu [rozšířit SharePoint – položky projektu](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Rozšíření projektů služby SharePoint. Například můžete přidat obslužné rutiny událostí k provádění specifických úloh, když položky jsou přidány nebo odebrány z projektů služby SharePoint. Další informace najdete v tématu [projekty SharePoint rozšířit](../sharepoint/extending-sharepoint-projects.md).  
  
-   Rozšíření balení a nasazení chování položky projektu služby SharePoint a projektů služby SharePoint. Například můžete vytvořit vlastní postup nasazení provést při nasazení nebo odvolávání projektu, nebo když Visual Studio provede určité kroky nasazení můžete provádět další vlastní úlohy. Další informace najdete v tématu [balení a nasazení SharePoint rozšířit](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Běžné úlohy vývoj
 Můžete provádět následující běžné úlohy v rozšíření systému projektu služby SharePoint:  
  
-   Uložení dat vlastní řetězec s položky projektu a v několika různých typů souborů projektu. Další informace najdete v tématu [uložení dat v rozšíření systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Převést objekt v systému projektu služby SharePoint na odpovídající objekt v sadě Visual Studio automatizace objektový model nebo integrace objektový model, nebo naopak. Další informace najdete v tématu [převést mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Viz také:
 [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Rozšíření položek projektu služby SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Rozšíření projektů služby SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Rozšíření balení a nasazení SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Uložení dat v rozšíření systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programování konceptů a funkcí pro rozšíření nástrojů SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  
