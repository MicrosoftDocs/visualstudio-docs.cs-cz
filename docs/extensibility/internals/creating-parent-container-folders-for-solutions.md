---
title: Vytváření nadřazených složek kontejnerů pro řešení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e5481e20a12fc05ccba97eef55173e5ce9b30d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709103"
---
# <a name="create-parent-container-folders-for-solutions"></a>Vytvoření složek nadřazených kontejnerů pro řešení
V rozhraní Plug-in Source Control API verze 1.2 může uživatel zadat jeden cíl kořenového ovládacího prvku zdrojového kódu pro všechny webové projekty v rámci řešení. Tento jeden kořen se nazývá Super Unified Root (SUR).

 V rozhraní Plug-in Source Control API verze 1.1, pokud uživatel přidal víceprojektové řešení do správy zdrojového kódu, byl uživatel vyzván k zadání jednoho cíle správy zdrojového kódu pro každý webový projekt.

## <a name="new-capability-flags"></a>Nové příznaky schopností
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nové funkce
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] téměř vždy vytvoří složku SUR při přidávání řešení do správy zdrojového kódu. Konkrétně tak činí v následujících případech:

- Projekt je webový projekt sdílení souborů.

- Existují různé jednotky pro projekt a soubor řešení.

- Existují různé sdílené složky pro projekt a soubor řešení.

- Projekty byly přidány samostatně (v řešení řízeném zdrojem).

V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]aplikace se doporučuje, aby byl název složky SUR stejný jako název řešení bez rozšíření. Následující tabulka shrnuje chování v obou verzích.

|Funkce|Rozhraní API modulu plug-in správy zdrojového kódu verze 1.1|Rozhraní API modulu plug-in správy zdrojového kódu verze 1.2|
|-------------| - | - |
|Přidat řešení do SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Přidání projektu do řešení řízeného zdrojem|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Poznámka:**  Visual Studio předpokládá, že řešení je přímým podřízeným SUR.|

## <a name="examples"></a>Příklady
 V následující tabulce jsou uvedeny dva příklady. V obou případech [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je uživatel vyzván k zadání cílového umístění řešení pod smytí zdrojového kódu, dokud nebude jako cíl zadán *user_choice.* Pokud je zadán user_choice, řešení a dva projekty jsou přidány bez výzvy uživatele k určení správy zdrojového kódu.

|Roztok obsahuje|Na disku umístění|Výchozí struktura databáze|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:\Řešení\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:\Řešení\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 Složka a podsložky SUR jsou vytvořeny bez ohledu na to, zda je operace zrušena nebo selže z důvodu chyby. Nejsou automaticky odebrány v podmínkách zrušení nebo chyb.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]výchozí verze 1.1 chování, pokud modul plug-in `SCC_CAP_CREATESUBPROJECT` `SCC_CAP_GETPARENTPROJECT` správy zdrojového kódu nevrátí a příznaky schopností. Kromě toho uživatelé [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mohou zvolit, aby se vrátil k verzi 1.1 chování nastavením hodnoty následující ho *dword:00000001*:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*

## <a name="see-also"></a>Viz také
- [Co je nového v rozhraní Plug-in Plug-in API správy zdrojového kódu verze 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
