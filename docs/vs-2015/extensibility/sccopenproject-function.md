---
title: Sccopenproject – funkce | Dokumentace Microsoftu
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
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a0bcb33ee214c11c369e17dc90bce138c0014fc6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768276"
---
# <a name="sccopenproject-function"></a>SccOpenProject – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce se otevře existující projekt ovládacího prvku zdroje nebo vytvoří nový.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontext modulu plug-in zdroje ovládacího prvku.  
  
 hWnd  
 [in] Popisovač okna integrovaného vývojového prostředí, které modul plug-in správy zdrojového kódu můžete použít jako nadřazený pro všechna dialogová okna, které poskytuje.  
  
 lpUser  
 [out v] Název uživatele (nesmí přesáhnout SCC_USER_SIZE, včetně ukončovacího znaku NULL).  
  
 lpProjName  
 [in] Řetězec identifikující název projektu.  
  
 lpLocalProjPath  
 [in] Cesta pracovní složky projektu.  
  
 lpAuxProjPath  
 [out v] Volitelné pomocné řetězec identifikující projektu (nesmí přesáhnout SCC_AUXPATH_SIZE, včetně ukončovacího znaku NULL).  
  
 lpComment  
 [in] Komentář na nový projekt, který se vytváří.  
  
 lpTextOutProc  
 [in] Funkce jazyka volitelné zpětného volání pro zobrazení textového výstupu z modulu plug-in správy zdrojového kódu.  
  
 dwFlags  
 [in] Signály, zda nového projektu je potřeba vytvořit, pokud je projekt neznámé zdroje ovládací prvek modulu plug-in. Hodnota může být kombinací `SCC_OP_CREATEIFNEW` a `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Úspěch v otevření projektu.|  
|SCC_E_INITIALIZEFAILED|Projekt se nepovedlo inicializovat.|  
|SCC_E_INVALIDUSER|Uživatel nemůže přihlásit do systému správy zdrojového kódu.|  
|SCC_E_COULDNOTCREATEPROJECT|Projekt před voláním; neexistuje.  `SCC_OPT_CREATEIFNEW` byl nastaven příznak, ale projekt se nevytvořil.|  
|SCC_E_PROJSYNTAXERR|Neplatný projekt syntaxe.|  
|SCC_E_UNKNOWNPROJECT|Projekt Neznámý do modulu plug-in správy zdrojového kódu a `SCC_OPT_CREATEIFNEW` příznakem nenastavila.|  
|SCC_E_INVALIDFILEPATH|Soubor je neplatný nebo nepoužitelné cesta.|  
|SCC_E_NOTAUTHORIZED|Uživatel nemůže k provedení této operace.|  
|SCC_E_ACCESSFAILURE|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize. Doporučuje se zkuste to znovu.|  
|SCC_E_NONSPECFICERROR|Obecná chyba; systém správy zdrojového kódu nebyla inicializována.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní IDE může předat uživatelské jméno (`lpUser`), nebo ho jednoduše předat ukazatel na prázdný řetězec. Pokud je uživatelské jméno, modul plug-in správy zdrojového kódu by měl používat jako výchozí. Nicméně pokud nebyl předán žádný název, nebo pokud se přihlášení nezdařilo se zadaným názvem, modul plug-in měl vyzvat uživatele k přihlášení a vrátí platný název v `lpUser` při přijetí platné přihlašovací údaje`.` vzhledem k tomu, že modul plug-in mohou změnit řetězce uživatelského jména , rozhraní IDE se vždy přidělí vyrovnávací paměť o velikosti (`SCC_USER_LEN`+ 1 nebo SCC_USER_SIZE, což zahrnuje prostor pro ukončovacího znaku null).  
  
> [!NOTE]
>  První akci integrovaného vývojového prostředí může být nutné provést může být volání konstruktoru `SccOpenProject` funkce nebo [sccgetprojpath –](../extensibility/sccgetprojpath-function.md). Z tohoto důvodu obou z nich mít identická `lpUser` parametru.  
  
 `lpAuxProjPath` a`lpProjName` jsou čtení ze souboru řešení nebo jsou vráceny z volání `SccGetProjPath` funkce. Tyto parametry obsahují řetězce, které modul plug-in správy zdrojového kódu se přidruží k projektu a mají smysl jenom pro modul plug-in. Pokud žádný takový řetězce v souboru řešení a nebyl byl uživatel vyzván k procházení (která vrátí řetězec prostřednictvím `SccGetProjPath` funkce), integrovaného vývojového prostředí předá prázdné řetězce pro obě `lpAuxProjPath` a `lpProjName`a očekává, že tyto hodnoty aktualizovat pomocí modulu plug-in když tato funkce vrátí.  
  
 `lpTextOutProc` je ukazatel na funkci zpětného volání poskytovaných IDE pro účely zobrazení výstupu výsledku příkazu modulu plug-in správy zdrojového kódu. Tato funkce zpětného volání je podrobně popsán v [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Pokud modul plug-in správy zdrojového kódu se chce využít výhody tohoto, musí mít nastaven `SCC_CAP_TEXTOUT` příznak v [sccinitialize –](../extensibility/sccinitialize-function.md). Pokud tento příznak nebyla nastavena nebo prostředí IDE nepodporuje tuto funkci `lpTextOutProc` bude `NULL`.  
  
 `dwFlags` Parametr určuje výsledek v případě, že se otevření projektu neexistuje. Skládá se ze dvou příznaky bitflag `SCC_OP_CREATEIFNEW` a `SCC_OP_SILENTOPEN`. Pokud projekt otevírané již existuje, funkce jednoduše otevře projekt a vrátí `SCC_OK`. Pokud projekt neexistuje a pokud `SCC_OP_CREATEIFNEW` příznak zapnutý, modul plug-in správy zdrojového kódu vytvoření projektu v systému správy zdrojového kódu, otevřete ho a vracet `SCC_OK`. Pokud projekt neexistuje a pokud `SCC_OP_CREATEIFNEW` příznak je vypnuté, modul plug-in byste pak vyhledejte `SCC_OP_SILENTOPEN` příznak. Pokud na tento příznak není, může modul plug-in požádat uživatele o název projektu. Pokud tento příznak zapnutý, modul plug-in jednoduše vrátit `SCC_E_UNKNOWNPROJECT`.  
  
## <a name="calling-order"></a>Pořadí volání  
 Při běžném průběhu událostí [sccinitialize –](../extensibility/sccinitialize-function.md) by byla volána nejprve otevřete relaci zdrojového ovládacího prvku. Relace se může skládat z volání `SccOpenProject`, za nímž následuje jiných volání funkcí rozhraní API modulu Plug-in zdroje ovládacího prvku a bude ukončen voláním [scccloseproject –](../extensibility/scccloseproject-function.md). Tato relace může opakovat několikrát před [sccuninitialize –](../extensibility/sccuninitialize-function.md) je volána.  
  
 Pokud zdroj modulu plug-in sady `SCC_CAP_REENTRANT` bit v `SccInitialize`, pak výše uvedené pořadí relace může opakuje tolikrát, kolikrát paralelně. Různé `pvContext` struktury sledovat různé relace, ve nichž každý `pvContext` je spojen s jeden otevřít projekt současně. Na základě`pvContext` parametr, modul plug-in můžete určit, který projekt se odkazuje v žádném konkrétním volání. Pokud bit možnost `SCC_CAP_REENTRANT` není nastavena, nonreentrant plug-in správy zdrojového kódu moduly mají omezenou schopnost pracovat s více projekty.  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT` Bit byla zavedena ve verzi 1.1 rozhraní API modulu Plug-in zdroje ovládacího prvku. Není nastavena nebo je ignorován ve verzi 1.0, a všechny verze 1.0 ovládací prvek moduly plug-in zdrojového kódu budou považovat za nonreentrant.  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu Plug-in zdroje ovládacího prvku](../extensibility/source-control-plug-in-api-functions.md)   
 [Scccloseproject –](../extensibility/scccloseproject-function.md)   
 [Sccgetprojpath –](../extensibility/sccgetprojpath-function.md)   
 [Sccinitialize –](../extensibility/sccinitialize-function.md)   
 [Sccuninitialize –](../extensibility/sccuninitialize-function.md)   
 [Omezení délky řetězců](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)

