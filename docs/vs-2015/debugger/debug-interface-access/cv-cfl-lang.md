---
title: CV_CFL_LANG – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6e2aa402d3f882d83525b180707653b97533e32
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724786"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje jazyk zdrojového kódu aplikace nebo propojeném modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
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
 Je aplikace jazyka C.  
  
 CV_CFL_CXX  
 Je aplikace jazyka C++.  
  
 CV_CFL_FORTRAN  
 Jazyk aplikace je až po FORTRAN.  
  
 CV_CFL_MASM  
 Microsoft Macro Assembler je jazyk aplikace.  
  
 CV_CFL_PASCAL  
 Jazyk aplikace je Pascal.  
  
 CV_CFL_BASIC  
 Jazyk aplikace je BASIC.  
  
 CV_CFL_COBOL  
 Jazyk aplikace je COBOL.  
  
 CV_CFL_LINK  
 Aplikace je modul vytvořeného v propojovacím programu.  
  
 CV_CFL_CVTRES  
 Aplikace je modul prostředků převést pomocí nástroje CVTRES.  
  
 CV_CFL_CVTPGD  
 Aplikace je modul optimalizovaný POGO generovaný nástrojem CVTPGD.  
  
 CV_CFL_CSHARP  
 Je aplikace jazyka C#.  
  
 CV_CFL_VB  
 Je aplikace jazyka Visual Basic.  
  
 CV_CFL_ILASM  
 Jazyk aplikace je sestavení převodní jazyk (to znamená, že sestavení Common Language Runtime (CLR)).  
  
 CV_CFL_JAVA  
 Je aplikace jazyka Java.  
  
 CV_CFL_JSCRIPT  
 Jazyk aplikace je Jscript.  
  
 CV_CFL_MSIL  
 Jazyk aplikace je neznámý Microsoft Intermediate Language (MSIL), může být způsobeno použitím [parametru/LTCG (generování kódu při propojování odkaz)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) přepnout.  
  
 CV_CFL_HLSL  
 Jazyk aplikace je vysoká úroveň shaderu jazyk.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty v tomto výčtu jsou vráceny prostřednictvím volání [idiasymbol::get_language –](../../debugger/debug-interface-access/idiasymbol-get-language.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: cvconst.h  
  
## <a name="see-also"></a>Viz také  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)



