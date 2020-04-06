---
title: LPTEXTOUTPROC | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702792"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Když uživatel provede operaci správy zdrojového kódu z uvnitř integrovaného vývojového prostředí (IDE), modul plug-in správy zdrojového kódu může chtít sdělit chybové nebo stavové zprávy týkající se operace. Modul plug-in může pro tento účel zobrazit vlastní okna se zprávami. Pro bezproblémovější integraci však modul plug-in může předávat řetězce do prostředí IDE, které je pak zobrazí v nativním způsobu zobrazení informací o stavu. Mechanismus pro toto je ukazatel `LPTEXTOUTPROC` funkce. Rozhraní IDE implementuje tuto funkci (podrobněji popsané níže) pro zobrazení chyby a stavu.

IDE předá modul plug-in řízení zdrojového kódu ukazatel `lpTextOutProc` funkce na tuto funkci, jako parametr, při volání [SccOpenProject](../extensibility/sccopenproject-function.md). Během operace SCC, například uprostřed volání [SccGet](../extensibility/sccget-function.md) zahrnující mnoho souborů, modul plug-in `LPTEXTOUTPROC` můžete volat funkci, pravidelně předávání řetězců pro zobrazení. IDE může zobrazit tyto řetězce na stavovém řádku, ve výstupním okně nebo v samostatném okně se zprávou podle potřeby. Volitelně ide může být schopen zobrazit určité zprávy s **tlačítko Storno.** To umožňuje uživateli zrušit operaci a poskytuje ide možnost předat tyto informace zpět do modulu plug-in.

## <a name="signature"></a>Podpis
 Výstupní funkce ide má následující podpis:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parametry

display_string

Textový řetězec, který se má zobrazit. Tento řetězec by neměl být ukončen návratem vozíku nebo posuvem řádků.

mesg_type

Typ zprávy. V následující tabulce jsou uvedeny podporované hodnoty pro tento parametr.

|Hodnota|Popis|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Zpráva je považována za informace, upozornění nebo chyba.|
|`SCC_MSG_STATUS`|Zpráva zobrazuje stav a může být zobrazena na stavovém řádku.|
|`SCC_MSG_DOCANCEL`|Odesláno bez řetězce zpráv.|
|`SCC_MSG_STARTCANCEL`|Začne zobrazovat tlačítko **Storno.**|
|`SCC_MSG_STOPCANCEL`|Zastaví zobrazení tlačítka **Storno.**|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Zeptá ide, pokud má být zrušena operace `SCC_MSG_RTN_CANCEL` na pozadí: IDE vrátí, pokud operace byla zrušena; v opačném `SCC_MSG_RTN_OK`případě vrátí . Parametr `display_string` je přetypován jako struktura [SccMsgDataIsCancelled,](#LinkSccMsgDataIsCancelled) která je dodávána modulem plug-in správy zdrojového kódu.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Informuje ide o souboru před jeho načtením ze správy verzí. Parametr `display_string` je přetypován jako struktura [SccMsgDataOnBeforeGetFile,](#LinkSccMsgDataOnBeforeGetFile) která je dodávána modulem plug-in správy zdrojového kódu.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Informuje ide o souboru poté, co byl načten ze správy verzí. Parametr `display_string` je přetypován jako struktura [SccMsgDataOnAfterGetFile,](#LinkSccMsgDataOnAfterGetFile) která je dodávána modulem plug-in správy zdrojového kódu.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Informuje ide aktuální stav operace na pozadí. Parametr `display_string` je přetypován jako struktura [SccMsgDataOnMessage,](#LinkSccMsgDataOnMessage) která je dodávána modulem plug-in správy zdrojového kódu.|

## <a name="return-value"></a>Návratová hodnota

|Hodnota|Popis|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Řetězec byl zobrazen nebo operace byla úspěšně dokončena.|
|SCC_MSG_RTN_CANCEL|Uživatel chce operaci zrušit.|

## <a name="example"></a>Příklad
 Předpokládejme, že ide volá [SccGet](../extensibility/sccget-function.md) s dvaceti názvy souborů. Modul plug-in správy zdrojového kódu chce zabránit zrušení operace uprostřed souboru get. Po získání každého souboru zavolá `lpTextOutProc`, předá informace o `SCC_MSG_DOCANCEL` stavu každého souboru a odešle zprávu, pokud nemá žádný stav k hlášení. Pokud kdykoli modul plug-in obdrží vrácenou `SCC_MSG_RTN_CANCEL` hodnotu z ide, okamžitě zruší operaci get, takže se nenačtou žádné další soubory.

## <a name="structures"></a>Struktury

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsZrušeno

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Tato struktura je `SCC_MSG_BACKGROUND_IS_CANCELLED` odeslána se zprávou. Používá se ke komunikaci ID operace na pozadí, která byla zrušena.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Tato struktura je `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` odeslána se zprávou. Používá se ke sdělování názvu souboru, který má být načten, a ID operace na pozadí, která provádí načítání.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Tato struktura je `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` odeslána se zprávou. Používá se ke komunikaci výsledek načítání zadaného souboru, jakož i ID operace na pozadí, který provedl načítání. Viz vrácené hodnoty pro [SccGet](../extensibility/sccget-function.md) pro co může být poskytnuta jako výsledek.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Tato struktura je `SCC_MSG_BACKGROUND_ON_MESSAGE` odeslána se zprávou. Používá se ke komunikaci aktuálního stavu operace na pozadí. Stav je vyjádřen jako řetězec, který má být zobrazen `bIsError` rozhraním IDE,`TRUE` a označuje závažnost zprávy ( pro chybovou zprávu; `FALSE` upozornění nebo informační zprávu). ID operace na pozadí odesílání stavu je také uveden.

## <a name="code-example"></a>Příklad kódu
 Zde je stručný příklad `LPTEXTOUTPROC` volání `SCC_MSG_BACKGROUND_ON_MESSAGE` odeslat zprávu, ukazuje, jak obsazení struktury pro volání.

```cpp
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
- [Funkce zpětného volání implementované ide](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
