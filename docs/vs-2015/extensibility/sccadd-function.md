---
title: Sccadd – funkce | Dokumentace Microsoftu
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
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29703be15369649df2208c1521a6636e5ccbefb9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765834"
---
# <a name="sccadd-function"></a>SccAdd – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce přidá nové soubory do systému správy zdrojového kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontext modulu plug-in zdroje ovládacího prvku.  
  
 hWnd  
 [in] Popisovač okna integrovaného vývojového prostředí, které modul plug-in správy zdrojového kódu můžete použít jako nadřazený pro všechna dialogová okna, které poskytuje.  
  
 %{nfiles/  
 [in] Počet vybraných mají být přidány do aktuálního projektu, jak je uvedeno v souborů `lpFileNames` pole.  
  
 lpFileNames  
 [in] Pole plně kvalifikované názvy místních souborů, které mají být přidány.  
  
 lpComment  
 [in] Komentář, který se má použít pro všechny přidávané soubory.  
  
 pfOptions  
 [in] Pole příznaků příkazů, na základě podle souborů k dispozici.  
  
 pvOptions  
 [in] Možností správy zdrojového kódu plug-konkrétní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Přidat operace byla úspěšná.|  
|SCC_E_FILEALREADYEXISTS|Vybraný soubor je již pod správou zdrojových kódů.|  
|SCC_E_TYPENOTSUPPORTED|Typ souboru (například binární) nepodporuje systém správy zdrojového kódu.|  
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu nepodporuje tuto operaci.|  
|SCC_E_ACCESSFAILURE|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize. Doporučuje se zkuste to znovu.|  
|SCC_E_NOTAUTHORIZED|Uživatel nemůže k provedení této operace.|  
|SCC_E_NONSPECIFICERROR|Obecná chyba; přidáte, nebyla provedena.|  
|SCC_I_OPERATIONCANCELED|Operace byla zrušena před dokončením.|  
|SCC_I_RELOADFILE|Soubor nebo projekt je potřeba znovu načíst.|  
|SCC_E_FILENOTEXIST|Místní soubor se nenašel.|  
  
## <a name="remarks"></a>Poznámky  
 Obvyklého `fOptions` zde nahrazuje pole, `pfOptions`, s jednou `LONG` možnost specifikace na soubor. Je to proto, že tento typ souboru se může lišit od souboru.  
  
> [!NOTE]
>  Je neplatné zadat současně `SCC_FILETYPE_TEXT` a `SCC_FILETYPE_BINARY` možnosti pro stejný soubor, ale platnost nezadáte. Nastavení ani je stejné jako nastavení `SCC_FILETYPE_AUTO`, v takovém případě řídit zdroj modulu plug-in automatické typ souboru.  
  
 Níže je seznam příznaky použité při `pfOptions` pole:  
  
|Možnost|Hodnota|Význam|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|Modul plug-in správy zdrojového kódu musí rozpoznat typ souboru.|  
|SCC_FILETYPE_TEXT|0x01|Určuje textový soubor ASCII.|  
|SCC_FILETYPE_BINARY|0x02|Určuje typ souborů než ASCII text.|  
|SCC_ADD_STORELATEST|0x04|Ukládá pouze nejnovější verzi souboru, žádné rozdíly.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Zpracuje soubor jako text ve formátu ANSI.|  
|SCC_FILETYPE_UTF8|0x10|Zpracuje soubor jako text v kódu Unicode ve formátu UTF8.|  
|SCC_FILETYPE_UTF16LE|0x20|Zpracuje soubor jako text v kódu Unicode v UTF16 ve formátu Little Endian formátu.|  
|SCC_FILETYPE_UTF16BE|0x40|Zpracuje formátu souboru jako text v kódu Unicode v UTF16 Big Endian.|  
  
## <a name="see-also"></a>Viz také  
 [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)

