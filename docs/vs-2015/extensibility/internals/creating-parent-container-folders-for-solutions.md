---
title: Vytváření nadřazených složek kontejneru pro řešení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b756da118943dd94bfd3bc5220dfc398c60e2a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196924"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Vytváření složek nadřazených kontejnerů pro řešení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V rozhraní API modulu plug-in správy zdrojového kódu verze 1,2 může uživatel pro všechny webové projekty v rámci řešení zadat jeden cíl ovládacího prvku kořenového zdrojového kódu. Tento jediný kořen se nazývá Super Unified root (SUR).  
  
 V rozhraní API modulu plug-in správy zdrojového kódu verze 1,1, pokud uživatel přidal řešení s více projekty do správy zdrojových kódů, byl uživateli vyzván k zadání jednoho cíle správy zdrojového kódu pro každý webový projekt.  
  
## <a name="new-capability-flags"></a>Nové příznaky schopností  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nové funkce  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Rozhraní IDE téměř vždy vytvoří SLOŽKU sur při přidávání řešení do správy zdrojového kódu. Konkrétně to provede v následujících případech:  
  
- Projekt je webový projekt sdílení souborů.  
  
- Pro projekt a soubor řešení existují různé jednotky.  
  
- Pro projekt a soubor řešení existují různé sdílené složky.  
  
- Projekty byly přidány samostatně (v řešení se správou zdrojového kódu).  
  
  V [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] takovém případě doporučujeme, aby název složky sur byl stejný jako název řešení bez přípony. Následující tabulka shrnuje chování ve dvou verzích.  
  
|Příznak|rozhraní API tSource ovládacího prvku modulu plug-in pro správu a verzi 1,1|Rozhraní API modulu plug-in správy zdrojového kódu verze 1,2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Přidat řešení do SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Přidat projekt do řešení se správou zdrojů|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject () **Poznámka:**  Visual Studio předpokládá, že řešení je přímým podřízeným prvku sur.|  
  
## <a name="examples"></a>Příklady  
 V následující tabulce jsou uvedeny dva příklady. V obou případech [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se uživateli zobrazí výzva k zadání cílového umístění řešení v rámci správy zdrojového kódu, dokud není  *user_choice* zadáno jako cíl. Pokud je zadána user_choice, řešení a dva projekty jsou přidány bez zobrazení výzvy uživateli pro cíle správy zdrojových kódů.  
  
|Řešení obsahuje|Na diskových místech|Výchozí struktura databáze|  
|-----------------------|-----------------------|--------------------------------|  
|sln1. sln<br /><br /> WEB1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot $ \web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*/C/WEB1<br /><br /> $/*user_choice*/web2|  
|sln1. sln<br /><br /> WEB1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*/D/WEB1<br /><br /> $/*user_choice*/sln1/win1|  
  
 Složka SUR a podsložky jsou vytvořeny bez ohledu na to, zda byla operace zrušena nebo dojde k chybě z důvodu chyby. Nejsou automaticky odebrány v podmínkách zrušení nebo chyb.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] použije se výchozí chování verze 1,1, pokud modul plug-in správy zdrojových kódů nevrací `SCC_CAP_CREATESUBPROJECT` `SCC_CAP_GETPARENTPROJECT` značky a schopnosti. Kromě toho mohou uživatelé [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zvolit možnost vrátit se k chování verze 1,1 nastavením hodnoty následujícího klíče na hodnotu DWORD: 00000001:  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
## <a name="see-also"></a>Viz také  
 [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
