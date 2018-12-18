---
title: Sccgetparentprojectpath – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 828c72224655f404e88ac0913908ef293119ccb3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855154"
---
# <a name="sccgetparentprojectpath-function"></a>Sccgetparentprojectpath – funkce
Tato funkce Určuje nadřazený projekt cestu zadaný projekt. Tato funkce je volána, když uživatele je přidání projektu sady Visual Studio do správy zdrojového kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
### <a name="parameters"></a>Parametry  
 pContext  
 [in] Ukazatel kontext modulu plug-in zdroje ovládacího prvku.  
  
 hWnd  
 [in] Popisovač okna integrovaného vývojového prostředí, které modul plug-in správy zdrojového kódu můžete použít jako nadřazený pro všechna dialogová okna, které poskytuje.  
  
 lpUser  
 [out v] Uživatelské jméno (až SCC_USER_SIZE, včetně ukončovacího znaku NULL).  
  
 lpProjPath  
 [in] Řetězec, který identifikuje cesta k projektu (až SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
 lpAuxProjPath  
 [out v] Pomocné řetězec, který identifikuje projektu (až SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
 lpParentProjPath  
 [out v] Výstupní řetězec, který identifikuje nadřazená cesta projektu (až SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Cesta k nadřazenému projektu byl úspěšně získán.|  
|SCC_E_INITIALIZEFAILED|Projekt se nepovedlo inicializovat.|  
|SCC_E_INVALIDUSER|Uživatele nejde se přihlásit do modulu plug-in správy zdrojového kódu.|  
|SCC_E_UNKNOWNPROJECT|Projekt Neznámý pro modul plug-in správy zdrojového kódu.|  
|SCC_E_INVALIDFILEPATH|Soubor je neplatný nebo nepoužitelné cesta.|  
|SCC_E_NOTAUTHORIZED|Uživatel nemůže k provedení této operace.|  
|SCC_E_ACCESSFAILURE|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize. Doporučuje se zkuste to znovu.|  
|SCC_E_PROJSYNTAXERR|Neplatný projekt syntaxe.|  
|SCC_E_CONNECTIONFAILURE|Store problému s připojením.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|K nespecifikované chybě.|  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce vrátí hodnotu úspěch nebo neúspěch a v případě úspěchu se vyplní proměnné `lpParentProjPath` s cestou úplné projektu do zadaného projektu.  
  
 Tato funkce vrací nadřazená cesta k projektu z existujícího projektu. Pro projekt, root, funkce vrátí cesta k projektu, který byl předán (to znamená, stejné kořenové projektu cesta). Všimněte si, že cestu k projektu je řetězec, který má smysl pouze na modul plug-in správy zdrojového kódu.  
  
 Rozhraní IDE je připraven přijmout změny `lpUser` a `lpAuxProjPath` také parametry. Rozhraní IDE se zachovat tyto řetězce a předat je do [sccopenproject –](../extensibility/sccopenproject-function.md) když uživatel otevře tento projekt v budoucnu. Tyto řetězce, proto se poskytují způsob pro modul plug-in pro sledování informací, které je potřeba přidružit k projektu správy zdrojového kódu.  
  
 Tato funkce je podobný [sccgetprojpath –](../extensibility/sccgetprojpath-function.md), s tím rozdílem, že výzvu uživateli vybrat projekt. Taky nikdy vytvoří nový projekt, ale funguje pouze s existující projekt.  
  
 Když `SccGetParentProjectPath` se nazývá `lpProjPath` a `lpAuxProjPath` nesmí být prázdný a bude odpovídat platný projekt. Tyto řetězce jsou obvykle přijatých integrovaného vývojového prostředí od předchozího volání `SccGetProjPath` funkce.  
  
 `lpUser` Argument je uživatelské jméno. Předá integrovaného vývojového prostředí ve stejné uživatelské jméno, které bylo dříve poslal `SccGetProjPath` funkce a modulu plug-in správy zdrojového kódu má použít jako výchozí název. Pokud uživatel už má otevření připojení pomocí modulu plug-in, modul plug-in by měl zkuste odstranit případné výzvy k Ujistěte se, že funkce pracuje bezobslužně. Ale pokud se přihlášení nezdaří, modul plug-in by se zobrazit výzva uživateli pro přihlášení a při přijetí platné přihlašovací údaje, předejte název zpět v `lpUser`. Vzhledem k tomu, že modul plug-in mohou změnit tento řetězec, rozhraní IDE se vždy přidělí vyrovnávací paměť o velikosti (`SCC_USER_LEN`+ 1). Pokud se změní řetězec nový řetězec musí být platné přihlašovací jméno (nejméně jako platná jako starý řetězec).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Scccreatesubproject – a sccgetparentprojectpath – technické poznámky  
 Přidávání řešení a projektů do správy zdrojových kódů zjednodušili jsme v sadě Visual Studio, chcete-li minimalizovat počet pokusů, které je uživatel vyzván k výběru umístění v systému správy zdrojového kódu. Tyto změny jsou aktivované pomocí sady Visual Studio, pokud obě nové funkce, podporuje modul plug-in správy zdrojového kódu [scccreatesubproject –](../extensibility/scccreatesubproject-function.md) a `SccGetParentProjectPath` funkce. Následující položku registru je však možné zakázat tyto změny a obnovit předchozí chování sady Visual Studio (zdrojový ovládací prvek modulu Plug-in API verze 1.1):  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001**  
  
 Pokud tato položka registru neexistuje nebo je nastavena na hodnotu DWORD: 00000000, Visual Studio se pokusí použití těchto nových funkcí `SccCreateSubProject`a`SccGetParentProjectPath`.  
  
 Pokud položka registru má nastavenou hodnotu DWORD: 00000001, Visual Studio nebude pokoušet o použití těchto nových funkcí a operace přidání do správy zdrojových kódů fungují stejně jako v předchozích verzích sady Visual Studio.  
  
## <a name="see-also"></a>Viz také:  
 [Funkce modulu plug-in API zdrojového ovládacího prvku](../extensibility/source-control-plug-in-api-functions.md)   
 [Scccreatesubproject –](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)