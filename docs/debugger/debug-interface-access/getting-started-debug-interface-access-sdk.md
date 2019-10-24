---
title: Začínáme (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dd6a98f377ba295d6a866c9db95671de4ff16ea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745106"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Začínáme (Přístup k rozhraní ladění SDK)
Sada SDK přístup k rozhraní ladění (DIA) poskytuje pokyny a ukázku, která ukazuje, jak používat rozhraní DIA API. Použijte rozhraní a metody v DIA SDK k vývoji vlastních aplikací, které otevřou soubory. pdb a. dbg, a vyhledejte jejich obsah pro symboly, hodnoty, atributy, adresy a další informace o ladění. Tato sada SDK také poskytuje referenční tabulky pro vlastnosti přidružené ke symbolům nalezeným v C++ aplikacích.

 Chcete-li nejlépe použít DIA SDK, měli byste být obeznámeni s následujícím:

- C++programovací jazyk

- Programování COM

- Integrované vývojové prostředí (IDE) sady Visual Studio pro kompilování ukázek

  DIA SDK se obvykle instaluje se sadou Visual Studio a její výchozí umístění je *[jednotka]* \Program Files\Microsoft Visual Studio 9.0 \ DIA SDK. V rámci instalace aplikace msdia90. dll, která implementuje DIA SDK, je automaticky registrována tak, aby `dia2.h` ji bylo možné použít pro použití v rámci programu a odkaz na `diaguids.lib`.

  Záhlaví: include\dia2.h

  Knihovna: lib\diaguids.lib

  Knihovna DLL: bin\msdia80.dll

  IDL: idl\dia2.idl

## <a name="in-this-section"></a>V tomto oddílu

[Přehled](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

Kontroluje základní architekturu DIA.

[Dotazování na soubor .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Poskytuje podrobné pokyny pro použití rozhraní DIA API k dotazování na soubor. pdb.

## <a name="see-also"></a>Viz také:

- [Přístup k rozhraní ladění SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)