---
title: Hierarchická organizace zdrojů pro lokalizaci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 11eeaa2c6742675372acf8b96280737f556c7799
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914135"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Hierarchická organizace zdrojů pro lokalizaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio jsou lokalizované prostředky (data, jako jsou řetězce a Image pro jednotlivé jazykové verze) uložená v samostatných souborech a načíst podle nastavení jazykové verze uživatelského rozhraní. Pochopit, jak jsou načteny lokalizované prostředky, je vhodné popřemýšlet z nich jako uspořádané hierarchické způsobem.  
  
## <a name="kinds-of-resources-in-the-hierarchy"></a>Typy prostředků v hierarchii  
  
- V horní části hierarchie "sedět" záložní prostředky pro vaše výchozí jazykovou verzi, třeba Angličtina ("en"). Toto jsou jediné prostředky, které nemají vlastní soubor. ukládají se v hlavní sestavení.  
  
- Následující materiály záložního prostředků pro všechny neutrální jazykové verze. Neutrální jazykovou verzi je přidružený jazyk, ale ne určitá země nebo oblast. Francouzština ("fr") je například neutrální jazykovou verzi. (Všimněte si, že záložní prostředky, se taky pro neutrální jazykovou verzi, ale speciální jeden.)  
  
- Níže jsou prostředků pro jakékoli konkrétní jazykové verze. Konkrétní jazykovou verzi je přidružený jazyk a zemi/oblast. Kanadská francouzština ("fr-CA") je třeba konkrétní jazykovou verzi.  
  
  Pokud aplikace se pokouší načíst všechny lokalizovaný prostředek, jako je řetězec a nebyly nalezeny, bude místo hierarchie dokud nenajde soubor prostředků obsahující požadovaný prostředek.  
  
  Nejlepší způsob, jak ukládat vaše prostředky se k zobecnění je co největší míře. To znamená, že k ukládání lokalizovaných řetězců, obrázků a tak dále v souborech prostředků neutrální jazykové verze, nikoli konkrétní jazykovou verzi, kdykoli je to možné. Například pokud máte prostředky pro Belgii francouzština ("fr-být") jazykovou verzi a okamžitě výše uvedené materiály záložního prostředků v angličtině, problém může dojít, když někdo v systému nakonfigurovaný pro jazykovou verzi francouzština Kanadské používá vaše aplikace. Systém nebude hledat satelitní sestavení pro "fr-CA", ho najít a načíst hlavní sestavení obsahující záložní prostředky, kterým je angličtina, namísto načítání francouzské prostředky. Následující obrázek znázorňuje tento scénář nežádoucí.  
  
  ![Jenom konkrétní prostředky](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")  
  
  Pokud budete postupovat podle doporučený postup uvedení množství prostředků je možné soubor prostředků neutrální pro jazykové verze "fr", Kanadské francouzský uživatel neuvidí prostředky označené pro "fr-být" jazykové verze, ale nezíská by zobrazený řetězce ve francouzštině. Následující situace ukazuje tento scénář upřednostňované.  
  
  ![NeutralSpecificResources – grafika](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")  
  
## <a name="see-also"></a>Viz také  
 [Neutrální jazyky zdrojů pro lokalizaci](../ide/neutral-resources-languages-for-localization.md)   
 [Zabezpečení a lokalizovaná satelitní sestavení](../ide/security-and-localized-satellite-assemblies.md)   
 [Lokalizace aplikací](../ide/localizing-applications.md)   
 [Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)   
 [Postupy: nastavení jazykové verze a jazykové verze uživatelského rozhraní pro globalizaci formulářů Windows](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)   
 [Postupy: nastavení jazykové verze a jazykové verze uživatelského rozhraní pro globalizaci webová stránka ASP.NET](http://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)

