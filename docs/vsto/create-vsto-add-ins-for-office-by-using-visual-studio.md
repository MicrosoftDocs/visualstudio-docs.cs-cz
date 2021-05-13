---
title: Vytváření doplňků VSTO pro Office s použitím sady Visual Studio
description: Přečtěte si, jak můžete pomocí nástrojů systém Microsoft Office Developer Tools v sadě Visual Studio vytvářet .NET Framework aplikace, které rozšíří Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 990caeec642a745bec5b6e0f2d29ff5d6213d095
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848315"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Vytváření doplňků VSTO pro Office s použitím sady Visual Studio
> [!IMPORTANT]
> VSTO spoléhá na [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). Doplňky modelu COM lze také zapsat pomocí .NET Framework. Doplňky Office se nedají vytvářet pomocí [.NET Core a .NET 5 +](https://docs.microsoft.com/dotnet/core/dotnet-five), nejnovější verze .NET. Důvodem je to, že .NET Core/. NET 5 + nemůže spolupracovat s .NET Framework ve stejném procesu a může vést k chybám načtení doplňku. Můžete dál používat .NET Framework k psaní VSTO a doplňků modelu COM pro Office. Microsoft nebude aktualizovat VSTO nebo platformu doplňku COM pro použití .NET Core nebo .NET 5 +. Můžete využít výhod .NET Core a .NET 5 +, včetně ASP.NET Core, k vytvoření serverové aplikace pro [webové Doplňky Office](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins).

  Pomocí nástrojů systém Microsoft Office Developer Tools v sadě Visual Studio můžete vytvářet .NET Framework aplikace, které rozšíří Office. Tyto aplikace se také nazývají *řešení pro systém Office*.

 Nástroje Office Developer Tools poskytují funkce, které vám pomůžou vytvářet řešení pro systém Office tak, aby vyhovovala různým obchodním potřebám. Nástroje obsahují šablony projektu, které vám pomohou vytvořit řešení pro systém Office pomocí Visual Basic nebo Visual C# a vizuálních návrhářů, které vám pomohou vytvořit vlastní uživatelská rozhraní pro vaše řešení pro systém Office.

[!include[Add-ins note](includes/addinsnote.md)]

 Nejnovější informace o vývoji pro Office najdete v centru pro [vývojáře systém Microsoft Office](https://developer.microsoft.com/office/docs).

## <a name="in-this-section"></a>V této části
- [Začněte &#40;vývoj pro Office v sadě Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)

 Obsahuje odkazy na informace o tom, jak nakonfigurovat vývojový počítač pro vytváření řešení pro systém Office, jak začít vytvářet řešení pro systém Office a co je nového pro vývoj pro Office v sadě Visual Studio.

- [Upgrade a migrace řešení pro systém Office](upgrading-and-migrating-office-solutions.md)

 Obsahuje odkazy na informace o procesu upgradu pro projekty vytvořené pomocí dřívějších verzí sady Visual Studio.

- [Architektura řešení pro systém Office v sadě Visual Studio](architecture-of-office-solutions-in-visual-studio.md)

 Obsahuje odkazy na informace o tom, jak fungují řešení Office, včetně informací o přizpůsobení na úrovni dokumentu a Doplňkech VSTO.

- [Návrh a vytváření řešení pro Systém Office](designing-and-creating-office-solutions.md)

 Tento článek obsahuje informace o tom, jak vytvořit projekt Office a nakonfigurovat ho v Visual Studio.

- [Vývoj řešení pro Office](developing-office-solutions.md)

 Poskytuje informace o tom, jak používat spravovaný kód s řešeními Office, včetně toho, jak přizpůsobit uživatelské rozhraní Office, pracovat s daty a řešit problémy.

- [Excelová řešení](excel-solutions.md)

 Tento článek obsahuje informace o automatizaci Excelu, vytváření excelových řešení a pochopení problémů s globalizací specifických pro Excel.

- [Řešení InfoPath](infopath-solutions.md)

 Tento článek obsahuje informace o vytváření šablon formulářů a doplňků VSTO pro aplikaci InfoPath.

- [Řešení outlooku](outlook-solutions.md)

 Tento článek obsahuje informace o automatizaci Outlooku a vytváření doplňků a oblastí formulářů Outlooku VSTO.

- [Řešení PowerPointu](powerpoint-solutions.md)

 Tento článek obsahuje informace o automatizaci PowerPointu a vytváření doplňků VSTO pro PowerPoint.

- [Řešení projektu](project-solutions.md)

 Tento článek obsahuje informace o automatizaci systém Microsoft Office projektu a vytváření doplňků VSTO projektu.

- [Řešení Visio](visio-solutions.md)

 Tento článek obsahuje informace o automatizaci visia a vytváření doplňků Visio VSTO.

- [Řešení pro word](word-solutions.md)

 Tento článek obsahuje informace o automatizaci wordových řešení a vytváření řešení aplikace Word.

- [Vytváření řešení pro Office](building-office-solutions.md)

 Poskytuje informace o rozdílech mezi sestavováním projektů Office a dalšími typy projektů v systému [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Ladění projektů Office](debugging-office-projects.md)

 Poskytuje informace o rozdílech mezi laděním projektů Office a dalšími typy projektů v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Zabezpečení řešení pro systém Office](securing-office-solutions.md)

 Obsahuje informace o tom, jak funkce zabezpečení fungují v řešeních pro systém Office.

- [Nasazení řešení pro systém Office](deploying-an-office-solution.md)

 Poskytuje informace o tom, jak zpřístupnit řešení Office uživatelům a jaké jsou hlavní problémy, které je potřeba vzít v úvahu při volbě metody nasazení.

- [Ukázky a návody pro vývoj pro Office](office-development-samples-and-walkthroughs.md)

 Obsahuje odkazy na ukázkové aplikace a témata, které poskytují podrobné pokyny pro provádění běžných úloh.

- [Obecné referenční informace &#40;vývoj pro Office v sadě Visual Studio&#41;](general-reference-office-development-in-visual-studio.md)

 Obsahuje odkazy na podrobné informace o sestaveních, manifestech, prvcích uživatelského rozhraní a chybových zprávách Office pro primární spolupráci.

- [Spravované referenční materiály &#40;vývoj pro Office v sadě Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md)

 Obsahuje odkazy na informace o oborech názvů a typech rozhraní API, které se používají v projektech Office, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Referenční dokumentace k rozhraní API pro obory názvů a typy, které se používají v projektech Office cílených na .NET Framework 3,5, najdete v následující referenční části dokumentace k sadě Visual Studio 2008: [2007 reference spravovaná systémem](managed-reference-office-development-in-visual-studio.md).

- [Nespravované Reference k rozhraní API &#40;vývoj pro Office v sadě Visual Studio&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Obsahuje odkazy na informace o rozhraních COM, která můžete použít k provádění akcí, jako je načítání a uvolňování spravovaných doplňků VSTO v aplikacích Office.

## <a name="related-sections"></a>Související oddíly
- [Vývoj pro Office s portálem pro vývojáře sady Visual Studio](https://developer.microsoft.com/office/docs) Poskytuje další zdroje, jako jsou například technické články, videa a blogy.

- [Středisko pro vývojáře sady Visual Studio](https://visualstudio.microsoft.com/) Poskytuje další prostředky sady Visual Studio, jako jsou například technické články, videa a blogy.

- [systém Microsoft Office vývojové části knihovny MSDN](/previous-versions/office/office-12/bb726434(v=office.12)) Oblast knihovny MSDN, kde najdete články a referenční dokumentaci týkající se vývoje řešení pro několik verzí Office (ne specifická pro vývoj pro Office pomocí Visual Studio).

- [Vývoj aplikací v Visual Studio](/previous-versions/h8w79z10(v=vs.140)) Obsahuje odkazy na témata, která vysvětlují, jak můžete pomocí Visual Studio navrhovat, vyvíjet, ladit a nasazovat webové aplikace, webové služby XML a tradiční klientské aplikace.

- [.NET Framework programování v Visual Studio](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Popisuje vývoj aplikací s .NET Framework v Visual Basic a Visual C#.
