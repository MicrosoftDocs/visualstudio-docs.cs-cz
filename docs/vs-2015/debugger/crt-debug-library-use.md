---
title: Použití knihovny ladění CRT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7e14a181b432dede3f00a4465d40154fdb393bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697859"
---
# <a name="crt-debug-library-use"></a>Použití knihovny ladění CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Knihovna run-time jazyka C poskytuje rozsáhlou podporu ladění. Chcete-li použít jednu z knihoven ladění CRT, je nutné propojit s [/Debug](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) a kompilovat pomocí **/MDD**, **/MTD**nebo **/LDD**.  
  
## <a name="remarks"></a>Poznámky  
 Hlavní definice a makra pro ladění CRT lze nalézt v souboru hlaviček souboru Crtdbg. h.  
  
 Funkce v ladicích knihovnách CRT jsou kompilovány s ladicími informacemi ([/Z7,/zd,/Zi,/Zi (formát ladicích informací)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) a bez optimalizace. Některé funkce obsahují kontrolní výrazy pro ověření parametrů, které jsou předány, a zdrojový kód je k dispozici. Pomocí tohoto zdrojového kódu můžete krokovat s funkcí CRT a ověřit tak, že funkce fungují podle očekávání a kontrolovat chybné parametry nebo stavy paměti. (Některé technologie CRT jsou proprietární a neposkytují zdrojový kód pro zpracování výjimek, plovoucí desetinnou čárku a několik dalších rutin.)  
  
 Při instalaci Visual C++ máte možnost instalace zdrojového kódu knihovny run-time jazyka C na pevný disk. Pokud nenainstalujete zdrojový kód, budete potřebovat disk CD-ROM pro krokování funkcí CRT.  
  
 Další informace o různých knihovnách modulu runtime, které lze použít, naleznete v tématu [C run-time libraries](https://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>Viz také  
 [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)   
 [/MD,/MT,/LD (Použít běhovou knihovnu)](https://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)
