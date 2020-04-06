---
title: Funkce SccInitialize | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700630"
---
# <a name="sccinitialize-function"></a>SccInitialize – funkce
Tato funkce inicializuje modul plug-in-in-source řízení a poskytuje možnosti a omezení integrovaného vývojového prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>Parametry
 `ppvContext`

[v] Modul plug-in správy zdrojového kódu můžete umístit ukazatel na jeho strukturu kontextu zde.

 `hWnd`

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 `lpCallerName`

[v] Název programu, který volá modul plug-in správy zdrojového kódu.

 `lpSccName`

[dovnitř, ven] Vyrovnávací paměť, kde modul plug-in správy zdrojového `SCC_NAME_LEN`kódu umístí svůj vlastní název (nesmí překročit).

 `lpSccCaps`

[out] Vrátí příznaky schopností modulu plug-in správy zdrojového kódu.

 `lpAuxPathLabel`

[dovnitř, ven] Vyrovnávací paměť, kde modul plug-in správy zdrojového kódu vloží řetězec, `lpAuxProjPath` který popisuje parametr vrácený [SccOpenProject](../extensibility/sccopenproject-function.md) a [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (nesmí překročit). `SCC_AUXLABEL_LEN`

 `pnCheckoutCommentLen`

[out] Vrátí maximální přípustnou délku komentáře k pokladně.

 `pnCommentLen`

[out] Vrátí maximální přípustnou délku pro ostatní poznámky.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Inicializace správy zdrojového kódu byla úspěšná.|
|SCC_E_INITIALIZEFAILED|Systém nelze inicializovat.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provést zadanou operaci.|
|SCC_E_NONSPECFICERROR|Nespecifické selhání; zdrojový řídicí systém nebyl inicializován.|

## <a name="remarks"></a>Poznámky
 IDE volá tuto funkci při prvním načtení modulu plug-in správy zdrojového kódu. Umožňuje ide předat určité informace, jako je například jméno volajícího, do modulu plug-in. IDE také získá zpět určité informace, jako je například maximální povolená délka pro komentáře a možnosti modulu plug-in.

 Ukazuje `ppvContext` na `NULL` ukazatel. Modul plug-in správy zdrojového kódu může přidělit strukturu pro `ppvContext`vlastní použití a uložit ukazatel této struktury v . Rozhraní IDE předá tento ukazatel na všechny ostatní funkce rozhraní API VSSCI, což umožňuje modulu plug-in mít k dispozici informace o kontextu bez použití globálního úložiště a pro podporu více instancí modulu plug-in. Tato struktura by měla být přidělena při [sccUninitialize](../extensibility/sccuninitialize-function.md) je volána.

 `lpCallerName` Parametry `lpSccName` a umožňují rozhraní IDE a modul plug-in správy zdrojového kódu k výměně názvů. Tyto názvy mohou být použity pouze k rozlišení mezi více instancemi nebo se mohou skutečně objevit v nabídkách nebo dialogových oknech.

 Parametr `lpAuxPathLabel` je řetězec používaný jako komentář k identifikaci pomocné cesty projektu, která je uložena v souboru řešení a předána modulu plug-in správy zdrojového kódu ve volání [projektu SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]používá řetězec "SourceSafe Project:"; jiné moduly plug-in správy zdrojového kódu by se měly zdržet používání tohoto konkrétního řetězce.

 Parametr `lpSccCaps` poskytuje modul plug-in správy zdrojového kódu místo pro ukládání bitových příznaků označujících možnosti modulu plug-in. (Úplný seznam bitových příznaků schopností naleznete v tématu [Příznaky schopností](../extensibility/capability-flags.md)). Například pokud modul plug-in plánuje zapisovat výsledky do funkce zpětného volání poskytované volajícím, modul plug-in by nastavil bit schopnosti SCC_CAP_TEXTOUT. To by signál IDE vytvořit okno pro výsledky správy verzí.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Příznaky funkcí](../extensibility/capability-flags.md)
