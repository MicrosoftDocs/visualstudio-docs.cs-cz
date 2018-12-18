---
title: Omezení ladění skriptů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 767322cd60ce1d1e455903b357a062cc1f31927d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753469"
---
# <a name="limitations-on-script-debugging"></a>Omezení ladění skriptů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podporuje ladění skriptů na straně klienta, v souladu s omezeními v tomto tématu.  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Omezení mapování zarážek pomocí skriptu na straně klienta  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Umožňuje nastavit zarážku na straně serveru ASPX nebo HTML soubor, který se transformuje do souboru na straně klienta v době běhu. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mapuje zarážku ze souboru na straně serveru pro odpovídající zarážky v souboru straně klienta, v souladu s těmito omezeními:  
  
-   Zarážky nastavené v `<script>` bloky. Zarážky v zpracování vloženého skriptu nebo `<% %>` bloky nelze mapovat.  
  
-   Adresa URL prohlížeče na stránce musí obsahovat název stránky. Například http://microsoft.com/default.apsx. Mapování zarážek nemůže rozpoznat jako například přesměrování z adresy http://microsoft.com na výchozí stránku.  
  
-   Zarážky musí být nastavena na stránce určeného v adrese URL prohlížeče, nikoli v souboru ASPX ovládací prvek (ascx), hlavní stránky nebo jiný soubor součástí této stránce. Zarážky nastavené v zahrnuté stránky nelze mapovat.  
  
-   Zarážky nastavené v `<script defer=true>` bloky nelze mapovat.  
  
-   Pro zarážky nastavené v `<script id="">` bloky, ignoruje mapování zarážek `id` atribut.  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>Mapování zarážek a duplicitní řádky  
 Algoritmus mapování zarážek ve skriptu na straně serveru a na straně klienta najít odpovídající umístění, kontroluje kód na každém řádku. Algoritmus předpokládá, že každý řádek představuje jedinečný. Pokud dva nebo více řádky obsahují stejný kód a nastavte zarážku v jednom z těchto duplicitní řádky, algoritmus mapování zarážky vybrat nesprávné duplicitní v souboru straně klienta. Chcete-li tomu zabránit, přidejte komentář k řádku, kde jste nastavili zarážku. Příklad:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```



