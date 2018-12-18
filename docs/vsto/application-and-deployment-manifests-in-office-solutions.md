---
title: Manifesty aplikace a nasazení v řešeních pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb4386469e02934045d9f1da45fe515dc9af5da2
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53247956"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifesty aplikace a nasazení v řešeních pro systém Office
  Manifest aplikace je soubor XML, který poskytuje informace, které používá řešení pro Office najít a aktualizovat jeho sestavení. Manifest aplikace je možné s manifestem nasazení, což je soubor XML, který je uložený na serveru, který poskytuje informace potřebné k vyhledání aktuální verze manifestu aplikace a sestavení.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="manifest-structure-for-office-solutions"></a>Manifest strukturu pro řešení pro systém Office  
 Řešení Microsoft Office vytvořená pomocí nástroje pro vývoj pro Office v sadě Visual Studio vychází všechny manifesty na standardní schéma ClickOnce. Při nasazení řešení Office jsou umístěny manifesty aplikace pro úrovni dokumentu a projekty doplňku VSTO v mezipaměti ClickOnce. Manifesty nasazení nejsou zkopírovány do klientského počítače.  
  
 Informace o obsahu, aplikace a manifesty nasazení pro projekty Office najdete v tématu [manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md) a [manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
## <a name="create-application-and-deployment-manifests"></a>Vytvoření aplikace a manifestů nasazení  
 Manifesty aplikací jsou vytvořeny automaticky jako součást procesu sestavení. Pokaždé, když vytváříte projekt úrovni dokumentu, umístění manifestu nasazení se vloží do dokumentu jako vlastní vlastnost dokumentu. Pro doplňky VSTO umístění manifestu nasazení je uložen v registru.  
  
 Další informace o **Průvodce publikováním**, naleznete v tématu [nasazení řešení Office s použitím technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Další informace o tom manifesty práce s řešeními sady Office, najdete v části [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Viz také:  
 [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifesty aplikace pro řešení pro systém Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty nasazení pro řešení pro systém Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce – manifest aplikace](/visualstudio/deployment/clickonce-application-manifest)   
 [ClickOnce – manifest nasazení](/visualstudio/deployment/clickonce-deployment-manifest)  
  
  