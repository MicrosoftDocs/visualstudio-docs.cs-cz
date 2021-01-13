---
title: Výstraha zabezpečení zdrojového serveru | Microsoft Docs
description: Přečtěte si informace o upozornění zabezpečení zdrojového serveru v ladicím programu sady Visual Studio. Mějte na paměti potenciální bezpečnostní hrozby při použití zdrojového serveru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf62abb91411048f46bfe7240074bd86c119bcd4
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149115"
---
# <a name="source-server-security-alert"></a>Výstraha zabezpečení zdrojového serveru
Při použití zdrojového serveru používejte pouze soubory symbolů, které jsou ze známého a důvěryhodného umístění.

 Toto upozornění se zobrazí, když povolíte podporu zdrojového serveru. Příkazy zdrojového serveru jsou vložené do souborů symbolů ladění (soubory **\* . pdb** ). Ujistěte se, že víte, odkud pocházejí vaše soubory PDB.

> [!IMPORTANT]
> Při použití zdrojového serveru je třeba vzít v úvahu následující potenciální bezpečnostní hrozby: libovolné příkazy lze vložit do souboru PDB aplikace, takže zajistěte, aby byly do souboru srcsrv.ini vloženy pouze ty, které chcete spustit. Pokus o provedení příkazu mimo soubor srcsvr.ini způsobí zobrazení dialogového okna s potvrzením. Další informace najdete v tématu [Upozornění zabezpečení: ladicí program musí spustit nedůvěryhodný příkaz](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Parametry příkazu nejsou ověřovány, proto buďte s důvěryhodnými příkazy opatrní. Například pokud důvěřujete souboru cmd.exe, uživateli se zlými úmysly může zadat parametry, které by z příkazu mohly udělat hrozbu.

## <a name="see-also"></a>Viz také
- [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Zdrojový Server](/windows/desktop/Debug/source-server-and-source-indexing)
