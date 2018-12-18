---
title: Scccheckin – funkce | Dokumentace Microsoftu
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
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26daf5fcd3ee4ec14b0801c828a6e536a65150d8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797998"
---
# <a name="scccheckin-function"></a>SccCheckin – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce zkontroluje v dříve rezervovaných souborů do systému správy zdrojového kódu, ukládání změn a vytvořit novou verzi. Tato funkce je volána s počet a pole názvů souborů se změnami.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontext modulu plug-in zdroje ovládacího prvku.  
  
 hWnd  
 [in] Popisovač okna integrovaného vývojového prostředí, pomocí modulu plug-in SCC můžete jako nadřazený pro všechna dialogová okna, které poskytuje.  
  
 %{nfiles/  
 [in] Počet souborů, které se rozhodli vrátit se změnami.  
  
 lpFileNames  
 [in] Pole úplná místní cesta názvy souborů, které mají být vráceny se změnami.  
  
 lpComment  
 [in] Komentář se má použít u všech vybraných souborů se změnami. Toto je `NULL` Pokud modul plug-in správy zdrojového kódu by se zobrazit výzva pro komentář.  
  
 fOptions  
 [in] Příkaz příznaky, buď 0 nebo `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] SCC plug-konkrétní možnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Soubory byly úspěšně vráceny se změnami.|  
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není pod správou zdrojového kódu.|  
|SCC_E_ACCESSFAILURE|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize. Doporučuje se zkuste to znovu.|  
|SCC_E_NONSPECIFICERROR|K nespecifikované chybě. Soubor se změnami.|  
|SCC_E_NOTCHECKEDOUT|Uživatel není rezervován souboru, takže nelze vrácení se změnami.|  
|SCC_E_CHECKINCONFLICT|Vrácení se změnami nelze provést, protože:<br /><br /> – Vrátil jiný uživatel má dopředu a `bAutoReconcile` je chybná.<br /><br /> -nebo-<br /><br /> -Automatické sloučení nelze provést, (například když jsou binární soubory).|  
|SCC_E_VERIFYMERGE|Soubor se sloučit automaticky, ale nebyla vrácena čekající ověření uživatele.|  
|SCC_E_FIXMERGE|Soubor se sloučit automaticky, ale nebyla vrácena kvůli konfliktu při slučování, který se musí ručně vyřešit.|  
|SCC_E_NOTAUTHORIZED|Uživatel nemůže k provedení této operace.|  
|SCC_I_OPERATIONCANCELED|Operace byla zrušena před dokončením.|  
|SCC_I_RELOADFILE|Soubor nebo projekt je potřeba znovu načíst.|  
|SCC_E_FILENOTEXIST|Místní soubor se nenašel.|  
  
## <a name="remarks"></a>Poznámky  
 Komentář se vztahuje na všechny soubory se změnami. Může být argumentem komentář `null` string, v takovém případě můžete plug-in správy zdrojových kódů vyzývat uživatele k řetězec komentáře pro každý soubor.  
  
 `fOptions` Argument můžete zadat hodnotu `SCC_KEEP_CHECKEDOUT` příznak označující záměru uživatele se změnami soubor a prohlédněte si ho znovu.  
  
## <a name="see-also"></a>Viz také  
 [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)

