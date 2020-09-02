---
title: Funkce SccGetUserOption | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd00a2b669b806b09a6ae221b2ba2e03f8d45ceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200071"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce načte celou řadu možností specifických pro uživatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 pro Ukazatel kontextu modulu plug-in správy zdrojových kódů.  
  
 nOption  
 pro Možnost, která se má načíst (možné možnosti viz poznámky)  
  
 lpVal  
 mimo Hodnota přidružená k možnosti  
  
## <a name="return-value"></a>Návratová hodnota  
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Možnost byla úspěšně načtena.|  
|SCC_E_OPNOTSUPPORTED|Možnost není podporována.|  
|SCC_E_NONSPECIFICERROR|Došlo k neurčené chybě.|  
  
## <a name="remarks"></a>Poznámky  
 Tento příkaz podporuje následující možnosti:  
  
|Možnost uživatele|Popis|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Určuje, jestli chce uživatel rezervovat místní verzi souborů. `lpVal` je přiřazen `SCC_USEROPT_COLV_YES` (uživatel chce rezervovat místní soubory) nebo `SCC_USEROPT_COLV_NO` .|  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)   
 [Kódy chyb](../extensibility/error-codes.md)
