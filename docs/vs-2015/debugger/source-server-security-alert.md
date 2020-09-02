---
title: Výstraha zabezpečení zdrojového serveru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f8b122deab5dbdc30b129bce221a804f8c53aa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699328"
---
# <a name="source-server-security-alert"></a>Výstraha zabezpečení zdrojového serveru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při použití zdrojového serveru používejte pouze soubory symbolů, které jsou ze známého a důvěryhodného umístění.  
  
 Toto upozornění se zobrazí, když povolíte podporu zdrojového serveru. Příkazy zdrojového serveru jsou vložené do souborů symbolů ladění (soubory PDB). Ujistěte se, že víte, odkud pocházejí vaše soubory PDB.  
  
> [!IMPORTANT]
> Při použití zdrojového serveru je třeba vzít v úvahu následující potenciální bezpečnostní hrozby: libovolné příkazy lze vložit do souboru PDB aplikace, takže zajistěte, aby byly do souboru srcsrv.ini vloženy pouze ty, které chcete spustit. Pokus o provedení příkazu mimo soubor srcsvr.ini způsobí zobrazení dialogového okna s potvrzením. Další informace najdete v tématu [Upozornění zabezpečení: ladicí program musí spustit nedůvěryhodný příkaz](../debugger/security-warning-debugger-must-execute-untrusted-command.md). U parametrů příkazu se neprovádí žádné ověření, proto buďte opatrní při důvěryhodných příkazech. Například pokud důvěřujete souboru cmd.exe, uživateli se zlými úmysly může zadat parametry, které by z příkazu mohly udělat hrozbu.  
  
## <a name="see-also"></a>Viz také  
 [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Zdrojový Server](https://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
