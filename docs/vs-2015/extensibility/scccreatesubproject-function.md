---
title: Scccreatesubproject – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 905a3319627a54ef84b5d473d3725069a9f1eecb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766436"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce vytvoří dílčí projekt s daným názvem. v rámci existující projekt nadřazené určené `lpParentProjPath` argument.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Ukazatel kontext modulu plug-in zdroje ovládacího prvku.  
  
 hWnd  
 [in] Popisovač okna integrovaného vývojového prostředí, které modul plug-in správy zdrojového kódu můžete použít jako nadřazený pro všechna dialogová okna, které poskytuje.  
  
 lpUser  
 [out v] Uživatelské jméno (až SCC_USER_SIZE, včetně ukončovacího znaku NULL).  
  
 lpParentProjPath  
 [in] Řetězec identifikující cesta nadřazeného projektu (až SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
 lpSubProjName  
 [in] Název dílčí projekt navrhované (až SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
 lpAuxProjPath  
 [out v] Pomocné řetězec, který identifikuje projektu (až SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
 lpSubProjPath  
 [out v] Výstupní řetězec, který identifikuje cesta pro podprojekt (až SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Dílčí projekt se úspěšně vytvořil.|  
|SCC_E_INITIALIZEFAILED|Nadřazený projekt se nepovedlo inicializovat.|  
|SCC_E_INVALIDUSER|Uživatel nemůže přihlásit do systému správy zdrojového kódu.|  
|SCC_E_COULDNOTCREATEPROJECT|Nelze vytvořit dílčí projekt.|  
|SCC_E_PROJSYNTAXERR|Neplatný projekt syntaxe.|  
|SCC_E_UNKNOWNPROJECT|Nadřazený projekt Neznámý pro modul plug-in správy zdrojového kódu.|  
|SCC_E_INVALIDFILEPATH|Soubor je neplatný nebo nepoužitelné cesta.|  
|SCC_E_NOTAUTHORIZED|Uživatel nemůže k provedení této operace.|  
|SCC_E_ACCESSFAILURE|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize. Doporučuje se zkuste to znovu.|  
|SCC_E_CONNECTIONFAILURE|Došlo k potížím zdrojový ovládací prvek modulu plug-in připojení.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|K nespecifikované chybě.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud dílčí projekt s názvem již existuje, funkce můžete změnit výchozí název vytvořit jedinečný certifikát, například přidáním "_\<číslo >" k němu. Volající musí být připraveni přijmout změny `lpUser`, `lpSubProjPath`, a `lpAuxProjPath`. `lpSubProjPath` a`lpAuxProjPath` pak jsou argumenty použity ve volání [sccopenproject –](../extensibility/sccopenproject-function.md). Neměl by být upravovat volající po návratu. Tyto řetězce představují způsob pro modul plug-in pro sledování informací, které je potřeba přidružit k projektu správy zdrojového kódu. Volajícího prostředí IDE nezobrazí tyto dva parametry po návratu, protože modul plug-in můžete použít formátovaný řetězec, který nemusí být vhodný pro zobrazení. Funkce vrátí hodnotu úspěch nebo neúspěch a v případě úspěchu se vyplní proměnné `lpSubProjPath` s cestou úplný projekt do nového projektu.  
  
 Tato funkce je podobný [sccgetprojpath –](../extensibility/sccgetprojpath-function.md), s tím rozdílem, že tiše vytvoří projekt spíše než výzvy k výběru jedné. Když `SccCreateSubProject` funkce je volána, `lpParentProjName` a `lpAuxProjPath` nesmí být prázdný a bude odpovídat platný projekt. Tyto řetězce jsou obvykle přijatých integrovaného vývojového prostředí od předchozího volání `SccGetProjPath` funkce nebo [sccgetparentprojectpath –](../extensibility/sccgetparentprojectpath-function.md).  
  
 `lpUser` Argument je uživatelské jméno. Integrované vývojové prostředí bude předáno stejné uživatelské jméno, které bylo dříve přijaté z `SccGetProjPath`, a modul plug-in správy zdrojového kódu má použít jako výchozí název. Pokud uživatel už má otevření připojení pomocí modulu plug-in, modul plug-in by měl zkuste odstranit případné výzvy k Ujistěte se, že funkce pracuje bezobslužně. Ale pokud se přihlášení nezdaří, modul plug-in by se zobrazit výzva uživateli pro přihlášení a při přijetí platné přihlašovací údaje, předejte název zpět v `lpUser`. Vzhledem k tomu, že modul plug-in mohou změnit tento řetězec, integrovaném vývojovém prostředí vždy přidělit vyrovnávací paměť o velikosti (SCC_USER_LEN + 1 nebo SCC_USER_SIZE, což zahrnuje prostor pro ukončovacího znaku null). Pokud se změní řetězec nový řetězec musí být platné přihlašovací jméno (nejméně jako platná jako starý řetězec).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Scccreatesubproject – a sccgetparentprojectpath – technické poznámky  
 Přidávání řešení a projektů do správy zdrojových kódů zjednodušili jsme v sadě Visual Studio, chcete-li minimalizovat počet pokusů, které je uživatel vyzván k výběru umístění v systému správy zdrojového kódu. Tyto změny jsou aktivované pomocí sady Visual Studio, pokud obě nové funkce, podporuje modul plug-in správy zdrojového kódu `SccCreateSubProject` a `SccGetParentProjectPath`. Následující položku registru je však možné zakázat tyto změny a obnovit předchozí chování sady Visual Studio (zdrojový ovládací prvek modulu Plug-in API verze 1.1):  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
 Pokud tato položka registru neexistuje nebo je nastavena na hodnotu DWORD: 00000000, Visual Studio se pokusí použití těchto nových funkcí `SccCreateSubProject` a `SccGetParentProjectPath`.  
  
 Pokud položka registru má nastavenou hodnotu DWORD: 00000001, Visual Studio nebude pokoušet o použití těchto nových funkcí a operace přidání do správy zdrojových kódů fungují stejně jako v předchozích verzích sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu Plug-in zdroje ovládacího prvku](../extensibility/source-control-plug-in-api-functions.md)   
 [Sccgetparentprojectpath –](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)

