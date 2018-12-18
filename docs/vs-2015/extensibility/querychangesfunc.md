---
title: QUERYCHANGESFUNC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b9a0bbf3c26f797ec1bbf67ad8439e5f5ba05b11
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764208"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto je funkce zpětného volání používané [sccquerychanges –](../extensibility/sccquerychanges-function.md) operace vytvoření výčtu kolekce názvů souborů a určit stav každého souboru.  
  
 `SccQueryChanges` Funkce je uveden seznam souborů a ukazatel `QUERYCHANGESFUNC` zpětného volání. Modul plug-in správy zdrojového kódu zobrazí v seznamu a obsahuje informace o stavu (prostřednictvím tohoto zpětného volání) pro každý soubor v seznamu.  
  
## <a name="signature"></a>podpis  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 [in] `pvCallerData` Byl předán parametr volající (IDE) [sccquerychanges –](../extensibility/sccquerychanges-function.md). Modul plug-in správy zdrojového kódu by měl vytvořit žádné předpoklady o obsahu této hodnoty.  
  
 pChangesData  
 [in] Ukazatel [QUERYCHANGESDATA struktura](#LinkQUERYCHANGESDATA) struktura popisující změny do souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Rozhraní IDE vrátí odpovídající chybový kód:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Pokračujte ve zpracování.|  
|SCC_I_OPERATIONCANCELED|Zastavte zpracování.|  
|SCC_E_xxx|Všechny příslušné chyby SCC by se měla zastavit zpracování.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> Struktura QUERYCHANGESDATA  
 Struktura předaná pro každý soubor bude vypadat nějak takto:  
  
```cpp#  
struct QUERYCHANGESDATA_A  
{  
    DWORD  dwSize;  
    LPCSTR lpFileName;  
    DWORD  dwChangeType;  
    LPCSTR lpLatestName;  
};  
  
typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;  
  
struct QUERYCHANGESDATA_W  
{  
    DWORD   dwSize;  
    LPCWSTR lpFileName;  
    DWORD   dwChangeType;  
    LPCWSTR lpLatestName;  
};  
```  
  
 dwSize  
 Velikost struktury (v bajtech).  
  
 lpFileName  
 Původní název souboru pro tuto položku.  
  
 dwChangeType  
 Kód označující stav souboru:  
  
|Kód|Popis|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Nelze zjistit, co se změnilo.|  
|`SCC_CHANGE_UNCHANGED`|Pro tento soubor beze změn názvů.|  
|`SCC_CHANGE_DIFFERENT`|Soubor s jinou identitou, ale se stejným názvem existuje v databázi.|  
|`SCC_CHANGE_NONEXISTENT`|Soubor neexistuje v databázi nebo místně.|  
|`SCC_CHANGE_DATABASE_DELETED`|Soubor byl odstraněn v databázi.|  
|`SCC_CHANGE_LOCAL_DELETED`|Soubor byl odstraněn místně, ale soubor stále existuje v databázi. Pokud to nejde určit, vrátí `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Soubor přidán do databáze, ale neexistuje lokálně.|  
|`SCC_CHANGE_LOCAL_ADDED`|Soubor neexistuje v databázi a je nový místní soubor.|  
|`SCC_CHANGE_RENAMED_TO`|Soubor přejmenován nebo přesunut v databázi jako `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Soubor přejmenován nebo přesunut v databázi z `lpLatestName`; Pokud je to moc drahé, pokud chcete sledovat, vrátí různé příznak, jako například `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Aktuální název souboru pro tuto položku.  
  
## <a name="see-also"></a>Viz také  
 [Funkce zpětného volání implementované integrovaným vývojovým prostředím](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Sccquerychanges –](../extensibility/sccquerychanges-function.md)   
 [Chybové kódy](../extensibility/error-codes.md)

