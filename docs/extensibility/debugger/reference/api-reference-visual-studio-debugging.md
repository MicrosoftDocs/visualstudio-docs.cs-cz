---
title: Reference k rozhraní API (ladění sady Visual Studio) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97d5aa6fc92457557493005389d129993d38e099
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839437"
---
# <a name="api-reference-visual-studio-debugging"></a>Referenční informace pro rozhraní API (Ladění sady Visual Studio)
Část odkaz obsahuje koncepční přehled rozhraní API, průvodce, který ukazuje syntaxi a použití pro všechny prvky rozhraní API a celé řady různých doprovodných příklady kódu. Všechny odkazy abecedním pořadí podle kategorie.  
  
 V následující tabulce jsou uvedeny běžné `HRESULT` hodnoty vrácené z metody.  
  
|Název|Popis|Hodnota|  
|----------|-----------------|-----------|  
|S_OK|Úspěch.|0x00000000|  
|E_UNEXPECTED, JE-|Neočekávaná chyba.|0x8000FFFF|  
|E_NOTIMPL|Není implementováno.|0x80004001|  
|E_OUTOFMEMORY|Není dostatek paměti k dokončení operace.|0x8007000E|  
|E_INVALIDARG|Jeden nebo více argumentů nejsou platné.|0x80070057|  
|E_NOINTERFACE|Rozhraní není podporováno.|0x80004002|  
|E_POINTER|Neplatný ukazatel.|0x80004003|  
|E_HANDLE|Neplatný popisovač.|0x80070006|  
|E_ABORT|Operace byla přerušena.|0x80004004|  
|E_FAIL|Neočekávaná chyba.|0x80004005|  
|E_ACCESSDENIED|Obecná chyba odepření přístupu.|0x80070005|  
  
> [!NOTE]
>  Když [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ladění metoda vrátí `S_OK`, se předpokládá, že ven parametr ukazatele jsou platné, to znamená, se žádné ověření provádějí na si parametr ukazatele při `S_OK` se vrátí.  
> 
> [!NOTE]
>  Neplatný nebo `NULL` [parametry out] může způsobit, že rozhraní IDE k selhání.  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Rozšiřitelnost programu Visual Studio Debugger](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)