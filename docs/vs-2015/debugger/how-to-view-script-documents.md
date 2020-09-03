---
title: 'Postupy: zobrazení dokumentů skriptu | Microsoft Docs'
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
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88f923ab0447f1ac7d57e84d94f0ab442d912d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189592"
---
# <a name="how-to-view-script-documents"></a>Postupy: Zobrazení dokumentů skriptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V dřívějších verzích nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se v okně Průzkumník skriptů objevily soubory skriptu na straně klienta generované ze skriptu na straně serveru. Okno Průzkumníka skriptů bylo často skryté, takže dostupnost skriptu na straně klienta není vždycky zřejmá.  
  
 V nástroji [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] se soubory skriptů na straně klienta generované ze skriptu na straně serveru zobrazují v Průzkumník řešení, což je ve výchozím nastavení viditelné. Okno Průzkumníka skriptů bylo eliminováno.  
  
 Soubory skriptu na straně klienta jsou viditelné pouze v režimu ladění nebo režimu přerušení. Zobrazí se v uzlu **dokumenty skriptu** .  
  
 Soubory skriptu na straně serveru jsou vždy viditelné. Zobrazí se v **\<Website Pathname>** uzlu. Název uzlu vypadá podobně jako v tomto příkladu: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Zobrazení dokumentu skriptu na straně serveru  
  
1. V **Průzkumník řešení**otevřete **\<Website Pathname>** uzel.  
  
2. Dvakrát klikněte na soubor skriptu, který chcete zobrazit.  
  
     V okně zdrojového kódu se otevře soubor skriptu na straně serveru.  
  
### <a name="to-view-a-client-side-script-document"></a>Zobrazení dokumentu skriptu na straně klienta  
  
1. V **Průzkumník řešení**otevřete uzel **dokumenty skriptu** .  
  
2. Dvakrát klikněte na soubor skriptu, který chcete zobrazit.  
  
     V okně zdrojového kódu se otevře soubor skriptu na straně klienta.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
