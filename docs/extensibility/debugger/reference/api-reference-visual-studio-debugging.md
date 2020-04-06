---
title: Odkaz na rozhraní API (ladění sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a2df6d82099a927664620e19096107f283afada
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738173"
---
# <a name="api-reference-visual-studio-debugging"></a>Referenční informace pro rozhraní API (Ladění sady Visual Studio)
Referenční část obsahuje koncepční přehled rozhraní API, průvodce, který zobrazuje syntaxi a použití pro všechny prvky rozhraní API a sortiment příkladů kódu. Všechny odkazy jsou seřazeny abecedně podle kategorií.

 V následující tabulce `HRESULT` jsou uvedeny běžné hodnoty vrácené metodami.

|Name (Název)|Popis|Hodnota|
|----------|-----------------|-----------|
|S_OK|Úspěch|0x00000000|
|E_UNEXPECTED|Došlo k neočekávanému selhání.|0x8000FFFF|
|E_NOTIMPL|Není implementováno.|0x80004001|
|E_OUTOFMEMORY|K dokončení operace není dostatek paměti.|0x8007000E|
|E_invalidarg|Jeden nebo více argumentů je neplatných.|0x80070057|
|E_NOINTERFACE|Žádné takové rozhraní není podporováno.|0x80004002|
|E_POINTER|Neplatný ukazatel.|0x80004003|
|E_HANDLE|Neplatný popisovač.|0x80070006|
|E_ABORT|Operace byla přerušena.|0x80004004|
|E_fail|Došlo k neočekávanému selhání.|0x80004005|
|E_ACCESSDENIED|Obecná chyba odepření přístupu.|0x80070005|

> [!NOTE]
> [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Když vrátí metoda ladění `S_OK`, předpokládá se, že všechny out ukazatele parametrů jsou platné, to znamená, `S_OK` že žádné ověření se provádí na out ukazatele parametru při vrácení.
>
> [!NOTE]
> Neplatné `NULL` nebo [out] parametry může způsobit selhání ide.

## <a name="see-also"></a>Viz také
- [Rozhraní](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Rozšiřitelnost programu Visual Studio Debugger](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
