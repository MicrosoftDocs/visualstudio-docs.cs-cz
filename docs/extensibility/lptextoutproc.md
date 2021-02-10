---
title: LPTEXTOUTPROC | Microsoft Docs
description: Seznamte se s ukazatelem na funkci LPTEXTOUTPROC. Rozhraní IDE sady Visual Studio implementuje funkci pro zobrazení chyb a stavu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef05b65b1a018772f4354062aa1be285c40b0d90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952171"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Když uživatel spustí operaci správy zdrojového kódu z integrovaného vývojového prostředí (IDE), modul plug-in správy zdrojových kódů může chtít předat chybové nebo stavové zprávy týkající se operace. Modul plug-in může pro tento účel zobrazit vlastní okna zpráv. Pro lepší integraci však modul plug-in může předat řetězce rozhraní IDE, které je pak zobrazí v nativním způsobu zobrazení informací o stavu. Mechanismus pro toto je ukazatel na `LPTEXTOUTPROC` funkci. Rozhraní IDE implementuje tuto funkci (podrobnější popis najdete níže) pro zobrazení chyb a stavů.

Rozhraní IDE předá do modulu plug-in správy zdrojových kódů ukazatel na tuto funkci, jako `lpTextOutProc` parametr, při volání metody [SccOpenProject](../extensibility/sccopenproject-function.md). Během operace SCC, například uprostřed volání [SccGet](../extensibility/sccget-function.md) obsahujícího mnoho souborů, modul plug-in může volat `LPTEXTOUTPROC` funkci a pravidelně předávat řetězce k zobrazení. Rozhraní IDE může zobrazit tyto řetězce ve stavovém řádku, v okně výstupu nebo v samostatném okně se zprávou. Volitelně může IDE zobrazit určité zprávy s tlačítkem **Storno** . To umožňuje uživateli zrušit operaci a rozhraní IDE poskytuje možnost předat tyto informace zpět do modulu plug-in.

## <a name="signature"></a>Podpis
 Výstupní funkce IDE má následující signaturu:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parametry

display_string

Textový řetězec, který se má zobrazit Tento řetězec by neměl být ukončen znakem CR nebo řádkem.

mesg_type

Typ zprávy Následující tabulka uvádí podporované hodnoty pro tento parametr.

|Hodnota|Popis|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Zpráva se považuje za informace, upozornění nebo chybu.|
|`SCC_MSG_STATUS`|Zpráva zobrazuje stav a je možné ji zobrazit ve stavovém řádku.|
|`SCC_MSG_DOCANCEL`|Odesílá se bez řetězce zpráv.|
|`SCC_MSG_STARTCANCEL`|Začíná zobrazovat tlačítko **Storno** .|
|`SCC_MSG_STOPCANCEL`|Zastaví zobrazení tlačítka **Storno** .|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Požádá IDE o zrušení operace na pozadí: IDE vrátí `SCC_MSG_RTN_CANCEL` , pokud operace byla zrušena. v opačném případě vrátí `SCC_MSG_RTN_OK` . `display_string`Parametr je přetypování jako struktura [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) , která je poskytována modulem plug-in správy zdrojových kódů.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Oznamuje rozhraní IDE o souboru před jeho načtením ze správy verzí. `display_string`Parametr je přetypování jako struktura [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) , která je poskytována modulem plug-in správy zdrojových kódů.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Instruuje rozhraní IDE o souboru po jeho načtení ze správy verzí. `display_string`Parametr je přetypování jako struktura [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) , která je poskytována modulem plug-in správy zdrojových kódů.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Oznamuje rozhraní IDE aktuálního stavu operace na pozadí. `display_string`Parametr je přetypování jako struktura [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) , která je poskytována modulem plug-in správy zdrojových kódů.|

## <a name="return-value"></a>Vrácená hodnota

|Hodnota|Popis|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Byl zobrazen řetězec nebo operace byla úspěšně dokončena.|
|SCC_MSG_RTN_CANCEL|Uživatel chce operaci zrušit.|

## <a name="example"></a>Příklad
 Předpokládejme, že rozhraní IDE volá [SccGet](../extensibility/sccget-function.md) a dvacet názvů souborů. Modul plug-in správy zdrojových kódů chce zabránit zrušení operace uprostřed souboru Get. Po získání každého souboru, jeho volání `lpTextOutProc` , předání stavových informací v jednotlivých souborech a odeslání `SCC_MSG_DOCANCEL` zprávy, pokud nemá stav sestav. Pokud však modul plug-in obdrží návratovou hodnotu `SCC_MSG_RTN_CANCEL` z rozhraní IDE, okamžitě zruší operaci get, takže nebudou načteny žádné další soubory.

## <a name="structures"></a>Struktury

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Tato struktura se posílá se `SCC_MSG_BACKGROUND_IS_CANCELLED` zprávou. Slouží ke sdělování ID operace pozadí, která byla zrušena.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Tato struktura se posílá se `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` zprávou. Slouží ke sdělování názvu souboru, který se má načíst, a ID operace na pozadí, která provádí načítání.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Tato struktura se posílá se `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` zprávou. Slouží ke sdělování výsledku načtení zadaného souboru i ID operace na pozadí, která se načítají. Podívejte se na vrácené hodnoty pro [SccGet](../extensibility/sccget-function.md) pro to, co může být uvedeno v důsledku.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Tato struktura se posílá se `SCC_MSG_BACKGROUND_ON_MESSAGE` zprávou. Slouží ke komunikaci s aktuálním stavem operace na pozadí. Stav je vyjádřen jako řetězec, který má být zobrazen rozhraním IDE, a `bIsError` označuje závažnost zprávy ( `TRUE` pro chybovou zprávu, `FALSE` upozornění nebo informativní zpráva). Je také zadáno ID operace na pozadí, která odesílá stav.

## <a name="code-example"></a>Příklad kódu
 Zde je stručný příklad volání `LPTEXTOUTPROC` pro odeslání `SCC_MSG_BACKGROUND_ON_MESSAGE` zprávy, který ukazuje, jak přetypování struktury pro volání.

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
- [Funkce zpětného volání implementované rozhraním IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
