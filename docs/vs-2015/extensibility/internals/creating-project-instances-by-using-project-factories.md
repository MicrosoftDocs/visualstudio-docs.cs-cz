---
title: Vytváření instancí projektu pomocí objektů pro vytváření projektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 358c13bdc8bc312a479b9c316fa516ad68b10630
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736245"
---
# <a name="creating-project-instances-by-using-project-factories"></a>Vytváření instancí projektu pomocí objektů pro vytváření projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typů projektů v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] použít *objekt pro vytváření projektu* pro vytvoření instancí objektů projektu. Objekt pro vytváření projektu je podobná objekt pro vytváření tříd standardní cocreatable objektů COM. Nicméně objekty projektu nejsou cocreatable: je třeba pouze vytvořit pomocí objekt pro vytváření projektu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Volá objekt pro vytváření projektů v vašeho balíčku VSPackage implementovat, pokud uživatel načte existující projekt nebo vytvoří nový projekt v integrovaném vývojovém prostředí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Nový objekt projektu poskytuje integrované vývojové prostředí s dostatek informací k naplnění Průzkumníku řešení. Nový objekt projektu také poskytuje požadovaná rozhraní pro podporu všechny příslušné akce uživatelského rozhraní inicializuje v integrovaném vývojovém prostředí.  
  
 Můžete implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> rozhraní ve třídě ve vašem projektu. Obvykle se nachází v jeho vlastní modul.  
  
 Příklad implementace `IVsProjectFactory` rozhraní najdete v tématu PrjFac.cpp, která je součástí [základního projektu](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) ukázka adresáře.  
  
 Projekty, které podporují agregaci vlastník musí zachovat klíčem vlastníka v jejich souboru projektu. Když <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metoda je volána v projektu s klíčem vlastníka, vlastnictví projektu převede na objekt pro vytváření projektu GUID pak zavolá jeho vlastníka klíč `CreateProject` metody v této výrobě projektu provedete skutečné vytváření.  
  
## <a name="creating-an-owned-project"></a>Vytvoření projektu vlastněná podnikem  
 Vlastník vytvoří vlastní projekt ve dvou fázích:  
  
1. Při volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metody. Díky tomu vlastnictví projektu příležitost k vytvoření objektu agregované projektu založen na vstupní řízení `IUnknown`. Vlastněné projektu předá vnitřní `IUnknown` a agregovaného objektu zpátky do projektu vlastníka. Díky tomu vlastnictví projektu příležitost k uložení vnitřní `IUnknown`.  
  
2. Při volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metody. Vlastněné project sleduje všechny její instance, když tato metoda je volána, bez volání `IVsProjectFactory::CreateProject` jako by tomu bylo v případě projektů, které nejsou vlastněny. Vstup `VSOWNEDPROJECTOBJECT` výčet je obvykle agregované vlastnictví projektu. Vlastněné projektu pomocí této proměnné můžete určit, zda již byla vytvořena jeho objekt projektu (soubor cookie není rovno NULL) nebo musí být vytvořeny (rovná se soubor cookie NULL).  
  
   Typy projektů jsou označeny projekt jedinečný identifikátor GUID, podobně jako na identifikátor CLSID objektu COM cocreatable. Obvykle zpracovává jeden projekt objekt pro vytváření vytváření instancí typu jednoho projektu, i když je možné mít jeden objekt pro vytváření projektu zpracovávat více než jeden projekt typu GUID.  
  
   Typy projektů jsou spojeny s konkrétní příponou názvu. Když uživatel pokusí otevřít existující soubor projektu nebo se pokusí vytvořit nový projekt pomocí klonování šablony, integrovaném vývojovém prostředí používá rozšíření souboru k určení odpovídajícího projektu GUID.  
  
   Jakmile rozhraní IDE zjistí, jestli musíte vytvořit nový projekt nebo otevřete existující projekt určitého typu, integrovaném vývojovém prostředí používá informace v systémovém registru pod [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] k vyhledání, která VSPackage implementuje objekt pro vytváření požadované projektu. Rozhraní IDE načte tento VSPackage. V <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metoda sady VSPackage musíte zaregistrovat jeho objekt pro vytváření projektů pomocí integrovaného vývojového prostředí pomocí volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> metody.  
  
   Hlavní metodou `IVsProjectFactory` rozhraní je <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> který by měl zpracovat dva scénáře: otevření existujícího projektu a vytvoření nového projektu. Většina projektů jejich stav projektu uložený v souboru projektu. Obvykle jsou nové projekty vytvořené vytváření kopie souboru šablony předán `CreateProject` metodu a poté otevřou kopie. Existující projekty se mohl vytvořit jeho instanci přímo otevření souboru projektu předány `CreateProject` metody. `CreateProject` Metodu můžete zobrazit další funkce uživatelského rozhraní pro uživatele podle potřeby.  
  
   Projekt můžete také použít žádné soubory a místo toho uložte jeho stav projektu v mechanismus pro ukládání než systém souborů, jako jsou databáze nebo webového serveru. V tomto případě předán parametr název souboru `CreateProject` metoda není ve skutečnosti cestu systému souborů, ale jedinečný řetězec – adresa URL – k identifikaci dat projektu. Není potřeba kopírovat soubory šablon, které jsou předány `CreateProject` aktivuje sekvenci odpovídající konstruktoru, který má být proveden.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)

