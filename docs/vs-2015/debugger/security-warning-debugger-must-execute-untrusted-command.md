---
title: 'Upozornění zabezpečení: ladicí program musí spustit nedůvěryhodný příkaz | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a29ba026f9b3c2b8839d474c2d0833eb79f7ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683299"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Upozornění zabezpečení: Ladicí program musí spustit nedůvěryhodný příkaz.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto dialogové okno s upozorněním se zobrazí, když používáte zdrojový server. Indikuje, že příkaz, který ladicí program potřebuje spustit pro získání zdrojového kódu, není v seznamu důvěryhodných příkazů pro zdrojový server, který je obsažený v souboru srcsvr.ini. Pokud se jedná o platný příkaz, můžete ho přidat do souboru srcsvr.ini. V opačném případě byste ji neměli spouštět. Další informace naleznete v tématu [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Text zprávy  
 **Ladicí program musí spustit následující nedůvěryhodný příkaz, aby získal zdrojový kód ze zdrojového serveru.**  
  
 **Pokud soubor se symboly ladění ( \* PDB) nepochází ze známého a důvěryhodného zdroje, může být tento příkaz neplatným nebo nebezpečným spuštěním.**  
  
 **Chcete spustit tento příkaz?**  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 Textové pole  
 Příkaz ze souboru. pdb, který se má spustit.  
  
 Spustit  
 Povolte spuštění příkazu.  
  
 Nespouštět  
 Zastavte spuštění příkazu a stažení souboru ze zdrojového serveru.  
  
## <a name="see-also"></a>Viz také  
 [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Zdrojový Server](https://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)
