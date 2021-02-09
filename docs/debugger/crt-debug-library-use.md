---
title: Použití knihovny ladění CRT | Microsoft Docs
description: Přečtěte si, jak Knihovna CRT (C run-time) podporuje vaše ladění a co musíte udělat, abyste mohli používat knihovny ladění CRT.
ms.custom: SEO-VS-2020
ms.date: 10/03/2019
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe50082f8ff62c4a19b7725facc18f43d672e353
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865706"
---
# <a name="crt-debug-library-use"></a>Použití knihovny ladění CRT
Knihovna run-time jazyka C poskytuje rozsáhlou podporu ladění. Chcete-li použít jednu z knihoven ladění CRT, je nutné propojit s [/Debug](/cpp/build/reference/debug-generate-debug-info) a kompilovat pomocí **/MDD**, **/MTD** nebo **/LDD**.

## <a name="remarks"></a>Poznámky
 Hlavní definice a makra pro ladění CRT lze nalézt v souboru hlaviček souboru Crtdbg. h.

 Funkce v ladicích knihovnách CRT jsou kompilovány s ladicími informacemi ([/Z7,/zd,/Zi,/Zi (formát ladicích informací)](/cpp/build/reference/z7-zi-zi-debug-information-format)) a bez optimalizace. Některé funkce obsahují kontrolní výrazy pro ověření parametrů, které jsou předány, a zdrojový kód je k dispozici. Pomocí tohoto zdrojového kódu můžete krokovat s funkcí CRT a ověřit tak, že funkce fungují podle očekávání a kontrolovat chybné parametry nebo stavy paměti. (Některé technologie CRT jsou proprietární a neposkytují zdrojový kód pro zpracování výjimek, plovoucí desetinnou čárku a několik dalších rutin.)

 Další informace o různých knihovnách modulu runtime, které můžete použít, najdete v tématu [knihovny Run-Time C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Viz také

- [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)
- [/MD,/MT,/LD (použití knihovny Run-Time)](/cpp/build/reference/md-mt-ld-use-run-time-library)