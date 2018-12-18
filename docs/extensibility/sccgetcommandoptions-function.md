---
title: Sccgetcommandoptions – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 846d1667e1f990a5580520353be46ede76644145
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923742"
---
# <a name="sccgetcommandoptions-function"></a>Sccgetcommandoptions – funkce
Tato funkce se zobrazí výzva pro rozšířené možnosti pro daný příkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontext modulu plug-in zdroje ovládacího prvku.  
  
 hWnd  
 [in] Popisovač okna integrovaného vývojového prostředí, které modul plug-in správy zdrojového kódu můžete použít jako nadřazený pro všechna dialogová okna, které poskytuje.  
  
 rozhraní iCommand  
 [in] Příkaz, pro které jsou požadovány v upřesňující možnosti (naleznete v tématu [příkaz kódu](../extensibility/command-code-enumerator.md) možných hodnot).  
  
 ppvOptions  
 [in] Struktura možnost (může být také `NULL`).  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Úspěch.|  
|SCC_I_ADV_SUPPORT|Modul plug-in správy zdrojového kódu podporuje rozšířené možnosti pro příkaz.|  
|SCC_I_OPERATIONCANCELED|Uživatel zrušil zdrojového ovládacího prvku plug-in **možnosti** dialogové okno.|  
|SCC_E_OPTNOTSUPPORTED|Modul plug-in správy zdrojového kódu nepodporuje tuto operaci.|  
|SCC_E_ISCHECKEDOUT|Nelze provést tuto operaci u souboru, který je právě rezervována.|  
|SCC_E_ACCESSFAILURE|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize. Doporučuje se zkuste to znovu.|  
|SCC_E_NONSPECIFICERROR|K nespecifikované chybě.|  
  
## <a name="remarks"></a>Poznámky  
 Integrované vývojové prostředí volá tuto funkci s prvním `ppvOptions` = `NULL` k určení, jestli plug-in správy zdrojových kódů podporuje funkce Rozšířené možnosti pro zadaný příkaz. Pokud modul plug-in nepodporuje funkci pro tento příkaz, integrovaném vývojovém prostředí volá tuto funkci znovu když uživatel požádá o rozšířené možnosti (obvykle implementovány jako **Upřesnit** tlačítko v dialogovém okně) a poskytuje NENULOVÝ ukazatel pro `ppvOptions` , která odkazuje na `NULL` ukazatele. Modul plug-in ukládá všechny rozšířené možnosti určeného uživatele v soukromé struktury a vrací ukazatel na danou strukturu v `ppvOptions`. Tato struktura je pak předán všechny ostatní funkce rozhraní API modulu Plug-in zdroje ovládacího prvku, které je potřeba vědět o, včetně následných volání `SccGetCommandOptions` funkce.  
  
 Příklad může pomoci objasnit této situaci.  
  
 Uživatel klikne **získat** příkazu a rozhraní IDE zobrazí **získat** dialogové okno. Volání rozhraní IDE `SccGetCommandOptions` s funkcí `iCommand` nastavena na `SCC_COMMAND_GET` a `ppvOptions` nastavena na `NULL`. To je interpretován jako dotaz modul plug-in správy zdrojového kódu, "Máte všechny rozšířené možnosti pro tento příkaz?" Pokud modul plug-in vrátí `SCC_I_ADV_SUPPORT`, rozhraní IDE zobrazí **Upřesnit** tlačítko v jeho **získat** dialogové okno.  
  
 Při prvním uživatel klikne **Upřesnit** tlačítko, rozhraní IDE znovu volá `SccGetCommandOptions` fungovala, tentokrát s non -`NULL``ppvOptions` , která odkazuje na `NULL` ukazatel. Modul plug-in zobrazí jeho vlastní **získat možnosti** dialogovém okně se zobrazí výzva pro informace, vloží tyto informace do vlastní struktury a vrací ukazatel na danou strukturu v `ppvOptions`.  
  
 Pokud uživatel klikne **Upřesnit** znovu v dialogovém okně stejné volání rozhraní IDE `SccGetCommandOptions` funkce znovu beze změny `ppvOptions`tak, aby struktura se předá zpět do modulu plug-in. To umožňuje modulu plug-in znovu inicializovat dialogové okno pro hodnoty, které uživatel dříve nastavené. Modul plug-in upraví struktury na místě před vrácením.  
  
 A konečně, když uživatel klikne na tlačítko **OK** v rozhraní IDE **získat** dialogové okno, volání integrované vývojové prostředí [sccget –](../extensibility/sccget-function.md), předejte strukturu vrácené v `ppvOptions` , která obsahuje Rozšířené možnosti.  
  
> [!NOTE]
>  Příkaz `SCC_COMMAND_OPTIONS` se používá, když se zobrazí rozhraní IDE **možnosti** dialogové okno, které umožní uživateli nastavit předvolby, které řídí, jak integrace funguje. Pokud chce, aby modul plug-in správy zdrojového kódu slouží k poskytování své vlastní dialogové okno Předvolby, může zobrazit z **Upřesnit** tlačítko v dialogovém okně Předvolby rozhraní IDE. Modul plug-in je výhradně zodpovědná za získání a při zachování tyto informace; rozhraní IDE není používat ji nebo ji změňte.  
  
## <a name="see-also"></a>Viz také:  
 [Funkce modulu plug-in API zdrojového ovládacího prvku](../extensibility/source-control-plug-in-api-functions.md)   
 [Kód příkazu.](../extensibility/command-code-enumerator.md)