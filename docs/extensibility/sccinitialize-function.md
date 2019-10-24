---
title: Funkce SccInitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 552ec06a4eabf55872358fc8e5d731e47c1eb6ca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721187"
---
# <a name="sccinitialize-function"></a>SccInitialize – funkce
Tato funkce Inicializuje modul plug-in správy zdrojových kódů a poskytuje možnosti a omezení integrovaného vývojového prostředí (IDE).

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

pro Modul plug-in správy zdrojových kódů může umístit ukazatel na svou kontextovou strukturu.

 `hWnd`

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 `lpCallerName`

pro Název programu, který volá modul plug-in správy zdrojového kódu.

 `lpSccName`

[in, out] Vyrovnávací paměť, kde modul plug-in správy zdrojových kódů vloží svůj vlastní název (nepřekračuje `SCC_NAME_LEN`).

 `lpSccCaps`

mimo Vrátí příznaky schopností modulu plug-in správy zdrojových kódů.

 `lpAuxPathLabel`

[in, out] Vyrovnávací paměť, kde modul plug-in správy zdrojových kódů vloží řetězec, který popisuje parametr `lpAuxProjPath` vrácený [SccOpenProject](../extensibility/sccopenproject-function.md) a [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (nesmí přesáhnout `SCC_AUXLABEL_LEN`).

 `pnCheckoutCommentLen`

mimo Vrátí maximální přípustnou délku komentáře k rezervaci.

 `pnCommentLen`

mimo Vrátí maximální přípustnou délku pro jiné komentáře.

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Inicializace správy zdrojového kódu byla úspěšná.|
|SCC_E_INITIALIZEFAILED|Systém nelze inicializovat.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení zadané operace.|
|SCC_E_NONSPECFICERROR|Nespecifická chyba; systém správy zdrojového kódu nebyl inicializován.|

## <a name="remarks"></a>Poznámky
 Rozhraní IDE tuto funkci volá, když poprvé načte modul plug-in správy zdrojových kódů. Umožňuje integrovanému vývojovém prostředí (IDE) předat modulu plug-in určité informace, jako je třeba název volajícího. Rozhraní IDE také vrátí určité informace, jako je maximální povolená délka pro komentáře a možnosti modulu plug-in.

 @No__t_0 odkazuje na ukazatel `NULL`. Modul plug-in správy zdrojových kódů může přidělit strukturu pro vlastní použití a Uložit ukazatel na tuto strukturu v `ppvContext`. Rozhraní IDE tento ukazatel předává každé jiné funkci VSSCI API, což umožňuje, aby modul plug-in měl k dispozici kontextové informace, aniž by bylo nutné použít globální úložiště a podporovat více instancí modulu plug-in. Tato struktura by měla být přidělena při volání [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 Parametry `lpCallerName` a `lpSccName` umožňují rozhraní IDE a modul plug-in správy zdrojového kódu k výměně názvů. Tyto názvy mohou být použity jednoduše k rozlišení mezi několika instancemi, nebo mohou být ve skutečnosti zobrazeny v nabídkách nebo dialogových oknech.

 Parametr `lpAuxPathLabel` je řetězec, který se používá jako komentář k identifikaci pomocné cesty projektu, který je uložen v souboru řešení a předaný do modulu plug-in správy zdrojových kódů ve volání [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] používá řetězec "projekt SourceSafe:"; jiné moduly plug-in správy zdrojového kódu by se měly zdržet používání tohoto konkrétního řetězce.

 Parametr `lpSccCaps` přiřadí modulu plug-in správy zdrojových kódů místo pro uložení bitflags označujících schopnosti modulu plug-in. (Úplný seznam funkcí bitflags najdete v tématu [příznaky schopností](../extensibility/capability-flags.md)). Pokud například modul plug-in plánuje zápis výsledků do funkce zpětného volání poskytnutého volajícím, modul plug-in nastaví SCC_CAP_TEXTOUT bit schopností. To by mohlo signalizovat, že rozhraní IDE vytvoří okno pro výsledky správy verzí.

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Příznaky funkcí](../extensibility/capability-flags.md)