---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699363"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje jazyk zdrojového kódu pro aplikaci nebo propojený modul.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## <a name="elements"></a>Elementy  
 CV_CFL_C  
 Jazyk aplikace je C.  
  
 CV_CFL_CXX  
 Jazyk aplikace je C++.  
  
 CV_CFL_FORTRAN  
 Jazyk aplikace je FORTRAN.  
  
 CV_CFL_MASM  
 Jazyk aplikace je Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 Jazyk aplikace je Pascal.  
  
 CV_CFL_BASIC  
 Jazyk aplikace je základní.  
  
 CV_CFL_COBOL  
 Jazyk aplikace je COBOL.  
  
 CV_CFL_LINK  
 Aplikace je modulem generovaným linkerem.  
  
 CV_CFL_CVTRES  
 Aplikace je modul prostředků převedený pomocí nástroje CVTRES Tool.  
  
 CV_CFL_CVTPGD  
 Aplikace je POGO optimalizovaný modul generovaný pomocí nástroje CVTPGD.  
  
 CV_CFL_CSHARP  
 Jazyk aplikace je C#.  
  
 CV_CFL_VB  
 Jazyk aplikace je Visual Basic.  
  
 CV_CFL_ILASM  
 Jazyk aplikace je sestavení zprostředkujícího jazyka (to znamená sestavení CLR).  
  
 CV_CFL_JAVA  
 Jazyk aplikace je Java.  
  
 CV_CFL_JSCRIPT  
 Jazyk aplikace je JScript.  
  
 CV_CFL_MSIL  
 Jazyk aplikace je neznámý jazyk MSIL (Microsoft Intermediate Language), pravděpodobně výsledkem použití přepínače [/LTCG (generování kódu při propojování)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) .  
  
 CV_CFL_HLSL  
 Jazyk aplikace je jazykem shaderu na vysoké úrovni.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty v tomto výčtu jsou vráceny voláním metody [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: cvconst. h  
  
## <a name="see-also"></a>Viz také  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
