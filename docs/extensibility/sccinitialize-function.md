---
description: Tato funkce inicializuje modul plug-in správy zdrojového kódu a poskytuje možnosti a omezení integrovaného vývojového prostředí (IDE).
title: SccInitialize – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 633e8909febd758df455a9375f735a93e3407c77
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902524"
---
# <a name="sccinitialize-function"></a>SccInitialize – funkce
Tato funkce inicializuje modul plug-in správy zdrojového kódu a poskytuje možnosti a omezení integrovaného vývojového prostředí (IDE).

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

[v] Modul plug-in správy zdrojového kódu může zde umístit ukazatel na jeho kontextovou strukturu.

 `hWnd`

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 `lpCallerName`

[v] Název programu, který volá modul plug-in správy zdrojového kódu.

 `lpSccName`

[in, out] Vyrovnávací paměť, kam modul plug-in správy zdrojového kódu zadá vlastní název (nesmí překročit `SCC_NAME_LEN` ).

 `lpSccCaps`

[out] Vrátí příznaky funkcí modulu plug-in správy zdrojového kódu.

 `lpAuxPathLabel`

[in, out] Vyrovnávací paměť, kam modul plug-in správy zdrojového kódu vložil řetězec popisující parametr vrácený `lpAuxProjPath` [projektem SccOpenProject](../extensibility/sccopenproject-function.md) a [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (nesmí překročit `SCC_AUXLABEL_LEN` ).

 `pnCheckoutCommentLen`

[out] Vrátí maximální povolenou délku komentáře k pokladně.

 `pnCommentLen`

[out] Vrátí maximální povolenou délku pro ostatní komentáře.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Inicializace správy zdrojového kódu byla úspěšná.|
|SCC_E_INITIALIZEFAILED|Systém se neinicializoval.|
|SCC_E_NOTAUTHORIZED|Uživatel nemůže provést zadanou operaci.|
|SCC_E_NONSPECFICERROR|Nespecikátní selhání; systém správy zdrojového kódu nebyl inicializován.|

## <a name="remarks"></a>Poznámky
 Integrované vývojové prostředí tuto funkci volá při prvním načtení modulu plug-in správy zdrojového kódu. Umožňuje integrovanému vývojovému prostředí (IDE) předávat do modulu plug-in určité informace, například jméno volajícího. Integrované vývojové prostředí (IDE) také získá zpět určité informace, jako je maximální povolená délka komentářů a možnosti modulu plug-in.

 Odkazuje `ppvContext` na `NULL` ukazatel. Modul plug-in správy zdrojového kódu může přidělit strukturu pro vlastní použití a uložit ukazatel na tuto strukturu v `ppvContext` . Integrované vývojové prostředí tento ukazatel předá každé jiné funkci rozhraní API VSSCI, což modulu plug-in umožní mít k dispozici kontextové informace, aniž by se uchýlly ke globálnímu úložišti a podporovaly více instancí modulu plug-in. Tato struktura by měla být zrušení přidělení při [volání SccUninitialize.](../extensibility/sccuninitialize-function.md)

 Parametry `lpCallerName` `lpSccName` a umožňují integrovanému vývojovému prostředí (IDE) a modulu plug-in správy zdrojového kódu vyměňovat si názvy. Tyto názvy se dají jednoduše použít k rozlišení mezi více instancemi nebo se dají ve skutečnosti zobrazit v nabídkách nebo dialogových oknech.

 Parametr je řetězec, který se používá jako komentář k identifikaci pomocné cesty k projektu, která je uložená v souboru řešení a předána modulu plug-in správy zdrojového kódu ve volání `lpAuxPathLabel` [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] používá řetězec "SourceSafe Project:"; Jiné moduly plug-in správy zdrojového kódu by neměly používat tento konkrétní řetězec.

 Parametr dává modulu plug-in správy zdrojového kódu místo pro ukládání bitflagů, které indikující `lpSccCaps` schopnosti modulu plug-in. (Úplný seznam funkcí bitflags najdete v tématu [Příznaky schopností](../extensibility/capability-flags.md)). Pokud například modul plug-in plánuje zapisovat výsledky do funkce zpětného volání poskytnuté volajícím, modul plug-in nastaví bit schopnosti SCC_CAP_TEXTOUT. To by signalizováno integrovaného vývojového prostředí k vytvoření okna pro výsledky řízení verzí.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Příznaky funkcí](../extensibility/capability-flags.md)
