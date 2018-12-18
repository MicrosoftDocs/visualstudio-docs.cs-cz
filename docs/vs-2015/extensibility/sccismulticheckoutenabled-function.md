---
title: Sccismulticheckoutenabled – funkce | Dokumentace Microsoftu
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
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e449ab110b4087f2c7e997b92d66f62f7bd780f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769409"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce zkontroluje, zda modul plug-in správy zdrojového kódu umožňuje více rezervace souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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

