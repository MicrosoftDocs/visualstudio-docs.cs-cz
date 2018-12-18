---
title: Vytváření složek nadřazený kontejnerů pro řešení | Dokumentace Microsoftu
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
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0a65595b7dabc28a6851820141a71460d84a4b73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762529"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Vytváření složek nadřazených kontejnerů pro řešení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Do zdrojového ovládacího prvku modulu Plug-in verze rozhraní API 1.2 můžete uživatele zadejte cílovou složku jeden kořenový zdrojového ovládacího prvku pro všechny webové projekty v řešení. Tento jeden kořenový se nazývá Super Unified Root (SUR).  
  
 V rozhraní zdrojového ovládacího prvku modulu Plug-in API verze 1.1 Pokud uživatel přidán multiprojektová řešení do správy zdrojového kódu se uživatel vyzván a zadejte jednu cílovou složku zdrojového ovládacího prvku pro každý webový projekt.  
  
## <a name="new-capability-flags"></a>Nové příznaky funkcí  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nové funkce  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE vytvoří složku SUR téměř vždy, když přidání řešení do správy zdrojového kódu. Konkrétně provádí se v následujících případech:  
  
- Projekt je sdílenou složku webového projektu.  
  
- Existují různé jednotky pro projekt a soubor řešení.  
  
- Existují jiné sdílené složky pro projekt a soubor řešení.  
  
- Projekty byly přidány samostatně (v řešení se spravovanými zdroji).  
  
  V [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] doporučuje se, že název složky SUR být stejný jako název řešení bez přípony. Následující tabulka shrnuje chování v obou verzích.  
  
|Funkce|tSource ovládací prvek modulu Plug-in API verze 1.1|Zdroj modulu Plug-in API správy ve verzi 1.2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Přidat řešení do SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Přidat projekt do řešení se spravovanými zdroji|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Poznámka:** sady Visual Studio předpokládá, že řešení je přímý podřízený sursaft|  
  
## <a name="examples"></a>Příklady  
 V následující tabulce jsou uvedeny dva příklady. V obou případech [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uživatel je vyzván k zadání cílové umístění pro řešení pod správou zdrojového kódu až *user_choice* je zadán jako cíl. Je-li user_choice zadána, jsou přidány dva projekty a řešení bez výzvy k zadání cíle ovládacího prvku zdroje.  
  
|Řešení obsahuje|Na umístění disku|Struktury výchozí databáze|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Server web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/serveru Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Server web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/serveru web1<br /><br /> $/*user_choice*  /sln1/win1|  
  
 Bez ohledu na to, jestli tato operace se zrušila, nebo se nepovedlo kvůli chybě se vytvoří SUR složce a jejích podsložkách. Nejsou odebrány automaticky v zrušit nebo chybové podmínky.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] použije výchozí chování verze 1.1, pokud modul plug-in správy zdrojového kódu nevrací `SCC_CAP_CREATESUBPROJECT` a `SCC_CAP_GETPARENTPROJECT` příznaky funkcí. Kromě toho uživatelům [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] můžete obnovit nastavením hodnoty klíče na DWORD: 00000001 verze 1.1 chování:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
## <a name="see-also"></a>Viz také  
 [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

