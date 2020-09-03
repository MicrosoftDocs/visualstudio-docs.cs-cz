---
title: Funkce SccUninitialize | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcb0b3a6718cc90db6f7176c823ccccbbfc05f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190852"
---
# <a name="sccuninitialize-function"></a>SccUninitialize – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce vyčistí všechna přidělení nebo otevřená připojení vytvořená předchozím voláním [SccInitialize](../extensibility/sccinitialize-function.md) při přípravě na vypnutí modulu plug-in správy zdrojových kódů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 pro Ukazatel na strukturu kontextu modulu plug-in správy zdrojového kódu vytvořenou v [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Vyčištění se úspěšně dokončilo.|  
  
## <a name="remarks"></a>Poznámky  
 Modul plug-in správy zdrojových kódů zodpovídá za přípravu a uvolnění paměti, kterou modul plug-in přidělil pro strukturu kontextu. Funkce se volá jednou pro každou danou instanci modulu plug-in. Volání [SccInitialize](../extensibility/sccinitialize-function.md) předchází tomuto volání. V době volání do nelze stále otevřít žádné projekty `SccUninitialize` .  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
