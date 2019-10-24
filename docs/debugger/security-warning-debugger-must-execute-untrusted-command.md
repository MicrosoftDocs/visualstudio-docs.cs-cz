---
title: 'Upozornění zabezpečení: ladicí program musí spustit nedůvěryhodný příkaz | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0922461c4ca5366e6d1dc215f5711f5566d00ae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729753"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Upozornění zabezpečení: Ladicí program musí spustit nedůvěryhodný příkaz.
Toto dialogové okno s upozorněním se zobrazí, když používáte zdrojový server. Indikuje, že příkaz, který ladicí program potřebuje spustit pro získání zdrojového kódu, není v seznamu důvěryhodných příkazů pro zdrojový server, který je obsažený v souboru srcsvr. ini. Pokud se jedná o platný příkaz, můžete ho přidat do souboru srcsvr. ini. V opačném případě byste ji neměli spouštět. Další informace naleznete v tématu [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Text zprávy
 **Ladicí program musí spustit následující nedůvěryhodný příkaz, aby získal zdrojový kód ze zdrojového serveru.**

 **Pokud soubor se symboly ladění (\*. pdb) nepochází ze známého a důvěryhodného zdroje, může být tento příkaz neplatný nebo nebezpečný pro spuštění.**

 **Chcete spustit tento příkaz?**

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 Příkaz textového pole ze souboru. pdb, který se má spustit.

 Spusťte příkaz umožňující spuštění příkazu.

 Nespouštějte příkaz Zastavit provádění příkazu a stažení souboru ze zdrojového serveru.

## <a name="see-also"></a>Viz také:
- [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Zdrojový Server](/windows/desktop/Debug/source-server-and-source-indexing)