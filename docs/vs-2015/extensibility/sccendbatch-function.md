---
title: Funkce SccEndBatch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 986056b1f5202c2fb94d27a8792ed3b0fe308944
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200141"
---
# <a name="sccendbatch-function"></a>SccEndBatch – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce uzavře dávku operací správy zdrojového kódu. Tyto dávky nemůžou být vnořené.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="return-value"></a>Návratová hodnota  
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Dávka operací se úspěšně uzavřela.|  
|SCC_E_UNKNOWNERROR|Nespecifická chyba.|  
  
## <a name="remarks"></a>Poznámky  
 Dávky správy zdrojového kódu se používají ke spouštění stejných operací správy zdrojových kódů napříč více projekty nebo několika kontexty. Dávky lze použít k vyloučení redundantních dialogových oken z uživatelského prostředí během dávkové operace. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) a `SccEndBatch` funkce slouží jako dvojice k označení začátku a konce operace. Nemohou být vnořené.  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
