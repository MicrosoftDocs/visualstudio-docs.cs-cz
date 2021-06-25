---
description: Tato funkce vrátí zpět předchozí operaci pokladny, čímž obnoví obsah vybraného souboru nebo souborů do stavu před pokladnou.
title: SccUncheckout – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3a382a112b5a11acc36c52735c949ebef71052ec
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904084"
---
# <a name="sccuncheckout-function"></a>SccUncheckout – funkce
Tato funkce vrátí zpět předchozí operaci pokladny, čímž obnoví obsah vybraného souboru nebo souborů do stavu před pokladnou. Všechny změny provedené v souboru, protože se při pokladně ztratí.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 nFiles

[v] Počet souborů zadaných v `lpFileNames` poli

 lpFileNames

[v] Pole plně kvalifikovaných názvů místních cest souborů, pro které se má vrátit zpět k pokladně.

 Možnosti fOptions

[v] Příznaky příkazů (nepouží se)

 pvOptions

[v] Možnosti modulu plug-in správy zdrojového kódu

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Vrácení zpět k pokladně bylo úspěšné.|
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není pod svládem zdrojového kódu.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit. Doporučuje se opakování.|
|SCC_E_NONSPECIFICERROR|Nespecikátní selhání. Vrácení zpět k pokladně nebylo úspěšné.|
|SCC_E_NOTCHECKEDOUT|Uživatel nemá soubor rezervován.|
|SCC_E_NOTAUTHORIZED|Uživatel nemůže tuto operaci provést.|
|SCC_E_PROJNOTOPEN|Projekt nebyl otevřen ze správy zdrojového kódu.|
|SCC_I_OPERATIONCANCELED|Operace se před dokončením zrušila.|

## <a name="remarks"></a>Poznámky
 Po této operaci se u souborů, u kterých byla provedena kontrola vrácení zpět, vynuluje příznak `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` a .

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
