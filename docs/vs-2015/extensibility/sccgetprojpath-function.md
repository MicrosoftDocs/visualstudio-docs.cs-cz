---
title: Funkce SccGetProjPath | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 585402efbda165844f449e2477d5ca69722613a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64781881"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce vyzve uživatele k zadání cesty k projektu, což je řetězec, který je smysluplný pouze pro modul plug-in správy zdrojových kódů. Je volána, když je uživatel:  
  
- Vytvoření nového projektu  
  
- Přidání existujícího projektu do správy verzí  
  
- Probíhá pokus o nalezení existujícího projektu správy verzí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 pro Struktura kontextu modulu plug-in správy zdrojových kódů.  
  
 hWnd  
 pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.  
  
 lpUser  
 [in, out] Uživatelské jméno (nesmí přesáhnout SCC_USER_SIZE, včetně ukončovacího znaku NULL)  
  
 lpProjName  
 [in, out] Název projektu IDE, pracovní prostor projektu nebo soubor pravidel (nesmí přesáhnout SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
 lpLocalPath  
 [in, out] Pracovní cesta projektu. Pokud `bAllowChangePath` je `TRUE` , modul plug-in správy zdrojového kódu může tento řetězec změnit (nesmí přesahovat _MAX_PATH, včetně ukončovacího znaku null).  
  
 lpAuxProjPath  
 [in, out] Vyrovnávací paměť pro vrácenou cestu projektu (nesmí přesahovat SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
 bAllowChangePath  
 pro V takovém případě se `TRUE` modul plug-in správy zdrojového kódu může vyzvat a upravit `lpLocalPath` řetězec.  
  
 pbNew  
 [in, out] Hodnota přicházející v označuje, zda se má vytvořit nový projekt. Vrácená hodnota indikuje úspěch při vytváření projektu:  
  
|Příchozí|Interpretace|  
|--------------|--------------------|  
|TRUE|Uživatel může vytvořit nový projekt.|  
|FALSE|Uživatel nemůže vytvořit nový projekt.|  
  
|Odesílaná|Interpretace|  
|--------------|--------------------|  
|TRUE|Vytvořil se nový projekt.|  
|FALSE|Byl vybrán existující projekt.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Projekt byl úspěšně vytvořen nebo načten.|  
|SCC_I_OPERATIONCANCELED|Operace byla zrušena.|  
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize.|  
|SCC_E_CONNECTIONFAILURE|Při pokusu o připojení k systému správy zdrojů došlo k potížím.|  
|SCC_E_NONSPECIFICERROR|Došlo k neurčené chybě.|  
  
## <a name="remarks"></a>Poznámky  
 Účelem této funkce je, aby rozhraní IDE získalo parametry `lpProjName` a `lpAuxProjPath` . Jakmile se modul plug-in správy zdrojových kódů vyzve uživatele k zadání těchto informací, předá tyto dva řetězce zpět do integrovaného vývojového prostředí (IDE). Rozhraní IDE tyto řetězce uchovává ve svém souboru řešení a předá je do [SccOpenProject](../extensibility/sccopenproject-function.md) vždy, když uživatel otevře tento projekt. Tyto řetězce umožňují modulu plug-in sledovat informace přidružené k projektu.  
  
 Při prvním volání funkce `lpAuxProjPath` je nastavena na prázdný řetězec. `lProjName` může být také prázdná nebo může obsahovat název projektu IDE, který modul plug-in správy zdrojového kódu může použít nebo ignorovat. Když funkce úspěšně vrátí, modul plug-in vrátí dva odpovídající řetězce. Rozhraní IDE neprovádí žádné předpoklady pro tyto řetězce, nebude je používat a neumožní uživateli je upravovat. Pokud uživatel chce změnit nastavení, IDE bude volat `SccGetProjPath` znovu a předává stejné hodnoty, které obdržel předchozí čas. Díky tomu má modul plug-in úplnou kontrolu nad těmito dvěma řetězci.  
  
 V případě `lpUser` rozhraní IDE může předat uživatelské jméno nebo může jednoduše předat ukazatel na prázdný řetězec. Pokud je uživatelské jméno, modul plug-in správy zdrojových kódů by ho měl používat jako výchozí. Pokud se ale žádný název nepředali nebo pokud se přihlašovací jméno nezdařilo s daným názvem, modul plug-in by měl uživateli požádat o přihlášení a předat ho zpátky v `lpUser` případě, že obdrží platné přihlašovací jméno. Vzhledem k tomu, že modul plug-in může tento řetězec změnit, rozhraní IDE vždy přidělí velikost vyrovnávací paměti ( `SCC_USER_LEN` + 1).  
  
> [!NOTE]
> První akce, kterou prostředí IDE provede, může být voláním `SccOpenProject` funkce nebo `SccGetProjPath` funkce. Proto oba mají stejný `lpUser` parametr, který umožňuje modulu plug-in správy zdrojových kódů přihlašovat uživatele v čase. I v případě, že návrat z funkce indikuje selhání, modul plug-in musí vyplnit tento řetězec platným přihlašovacím jménem.  
  
 `lpLocalPath` je adresář, do kterého uživatel udržuje projekt. Může to být prázdný řetězec. Pokud není aktuálně definován žádný adresář (jako v případě, že se uživatel pokouší stáhnout projekt ze systému správy zdrojů) a pokud `bAllowChangePath` je `TRUE` , modul plug-in správy zdrojových kódů může uživatele vyzvat ke vstupu nebo použít jinou metodu k umístění vlastního řetězce do `lpLocalPath` . Pokud `bAllowChangePath` má `FALSE` parametr hodnotu, nesmí modul plug-in změnit řetězec, protože uživatel již v zadaném adresáři pracuje.  
  
 Pokud uživatel vytvoří nový projekt, který má být umístěn pod správou zdrojových kódů, modul plug-in správy zdrojových kódů nemusí ve chvíli vytvořit v systému správy zdrojového kódu v době `SccGetProjPath` volání. Místo toho předá řetězec spolu s nenulovou hodnotou pro `pbNew` , což značí, že projekt bude vytvořen v systému správy zdrojového kódu.  
  
 Například pokud uživatel v průvodci **vytvořením projektu** v aplikaci Visual Studio přidá svůj projekt do správy zdrojových kódů, aplikace Visual Studio tuto funkci volá a modul plug-in určí, zda je v systému správy zdrojů možné vytvořit nový projekt, který bude obsahovat projekt sady Visual Studio. Pokud uživatel klikne na **Zrušit** před dokončením průvodce, projekt se nikdy nevytvoří. Pokud uživatel klikne na **tlačítko OK**, volání `SccOpenProject` sady Visual Studio, předání do `SCC_OPT_CREATEIFNEW` a projekt se správou zdrojového kódu se vytvoří v daném čase.  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
