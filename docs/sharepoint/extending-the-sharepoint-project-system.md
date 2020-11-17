---
title: Rozšíření systému projektu služby SharePoint | Microsoft Docs
description: Rozšíří systém projektu služby SharePoint. Naučte se, jak rozšiřuje systém projektu služby SharePoint. Pochopení běžných vývojových úloh.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c017217f66e38eed6248b90efaeabce0efaa9c70
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672545"
---
# <a name="extend-the-sharepoint-project-system"></a>Rozšíří systém projektu služby SharePoint.
  Můžete vytvořit řešení služby SharePoint pomocí sady šablon projektů a šablon položek v sadě Visual Studio. Tyto šablony splňují požadavky mnoha scénářů vývoje, ale můžete zjistit, že některé případy neposkytují funkce, které požadujete. V těchto případech můžete roztáhnout systém projektu služby SharePoint.

## <a name="overview-of-the-sharepoint-project-system"></a>Přehled systému projektu služby SharePoint
 Systém projektu služby SharePoint je založen na základní součásti *položek projektu služby SharePoint*. Položka SharePointového projektu představuje jedno přizpůsobení SharePointu, jako je například definice seznamu, Webová část nebo typ obsahu.

 Projekt služby SharePoint je projekt aplikace Visual Studio, který obsahuje jednu nebo více položek projektu služby SharePoint. Projekty služby SharePoint také obsahují další komponenty, které definují, jak jsou položky projektu seskupeny do funkcí a balíčků pro nasazení.

 Další informace o obsahu položek projektu služby SharePoint a projektech služby SharePoint naleznete v tématu [Create Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>Postup rozšiřování systému projektu služby SharePoint
 Systém projektu služby SharePoint můžete roztáhnout následujícími způsoby:

- Definujte vlastní typy položek projektu služby SharePoint a přidružte je k šablonám nových položek nebo šablonám projektů v aplikaci Visual Studio. Můžete například definovat typ položky projektu SharePoint pro vytvoření vlastní akce nebo pole. Další informace naleznete v tématu [definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Rozšiřuje typy položek projektu služby SharePoint, které jsou již nainstalovány v aplikaci Visual Studio. Můžete například přidat položku místní nabídky do položky projektu v **Průzkumník řešení** a přizpůsobit položku projektu, když vývojář zvolí položku nabídky. Další informace najdete v tématu věnovaném [rozšiřování položek projektu služby SharePoint](../sharepoint/extending-sharepoint-project-items.md).

- Rozšiřuje projekty služby SharePoint. Například můžete přidat obslužné rutiny události k provedení určitých úkolů při přidání nebo odebrání položek z projektů služby SharePoint. Další informace najdete v tématu věnovaném [rozšiřování projektů SharePoint](../sharepoint/extending-sharepoint-projects.md).

- Rozšiřuje chování balení a nasazení položek projektu služby SharePoint a projektů služby SharePoint. Můžete například vytvořit vlastní kroky nasazení, které mají být provedeny při nasazení nebo odvolání projektu, nebo můžete provést další vlastní úkoly, pokud aplikace Visual Studio provede určité kroky nasazení. Další informace najdete v tématu věnovaném [rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Běžné úlohy vývoje
 V rozšíření systému projektu služby SharePoint můžete provádět následující běžné úlohy:

- Uložte vlastní řetězcová data s položkami projektu a v několika různých typech souborů projektu. Další informace naleznete v tématu [uložení dat v rozšíření systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- Převeďte objekt v systému projektu služby SharePoint na odpovídající objekt v modelu automatizačních objektů sady Visual Studio nebo v modelu objektu integrace nebo naopak. Další informace naleznete v tématu [Conver mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

## <a name="see-also"></a>Viz také
- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Rozšiřování položek projektu služby SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Rozšiřování projektů SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Uložení dat v rozšířeních systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Programování konceptů a funkcí pro rozšíření nástrojů SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
