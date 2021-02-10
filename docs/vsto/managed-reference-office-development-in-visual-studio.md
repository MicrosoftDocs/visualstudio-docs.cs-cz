---
title: Spravované referenční materiály (vývoj pro Office v sadě Visual Studio)
description: Přečtěte si o referenční dokumentaci k rozhraní API pro obory názvů a typy, které se používají v projektech Office, které cílí na .NET Framework.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9364b191886408e509aa09a83bde70ce8240707e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958749"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Spravované referenční materiály (vývoj pro Office v sadě Visual Studio)
  Tato část obsahuje referenční dokumentaci rozhraní API pro obory názvů a typy, které se používají v projektech Office, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](includes/net-v45-md.md)] . Referenční dokumentace k rozhraní API pro obory názvů a typy, které se používají v projektech Office, které cílí na .NET Framework 3,5, najdete v následující referenční části v dokumentaci k sadě Visual Studio: [spravované referenční materiály (vývoj pro Office v sadě Visual Studio)](managed-reference-office-development-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>V této části
 <xref:Microsoft.Office.Tools>

 Obsahuje třídy společné pro programování řešení pro systém Office. Patří mezi ně základní třída pro doplňky VSTO, třídy pro vytváření vlastních podoken úloh v doplňcích VSTO, třídy pro vytváření inteligentních značek v aplikacích Excel a Word a třídy pro vytváření podoken akcí v přizpůsobeních na úrovni dokumentu.

 <xref:Microsoft.Office.Tools.Excel>

 Obsahuje ovládací prvky hostitele a hostitelské položky, které lze použít v řešeních pro aplikaci Excel.

 <xref:Microsoft.Office.Tools.Excel.Controls>

 Obsahuje ovládací prvky aplikace Excel a model Windows Forms ovládací prvky, které lze použít v řešeních pro aplikaci Excel.

 <xref:Microsoft.Office.Tools.Outlook>

 Obsahuje třídy, které jsou používány doplňky VSTO pro Outlook, včetně tříd, které se používají k vytváření vlastních oblastí formuláře.

 <xref:Microsoft.Office.Tools.Ribbon>

 Obsahuje třídy, které slouží k programové úpravě přizpůsobení pásu karet vytvořeného pomocí Návrháře pásu karet.

 <xref:Microsoft.Office.Tools.Word>

 Obsahuje ovládací prvky hostitele a hostitelské položky, které lze použít v řešeních pro aplikaci Word.

 <xref:Microsoft.Office.Tools.Word.Controls>

 Obsahuje ovládací prvky aplikace Word a model Windows Forms ovládací prvky, které lze použít v řešeních pro aplikaci Word.

 <xref:Microsoft.VisualStudio.Tools.Applications>

 Obsahuje <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídu a sadu souvisejících datových tříd uložených v mezipaměti. Tyto třídy lze použít k úpravě některých aspektů přizpůsobení na úrovni dokumentu na počítačích, které nemají nainstalované systém Microsoft Office.

 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>

 Obsahuje <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> rozhraní (které můžete implementovat pro vytvoření *akce po nasazení* pro řešení Office), výjimky, které mohou být vyvolány při instalaci řešení Office a dalších rozhraní API, která jsou součástí infrastruktury sady Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>

 Obsahuje většinu výjimek, které mohou být vyvolány [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] , několik tříd, které lze použít k ukládání dat do mezipaměti v přizpůsobení na úrovni dokumentu a dalších rozhraní API, která jsou součástí infrastruktury sady Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>

 Obsahuje třídy úloh nástroje MSBuild, které slouží k sestavování projektů Office.

## <a name="see-also"></a>Viz také
- [Přehled nástrojů Visual Studio Tools for Office runtime](visual-studio-tools-for-office-runtime-overview.md)
- [Začněte &#40;vývoj pro Office v sadě Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)
- [Ukázky a návody pro vývoj pro Office](office-development-samples-and-walkthroughs.md)
- [Návrh a tvorba řešení pro systém Office](designing-and-creating-office-solutions.md)
