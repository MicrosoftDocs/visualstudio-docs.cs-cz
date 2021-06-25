---
description: Tato funkce umožňuje uživateli vyhledat soubory, které už jsou v systému správy zdrojového kódu, a následně tyto soubory udělat součástí aktuálního projektu.
title: SccAddFromScc – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48560f135d73c4e53ba132845f4c768cdf4ac982
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904873"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc – funkce
Tato funkce umožňuje uživateli vyhledat soubory, které už jsou v systému správy zdrojového kódu, a následně tyto soubory udělat součástí aktuálního projektu. Tato funkce může například získat společný soubor hlaviček do aktuálního projektu bez kopírování souboru. Pole vrácených souborů obsahuje seznam souborů, které chce uživatel přidat `lplpFileNames` do projektu ide.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>Parametry
 pvContext

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 lpnFiles

[in, out] Vyrovnávací paměť pro počet souborů, které se přidávají. (To je `NULL` v případě, že paměť, `lplpFileNames` na kterou odkazuje , má být uvolněna. Podrobnosti najdete v poznámkách.)

 lplpFileNames

[in, out] Pole ukazatelů na všechny názvy souborů bez cest k adresářům. Toto pole se přiděluje a uchová modul plug-in správy zdrojového kódu. Pokud = 1 a není , první jméno v poli, na `lpnFiles` které odkazuje , obsahuje `lplpFileNames` `NULL` `lplpFileNames` cílovou složku.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Soubory se úspěšně našly a přidaly do projektu.|
|SCC_I_OPERATIONCANCELED|Operace se zrušila bez vlivu.|
|SCC_I_RELOADFILE|Soubor nebo projekt je potřeba znovu načíst.|

## <a name="remarks"></a>Poznámky
 Integrované vývojové prostředí tuto funkci volá. Pokud modul plug-in správy zdrojového kódu podporuje zadání místní cílové složky, předá integrované vývojové prostředí (IDE) hodnotu = 1 a předá název `lpnFiles` místní složky do `lplpFileNames` .

 Když se volání funkce vrátí, modul plug-in přiřadil hodnoty a , které podle potřeby přidělují paměť pro pole názvů souborů (všimněte si, že toto přidělení nahrazuje `SccAddFromScc` `lpnFiles` ukazatel v `lplpFileNames` `lplpFileNames` ). Modul plug-in správy zdrojového kódu zodpovídá za umístění všech souborů do adresáře uživatele nebo do zadané složky označení. Integrované vývojové prostředí (IDE) pak přidá soubory do projektu integrovaného vývojového prostředí (IDE).

 Integrované vývojové prostředí tuto funkci volá podruhé a předá `NULL` ji pro `lpnFiles` . To je interpretováno jako speciální signál modulu plug-in správy zdrojového kódu pro uvolnění paměti přidělené pro pole názvu souboru v `lplpFileNames``.`

 `lplpFileNames` je `char ***` ukazatel. Modul plug-in správy zdrojového kódu umístí ukazatel na pole ukazatelů na názvy souborů, čímž se seznam pro toto rozhraní API předává standardním způsobem.

> [!NOTE]
> Počáteční verze rozhraní API VSSCI neposkytly způsob, jak označit cílový projekt pro přidané soubory. Aby se tomu přizpůsobil, vylepšuje se sémantika parametru, aby se z něj místo `lplpFIleNames` výstupního parametru vylepšoval parametr in/out. Pokud je zadán pouze jeden soubor, to znamená, že hodnota, na kterou odkazuje = 1, pak první prvek obsahuje `lpnFiles` `lplpFileNames` cílovou složku. Pokud chcete použít tuto novou sémantiku, volá integrované vývojové prostředí `SccSetOption` funkci s `nOption` parametrem nastaveným na `SCC_OPT_SHARESUBPROJ` . Pokud modul plug-in správy zdrojového kódu nepodporuje sémantiku, vrátí `SCC_E_OPTNOTSUPPORTED` . Tím zakážete použití funkce **Přidat ze správy zdrojového** kódu. Pokud modul plug-in podporuje **funkci Přidat ze správy zdrojového** kódu ( ), musí podporovat novou sémantiku a vrátit `SCC_CAP_ADDFROMSCC` `SCC_I_SHARESUBPROJOK` .

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
