---
title: Hierarchická organizace prostředků pro lokalizaci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a79caca18c7813605ff851eea6bda642e6300a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645617"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Hierarchická organizace zdrojů pro lokalizaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio jsou lokalizované prostředky (data, jako jsou například řetězce a obrázky vhodné pro jednotlivé jazykové verze) uloženy v samostatných souborech a načteny podle nastavení jazykové verze uživatelského rozhraní. Aby bylo možné pochopit, jak jsou lokalizované prostředky načteny, je vhodné je považovat hierarchicky uspořádaným způsobem.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Druhy prostředků v hierarchii

- V horní části hierarchie Zasaďte záložní prostředky pro výchozí jazykovou verzi, například English ("en"). Toto jsou jediné prostředky, které nemají vlastní soubor. jsou uloženy v hlavním sestavení.

- Pod záložními prostředky jsou prostředky pro jakékoli neutrální jazykové verze. Neutrální jazyková verze je přidružena k jazyku, ale nikoli zemi nebo oblasti. Například francouzština ("fr") je neutrální jazyková verze. (Všimněte si, že záložní prostředky jsou také pro neutrální jazykovou verzi, ale zvláštní.)

- Níže jsou uvedeny prostředky pro všechny konkrétní jazykové verze. Konkrétní jazyková verze je přidružená k jazyku a zemi nebo oblasti. Například francouzština kanadská ("fr-CA") je specifická jazyková verze.

  Pokud se aplikace pokusí načíst libovolný lokalizovaný prostředek, jako je například řetězec, a nenalezne jej, bude procházet hierarchii, dokud nenajde soubor prostředků obsahující požadovaný prostředek.

  Nejlepším způsobem, jak ukládat vaše prostředky, je co nejvíc zobecnit. To znamená, že pokud je to možné, ukládají se lokalizované řetězce, obrázky a tak dále do souborů prostředků pro neutrální kultury namísto konkrétních kultur. Například pokud máte prostředky pro jazykovou verzi francouzštiny ("fr-to") a výše uvedené prostředky jsou záložními prostředky v angličtině, může dojít k problému, když někdo používá vaši aplikaci v systému nakonfigurovaném pro kanadskou jazykovou verzi francouzštiny. Systém bude hledat satelitní sestavení pro "fr-CA", nenalezne ho a načte hlavní sestavení obsahující záložní prostředek, který je English, místo nasazování francouzských prostředků. Následující obrázek znázorňuje tento nežádoucí scénář.

  ![Pouze konkrétní prostředky](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")

  Pokud budete postupovat podle doporučené praxe umístění tolika prostředků do neutrálního souboru prostředků pro jazykovou verzi "fr", francouzskému kanadskému uživateli se nezobrazují prostředky označené pro jazykovou verzi "fr-", ale budou se zobrazovat jako řetězce ve francouzštině. V následující situaci se zobrazuje upřednostňovaný scénář.

  ![Obrázek NeutralSpecificResources](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")

## <a name="see-also"></a>Viz také
 [Neutrální jazyky zdrojů pro lokalizaci](../ide/neutral-resources-languages-for-localization.md) [zabezpečení a lokalizované satelitní sestavení](../ide/security-and-localized-satellite-assemblies.md) [lokalizace aplikací](../ide/localizing-applications.md) [globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md) [Postupy: nastavení jazykové verze a jazykové verze uživatelského rozhraní pro model Windows Forms Globalizace](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) [Postup: nastavení jazykové verze a jazykové verze uživatelského rozhraní pro globalizaci webové stránky v ASP.NET](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)
