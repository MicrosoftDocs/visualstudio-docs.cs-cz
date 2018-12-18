---
title: Sccismulticheckoutenabled – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4a71f839c2129bcfb699188dec09b02b18d4cd1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920115"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled – funkce
Tato funkce zkontroluje, zda modul plug-in správy zdrojového kódu umožňuje více rezervace souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Struktura kontext modulu plug-in zdroje ovládacího prvku.  
  
 pbMultiCheckout  
 [out] Určuje, zda je povoleno více rezervace pro tento projekt (nenulovou znamená, že se podporují více rezervace).  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Kontrola proběhla úspěšně.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|K nespecifikované chybě.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní IDE vytvoří dvě kontroly k určení, pokud soubory lze rezervovat současně více než jeden uživatel. Systém správy zdrojového kódu, nejprve musí podporovat více rezervace. Modul plug-in správy zdrojového kódu můžete zadat tato funkce při inicializaci tak, že zadáte `SCC_CAP_MULTICHECKOUT`. Po tomto datu, jako druhý kontrolu integrovaném vývojovém prostředí volá tuto funkci k určení, zda aktuální projekt podporuje více rezervace. Pokud více rezervace jsou podporovány pro zvolený projekt, modulu plug-in vrátí úspěch kód a nastaví `pbMultiCheckout` na nenulovou hodnotu (`TRUE`) nebo `FALSE`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)