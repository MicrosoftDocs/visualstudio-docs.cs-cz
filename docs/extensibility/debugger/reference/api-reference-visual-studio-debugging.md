---
description: Referenční oddíl obsahuje koncepční přehled rozhraní API, průvodce, který zobrazuje syntaxi a použití pro všechny prvky rozhraní API a řadu příkladů kódu.
title: Reference k rozhraní API (ladění sady Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a8a43e4bae5afce98e07b196f5a01c33d44c72ca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085543"
---
# <a name="api-reference-visual-studio-debugging"></a>Referenční informace pro rozhraní API (Ladění sady Visual Studio)
Referenční oddíl obsahuje koncepční přehled rozhraní API, průvodce, který zobrazuje syntaxi a použití pro všechny prvky rozhraní API a řadu příkladů kódu. Všechny odkazy jsou seřazené podle kategorií podle abecedy.

 V následující tabulce jsou uvedeny běžné `HRESULT` hodnoty vracené metodami.

|Název|Description|Hodnota|
|----------|-----------------|-----------|
|S_OK|Úspěch.|0x00000000|
|E_UNEXPECTED|Došlo k neočekávanému selhání.|0x8000FFFF|
|E_NOTIMPL|Není implementováno.|0x80004001|
|E_OUTOFMEMORY|K dokončení operace není dostatek paměti.|0x8007000E|
|E_INVALIDARG|Jeden nebo více argumentů je neplatných.|0x80070057|
|E_NOINTERFACE|Takové rozhraní není podporováno.|0x80004002|
|E_POINTER|Neplatný ukazatel|0x80004003|
|E_HANDLE|Neplatný popisovač.|0x80070006|
|E_ABORT|Operace byla přerušena.|0x80004004|
|E_FAIL|Došlo k neočekávanému selhání.|0x80004005|
|E_ACCESSDENIED|Chyba obecného přístupu k odepření|0x80070005|

> [!NOTE]
> Když se [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Metoda ladění vrátí `S_OK` , předpokládá se, že všechny ukazatele parametrů jsou platné, to znamená, že při návratu se neprovádí žádné ověřování ukazatelů parametrů `S_OK` .
>
> [!NOTE]
> Neplatné nebo `NULL` [out] parametry mohou způsobit zhroucení rozhraní IDE.

## <a name="see-also"></a>Viz také
- [Rozhraní](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Rozšiřitelnost programu Visual Studio Debugger](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
