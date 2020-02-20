---
title: Omezení ladění skriptů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f4f8f1e2fb014dc812bb5980d333e0a851f9222
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476818"
---
# <a name="limitations-on-script-debugging"></a>Omezení ladění skriptů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podporuje ladění skriptu na straně klienta v souladu s omezeními v tomto tématu.  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Omezení mapování zarážek u skriptu na straně klienta  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umožňuje nastavit zarážku v souboru ASPX nebo HTML na straně serveru, který se transformuje na soubor na straně klienta v době běhu. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mapuje zarážku ze souboru na straně serveru na odpovídající zarážku v souboru na straně klienta v závislosti na následujících omezeních:  
  
- V blocích `<script>` musí být nastavené zarážky. Zarážky ve vloženém skriptu nebo `<% %>` bloky nelze namapovat.  
  
- Adresa URL prohlížeče stránky musí obsahovat název stránky. například `http://microsoft.com/default.apsx`. Mapování zarážek nemůže rozpoznat přesměrování z adresy, jako je například `http://microsoft.com` na výchozí stránku.  
  
- Zarážka musí být nastavena na stránce zadané v adrese URL prohlížeče, nikoli v souboru ovládacího prvku ASPX (ASCX), na stránce předlohy nebo v jiném souboru, který je součástí této stránky. Zarážky nastavené v zahrnutých stránkách nejde namapovat.  
  
- Zarážky nastavené v blocích `<script defer=true>` nelze namapovat.  
  
- Pro zarážky nastavené v blocích `<script id="">`, mapování zarážek ignoruje atribut `id`.  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>Mapování zarážek a duplicitní řádky  
 Chcete-li najít odpovídající umístění na straně serveru a na straně klienta, algoritmus mapování zarážek kontroluje kód na každém řádku. Algoritmus předpokládá, že každý řádek je jedinečný. Pokud dva nebo více řádků obsahují stejný kód a nastavili jste zarážku na jednom z těchto duplicitních řádků, algoritmus mapování zarážek může v souboru na straně klienta vybrat chybnou duplicitu. Chcete-li tomu zabránit, přidejte komentář na řádek, kde jste nastavili zarážku. Například:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```
