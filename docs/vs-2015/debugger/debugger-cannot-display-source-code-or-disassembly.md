---
title: Ladicí program nemůže zobrazit zdrojový kód nebo zpětný překlad | Microsoft Docs
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
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce4460aecb634523de02f2e3f6929b206b415e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186496"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Ladicí program nemůže zobrazit zdrojový kód nebo zpětný překlad.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato chyba čte:  
  
 Ladicí program nemůže zobrazit zdrojový kód nebo zpětný překlad pro aktuální umístění, kde bylo spuštění zastaveno.  
  
 Tato chybová zpráva se může vyskytnout z několika důvodů:  
  
- Možná jste narazili na zarážku v umístění, pro které neexistuje zdrojový kód, při ladění jazyka, který nepodporuje zpětný překlad. Otevřete okno **zarážky** , najděte zarážku a odstraňte ji.  
  
- Pokud ladíte skript, možná jste narazili na zarážku, zatímco v programu neexistovala žádná vlákna. V nabídce **ladění** vyberte **Krok** nebo **pokračovat** a pokračujte v ladění.  
  
- Kvůli bezpečnostním hlediskům může ladicí program zabránit načtení zásobníku, vlákna, registraci a dalších informací o kontextu z programu, který ladíte. K tomu pravděpodobně dojde, pokud ladíte webovou aplikaci a nemáte správné oprávnění pro přístup k virtuálnímu adresáři. Nastavte zabezpečení virtuálního adresáře na anonymní a zkuste to znovu.  
  
## <a name="see-also"></a>Viz také  
 [Základy ladicího programu](../debugger/debugger-basics.md)   
 [Ladění v aplikaci Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
