---
title: Funkce SccGetVersion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4e548f1f2b82a97206cdf41174a8c1c7d61e885
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200044"
---
# <a name="sccgetversion-function"></a>SccGetVersion – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce získá číslo verze rozhraní API modulu plug-in správy zdrojového kódu podporovaného modulem plug-in správy zdrojových kódů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="return-value"></a>Návratová hodnota  
 `LONG`Datový typ, který obsahuje číslo verze podporovaného rozhraní API modulu plug-in správy zdrojových kódů:  
  
|WORD|Popis|  
|----------|-----------------|  
|HIWORD|Hlavní verze|  
|LOWORD|Podverze|  
  
## <a name="remarks"></a>Poznámky  
 Pokud například modul plug-in správy zdrojových kódů podporuje verzi 1,3 rozhraní API modulu plug-in správy zdrojového kódu, vrátí tato funkce 0x0103.  
  
## <a name="see-also"></a>Viz také  
 [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
