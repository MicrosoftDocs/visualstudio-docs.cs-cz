---
title: Manifesty aplikací a nasazení v řešeních pro systém Office
titleSuffix: ''
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc4095ce8cd945ff35903c9d8ffc95400cc3b7ab
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584435"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifesty aplikací a nasazení v řešeních pro systém Office
  Manifest aplikace je soubor XML, který poskytuje informace používané řešením pro systém Office k vyhledání a aktualizaci jeho sestavení. Manifest aplikace lze použít s manifestem nasazení, což je soubor XML uložený na serveru, který poskytuje informace potřebné k vyhledání nejaktuálnější verze manifestu a sestavení aplikace.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Struktura manifestu pro řešení pro systém Office
 Pro systém Microsoft Office řešení vytvořená pomocí vývojářských nástrojů pro Office v sadě Visual Studio jsou všechny manifesty založené na standardním schématu ClickOnce. Když nasadíte řešení pro systém Office, manifesty aplikace pro projekty doplňku na úrovni dokumentu a VSTO jsou umístěny v mezipaměti ClickOnce. Manifesty nasazení nejsou zkopírovány do klientského počítače.

 Informace o obsahu manifestů aplikace a nasazení pro projekty systému Office naleznete v tématu [manifesty aplikace pro řešení systému Office](../vsto/application-manifests-for-office-solutions.md) a [manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Vytvoření manifestů aplikací a nasazení
 Manifesty aplikace jsou vytvořeny automaticky jako součást procesu sestavení. Pokaždé, když sestavíte projekt na úrovni dokumentu, umístění manifestu nasazení je vloženo do dokumentu jako vlastnost vlastního dokumentu. V případě doplňků VSTO je umístění manifestu nasazení Uloženo v registru.

 Další informace o **Průvodci publikováním**naleznete v tématu [nasazení řešení pro systém Office pomocí technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Další informace o tom, jak manifesty fungují s řešeními pro systém Office, najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také

- [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
- [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)