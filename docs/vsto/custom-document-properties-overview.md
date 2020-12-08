---
title: Přehled vlastních vlastností dokumentu
description: Přečtěte si, že když sestavíte projekt na úrovni dokumentu, Visual Studio přidá do dokumentu v projektu dvě vlastní vlastnosti.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8c30e0b3253e19316eed24fa26500cd55a3dd515
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847790"
---
# <a name="custom-document-properties-overview"></a>Přehled vlastních vlastností dokumentu

Když sestavíte projekt na úrovni dokumentu, Visual Studio přidá do dokumentu dvě vlastní vlastnosti v projektu: \_ AssemblyLocation a \_ AssemblyName. Když uživatel otevře dokument, systém Microsoft Office aplikace zkontroluje tyto vlastní vlastnosti dokumentu. Pokud v dokumentu existují, aplikace načte [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] a spustí vlastní nastavení. Další informace najdete v tématu [Architektura řešení pro systém Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_Doplňk

Tato vlastnost obsahuje identifikátor CLSID rozhraní v komponentě zavaděče řešení pro systém Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Hodnota CLSID je 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B. Tuto hodnotu byste nikdy neměli měnit.

## <a name="_assemblylocation"></a>\_AssemblyLocation

Tato vlastnost obsahuje řetězec, který poskytuje podrobnosti o manifestu nasazení pro vlastní nastavení. Další informace o manifestech naleznete v tématu [manifesty aplikací a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 \_Hodnota vlastnosti AssemblyLocation může mít různé formáty v závislosti na tom, jak je řešení nasazeno:

- Pokud je řešení publikované pro instalaci z webu, cesty UNC nebo disku CD nebo USB, vlastnost _AssemblyLocation má formát *DeploymentManifestPath* | *SolutionId*. Následující řetězec je příklad:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Pokud používáte nebo ladíte řešení ze sady Visual Studio, vlastnost _AssemblyLocation má formát *DeploymentManifestName* | *SolutionId*| vstolocal. Následující řetězec je příklad:

     ExcelWorkbook1. VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  *SolutionId* je identifikátor GUID, který [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] používá k identifikaci řešení. *SolutionId* se automaticky generuje při sestavování projektu. Termín **vstolocal** označuje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , že sestavení by mělo být načteno ze stejné složky jako dokument.

## <a name="see-also"></a>Viz také

- [Architektura řešení pro systém Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Manifesty aplikací a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Postupy: publikování řešení pro systém Office pomocí technologie ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Postupy: vytváření a úpravy vlastností vlastního dokumentu](../vsto/how-to-create-and-modify-custom-document-properties.md)