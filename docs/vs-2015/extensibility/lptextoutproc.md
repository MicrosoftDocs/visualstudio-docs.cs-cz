---
title: LPTEXTOUTPROC | Dokumentace Microsoftu
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
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28a48c0d2dbc89295d6c1f8e900ce6219e2c9313
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750863"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když uživatel provede operaci správy zdrojových kódů v rámci integrovaného vývojového prostředí (IDE), modul plug-in správy zdrojového kódu může být vhodné k předání chyba nebo stav zprávy týkající se operace. Modul plug-in zobrazíte jeho vlastní okna se zprávou pro tento účel. Ale pro další bezproblémovou integraci, modul plug-in můžete předat řetězce integrovaného vývojového prostředí, které zobrazí je v jeho nativní způsob zobrazení informací o stavu. Je mechanismus pro to, `LPTEXTOUTPROC` ukazatel na funkci. Rozhraní IDE implementuje tuto funkci (podrobněji popsaný níže) pro zobrazení stavů a chyb.  
  
 Rozhraní IDE předává do správy zdrojového kódu modulu plug-in ukazatele na funkci na tuto funkci, jako `lpTextOutProc` parametru při volání [sccopenproject –](../extensibility/sccopenproject-function.md). Během operace SCC, třeba uprostřed volání [sccget –](../extensibility/sccget-function.md) zahrnující mnoho souborů, modul plug-in můžete volat `LPTEXTOUTPROC` funkce pravidelně předávání řetězce k zobrazení. Rozhraní IDE se může zobrazit tyto řetězce na stavovém řádku v okně výstupu nebo v samostatném okně, podle potřeby. Volitelně může nebude moci zobrazit některé zprávy s integrovaného vývojového prostředí **zrušit** tlačítko. To umožňuje uživateli zrušit operaci a integrované vývojové prostředí nabízí možnost předávání zpátky do modulu plug-in tyto informace.  
  
## <a name="signature"></a>podpis  
 Rozhraní IDE výstup funkce má následující podpis:  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Parametry  
 display_string  
 Textový řetězec k zobrazení. Tento řetězec by neměl být ukončen direktivou zalomení řádku návratový nebo odřádkování.  
  
 mesg_type  
 Typ zprávy. Následující tabulka uvádí podporované hodnoty pro tento parametr.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Zpráva se považuje za informace, varování nebo chyba.|  
|`SCC_MSG_STATUS`|Zpráva se zobrazuje stav a mohou být zobrazeny ve stavovém řádku.|  
|`SCC_MSG_DOCANCEL`|Odeslat s řetězec žádné zprávy.|  
|`SCC_MSG_STARTCANCEL`|Začne, zobrazení **zrušit** tlačítko.|  
|`SCC_MSG_STOPCANCEL`|Zastaví zobrazování **zrušit** tlačítko.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Požádá integrovaného vývojového prostředí, pokud je operace na pozadí zruší: IDE vrátí `SCC_MSG_RTN_CANCEL` Pokud byla operace zrušena; v opačném případě vrátí `SCC_MSG_RTN_OK`. `display_string` Parametr je typovaná jako [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) struktury, který je poskytnut pomocí modulu plug-in správy zdrojového kódu.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Poskytuje integrované vývojové prostředí o souboru před načtením ze správy verzí. `display_string` Parametr je typovaná jako [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) struktury, který je poskytnut pomocí modulu plug-in správy zdrojového kódu.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Poskytuje integrované vývojové prostředí o souboru po jeho načtení ze správy verzí. `display_string` Parametr je typovaná jako [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) struktury, který je poskytnut pomocí modulu plug-in správy zdrojového kódu.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Instruuje integrované vývojové prostředí aktuálního stavu operaci na pozadí. `display_string` Parametr je typovaná jako [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) struktury, který je poskytnut pomocí modulu plug-in správy zdrojového kódu.|  
  
## <a name="return-value"></a>Návratová hodnota  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Řetězec se zobrazí nebo operace byla úspěšně dokončena.|  
|SCC_MSG_RTN_CANCEL|Uživatel chce, aby na zrušení operace.|  
  
## <a name="example"></a>Příklad  
 Předpokládejme, že volání rozhraní IDE [sccget –](../extensibility/sccget-function.md) s dvacet názvy souborů. Modul plug-in správy zdrojového kódu se chce zabránit zrušení operace uprostřed souboru get. Po získání každého souboru, volá `lpTextOutProc`předáním informace o stavu u všech souborů a odešle `SCC_MSG_DOCANCEL` zprávy, pokud nemá stav do sestavy. Pokud v každém okamžiku modul plug-in přijímá návratovou hodnotu `SCC_MSG_RTN_CANCEL` z rozhraní IDE, zruší operaci get okamžitě, tak, že jsou načteny žádné další soubory.  
  
## <a name="structures"></a>Struktury  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Tato struktura se neposílají `SCC_MSG_BACKGROUND_IS_CANCELLED` zprávy. Používá se pro komunikaci ID operace na pozadí, která byla zrušena.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Tato struktura se neposílají `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` zprávy. Používá se pro komunikaci název souboru, o který se má načíst a ID operace na pozadí, který provádí načítání.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Tato struktura se neposílají `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` zprávy. Používá se pro komunikaci výsledek načtení souboru zadané jak ID operace na pozadí, který nebyl načítání. Zobrazit návratové hodnoty pro [sccget –](../extensibility/sccget-function.md) pro co mohou být zadány ve výsledku.  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Tato struktura se neposílají `SCC_MSG_BACKGROUND_ON_MESSAGE` zprávy. Používá se pro komunikaci aktuální stav operaci na pozadí. Stav je vyjádřena jako řetězec, který se má zobrazovat integrovaném vývojovém prostředí a `bIsError` označuje závažnost zprávy (`TRUE` pro chybovou zprávu; `FALSE` upozornění nebo informační zpráva). ID operace na pozadí odesílání stav je také zadána.  
  
## <a name="code-example"></a>Příklad kódu  
 Tady je stručný příkladem volání `LPTEXTOUTPROC` k odeslání `SCC_MSG_BACKGROUND_ON_MESSAGE` zprávu, která zobrazuje postup přetypování struktura volání.  
  
```cpp#  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Funkce zpětného volání implementované integrovaným vývojovým prostředím](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)

