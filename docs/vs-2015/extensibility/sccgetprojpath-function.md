---
title: Sccgetprojpath – funkce | Dokumentace Microsoftu
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
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 978316cd9c953217a3e59a7ecd1b047cab12734b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752596"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce se zobrazí výzva pro cestu k projektu, což je řetězec, který má smysl pouze na modul plug-in správy zdrojového kódu. Je volána, když se uživatel:  
  
-   Vytvoření nového projektu  
  
-   Přidat existující projekt do správy verzí  
  
-   Pokouším se najít existující projekt ovládacího prvku verze  
  
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
 [in] Struktura kontext modulu plug-in zdroje ovládacího prvku.  
  
 hWnd  
 [in] Popisovač okna integrovaného vývojového prostředí, které modul plug-in správy zdrojového kódu můžete použít jako nadřazený pro všechna dialogová okna, které poskytuje.  
  
 lpUser  
 [out v] Uživatelské jméno (nesmí přesáhnout SCC_USER_SIZE, včetně ukončovacího znaku NULL)  
  
 lpProjName  
 [out v] Název projektu IDE, pracovní prostor projektu nebo souboru pravidel (nesmí přesáhnout SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
 lpLocalPath  
 [out v] Cesta pracovního projektu. Pokud `bAllowChangePath` je `TRUE`, modul plug-in správy zdrojového kódu můžete upravit tento řetězec (nesmí přesáhnout _MAX_PATH, včetně ukončovacího znaku null).  
  
 lpAuxProjPath  
 [out v] Vyrovnávací paměť pro vrácený projektu k cestě (nesmí přesáhnout SCC_PRJPATH_SIZE, včetně ukončovacího znaku NULL).  
  
 bAllowChangePath  
 [in] Pokud je to `TRUE`, modul plug-in správy zdrojového kódu můžete k zadání a upravovat `lpLocalPath` řetězec.  
  
 pbNew  
 [out v] Hodnota v označuje, zda chcete-li vytvořit nový projekt. Vrácená hodnota označuje úspěch vytvoření projektu:  
  
|příchozí|interpretace|  
|--------------|--------------------|  
|HODNOTA TRUE|Uživatel může vytvořit nový projekt.|  
|FALSE|Uživatele nelze vytvořit nový projekt.|  
  
|Odchozí|interpretace|  
|--------------|--------------------|  
|HODNOTA TRUE|Nový projekt byl vytvořen.|  
|FALSE|Je vybraný existující projekt.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Projekt byl úspěšně vytvořen nebo načten.|  
|SCC_I_OPERATIONCANCELED|Operace byla zrušena.|  
|SCC_E_ACCESSFAILURE|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize.|  
|SCC_E_CONNECTIONFAILURE|Došlo k pokusu o připojení k systému správy zdrojového kódu.|  
|SCC_E_NONSPECIFICERROR|Došlo k nespecifikované chybě.|  
  
## <a name="remarks"></a>Poznámky  
 Účelem této funkce je pro rozhraní IDE k získání parametry `lpProjName` a `lpAuxProjPath`. Po modul plug-in správy zdrojového kódu se zobrazí výzva pro tyto informace, předá tyto dva řetězce zpět do integrovaného vývojového prostředí. Rozhraní IDE uchovává tyto řetězce v souboru řešení a předává je do [sccopenproject –](../extensibility/sccopenproject-function.md) vždy, když uživatel otevře tento projekt. Tyto řetězce povolte modul plug-in pro sledování informací, které jsou spojené s projektem.  
  
 Při prvním volání funkce `lpAuxProjPath` je nastaven na prázdný řetězec. `lProjName` může také být prázdný, nebo může obsahovat název projektu integrovaného vývojového prostředí, které modul plug-in správy zdrojového kódu může použít nebo ignorovat. Po návratu funkce úspěšně, modul plug-in vrátí dva řetězce odpovídající. Integrovaného vývojového prostředí nepředpokládá, o tyto řetězce, nebudeme je používat a neumožňuje uživateli je upravovat. Pokud chce uživatel změnit nastavení, bude volat rozhraní IDE `SccGetProjPath` znovu, předanou ve stejné hodnoty se v minulosti obdržel předchozí čas. To poskytuje modul plug-in úplnou kontrolu nad tyto dva řetězce.  
  
 Pro `lpUser`, rozhraní IDE může předat uživatelské jméno, nebo ho jednoduše předat ukazatel na prázdný řetězec. Pokud je uživatelské jméno, modul plug-in správy zdrojového kódu by měl používat jako výchozí. Ale pokud nebyl předán žádný název, nebo pokud se přihlášení nezdařilo se zadaným názvem, modul plug-in by měl požádat uživatele o přihlášení a předejte název zpět v `lpUser` při přijetí platné přihlašovací údaje. Vzhledem k tomu, že modul plug-in mohou změnit tento řetězec, rozhraní IDE se vždy přidělí vyrovnávací paměť o velikosti (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  První akci prováděnou v integrovaném vývojovém prostředí může být volání na buď `SccOpenProject` funkce nebo `SccGetProjPath` funkce. Proto obou z nich mít identická `lpUser` parametr, který umožňuje přihlásit uživatele v době buď plug-in správy zdrojových kódů. I v případě, že vrácení z funkce naznačuje chybu, musí modulu plug-in zadejte tento řetězec s platným přihlašovacím jménem.  
  
 `lpLocalPath` je adresář, ve kterém balancovat projektu. Může být prázdný řetězec. Pokud není žádný adresář aktuálně definován (třeba v případě uživatelů, pokus o stažení projektu ze správy zdrojového kódu) a pokud `bAllowChangePath` je `TRUE`, modul plug-in správy zdrojového kódu můžete požádat uživatele o vstup nebo některé jiné metody použijte k nastavení jeho vlastní řetězec do `lpLocalPath`. Pokud `bAllowChangePath` je `FALSE`, modul plug-in neměli měnit řetězec, protože uživatel již pracuje v zadaném adresáři.  
  
 Pokud uživatel vytvoří nový projekt, které budou umístěny pod správou zdrojových kódů, modul plug-in správy zdrojového kódu nemusí ve skutečnosti jej vytvořit v systému správy zdrojového kódu v době `SccGetProjPath` je volána. Místo toho předává zpět řetězec spolu s nenulovou hodnotu pro `pbNew`, která udává, že projekt bude vytvořen v systému správy zdrojového kódu.  
  
 Například, pokud uživatel **nový projekt** průvodce v sadě Visual Studio přidá jeho projekt do správy zdrojových kódů, tuto funkci volá, Visual Studio a modulu plug-in Určuje, zda je možné vytvořit nový projekt v systému správy zdrojového kódu pro obsahují projekt sady Visual Studio. Pokud uživatel klikne **zrušit** před dokončením průvodce, nikdy vytvoření projektu. Pokud uživatel klikne **OK**, Visual Studio volá `SccOpenProject`a předejte `SCC_OPT_CREATEIFNEW`, a vytvoření projektu spravovanými zdroji v daném čase.  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu Plug-in zdroje ovládacího prvku](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)

