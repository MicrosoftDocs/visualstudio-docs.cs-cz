---
title: 'IDiaDataSource:: openSession | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198603"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otevře relaci pro zadávání dotazů na symboly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 ppSession  
 mimo Vrátí objekt [IDiaSession](../../debugger/debug-interface-access/idiasession.md) představující otevřenou relaci.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. V následující tabulce jsou uvedeny možné návratové hodnoty pro tuto metodu.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|E_UNEXPECTED|Objekt [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) nebyl dříve inicializován se zdrojem symbolů.|  
|E_INVALIDARG|Neplatný `ppSession` parametr|  
|E_OUTOFMEMORY|Pro otevření relace není dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda otevře objekt [IDiaSession](../../debugger/debug-interface-access/idiasession.md) pro zdroj dat.  
  
 `IDiaSession` objekty implementují dotazy do zdroje dat. Relace spravuje jeden adresní prostor pro každou sadu symbolů ladění. Pokud je soubor. exe nebo. dll popsaný v symbolech zdroje dat aktivní ve více rozsahech adres (například proto, že je načteno více procesů), měla by být použita jedna relace pro každý rozsah adres.  
  
## <a name="example"></a>Příklad  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Přehled](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Dotazování na soubor .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
