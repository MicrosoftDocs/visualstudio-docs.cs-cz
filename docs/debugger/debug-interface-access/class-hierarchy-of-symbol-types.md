---
title: Hierarchie tříd typů symbolů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed6817c5c01b66143739b2f81899f2b58886d8e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462271"
---
# <a name="class-hierarchy-of-symbol-types"></a>Hierarchie tříd typů symbolů
Následující tabulka popisuje typy symbolů v hierarchii tříd.

## <a name="symbol-types"></a>Typy symbolů

|Typ symbolu|Popis|
|-----------------|-----------------|
|[UDT](../../debugger/debug-interface-access/udt.md)|Symbol, který se používá k reprezentaci každé třídy, struktury a sjednocení.|
|[Výčet (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Symbol pro výčtové typy|
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Symbol pro typy ukazatelů|
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Symbol pro typy polí|
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Symbol pro základní typy|
|[Typedef (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Symbol, který zavádí názvy pro jiné typy.|
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Symbol použitý pro každou základní třídu uživatelsky definovaného typu (UDT).|
|[Friend (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Symbol pro třídy Friend a Friend Functions|
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Symbol pro každý podpis jedinečné funkce|
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Symbol pro každý parametr funkce|
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Symbol pro velikost virtuální tabulky|
|[VTable](../../debugger/debug-interface-access/vtable.md)|Symbol pro virtuální tabulku|
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Symbol pro typ definovaný dodavatelem|
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Symbol pro typ definovaný v metadatech|
|[Rozměr](../../debugger/debug-interface-access/dimension.md)|Symbol pro rozměry pole|

> [!NOTE]
> Každý symbol může mít vlastnosti, které uchovávají informace o symbolu, jakož i odkazy na jiné symboly. Tyto vlastnosti jsou uvedeny v tématech jednotlivých symbolů.

## <a name="see-also"></a>Viz také
- [CV_access_e – výčet](../../debugger/debug-interface-access/cv-access-e.md)
- [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Symboly a značky symbolů](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)