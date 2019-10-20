---
title: Neutrální jazyky zdrojů pro lokalizaci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85e0be0172f27732f8efeb882cbcde5b9c6aef3d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670391"
---
# <a name="neutral-resources-languages-for-localization"></a>Neutrální jazyky zdrojů pro lokalizaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Třída <xref:System.Resources.NeutralResourcesLanguageAttribute> určuje jazykovou verzi prostředků obsažených v hlavním sestavení. Tento atribut se používá jako zvýšení výkonu, aby objekt <xref:System.Resources.ResourceManager> nehledal prostředky, které jsou zahrnuty v hlavním sestavení.

 Následující kód ukazuje, jak nastavit neutrální jazyk prostředků. Kód lze umístit buď do skriptu sestavení, nebo do souboru AssemblyInfo. vb nebo AssemblyInfo.cs.

```vb
' Set neutral resources language for assembly.
<Assembly: NeutralResourcesLanguageAttribute("en")>

```

```csharp
// Set neutral resources language for assembly.
[assembly: NeutralResourcesLanguageAttribute("en")]
```

## <a name="see-also"></a>Viz také
 <xref:System.Resources.ResourceManager> [Seznámení s mezinárodními aplikacemi na základě .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [hierarchické organizace prostředků pro lokalizaci](../ide/hierarchical-organization-of-resources-for-localization.md) [aplikací](../ide/localizing-applications.md) [, které využívají globalizaci a lokalizaci aplikací](../ide/globalizing-and-localizing-applications.md)
