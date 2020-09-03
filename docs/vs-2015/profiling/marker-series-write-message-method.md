---
title: 'marker_series:: write_message metoda | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f759ea679af818d85dd365f5615ce4fc664df89a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200745"
---
# <a name="marker_serieswrite_message-method"></a>marker_series::write_message – metoda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapíše zprávu do trasovacího souboru Vizualizátor souběžnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void write_message(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Format`  
 Složený řetězec formátu, který obsahuje text vzájemně se smíšenými nulami nebo více formátovacími položkami, které odpovídají objektům v seznamu argumentů.  
  
 `_Importance`  
 Úroveň důležitosti.  
  
 `_Category`  
 Category. důležitost úrovně.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkersobj. h  
  
 **Obor názvů:** Concurrency::d odeslání diagnostických  
  
## <a name="see-also"></a>Viz také  
 [marker_series – třída](../profiling/marker-series-class.md)
