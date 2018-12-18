---
title: Upravit a pokračovat – dialogové okno chybové zprávy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c311f6243ddbf087fd18fd9209e2e17bbe3065a6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771331"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Dialogové okno chybových zpráv operace Upravit a pokračovat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto dialogové okno se zobrazí při ladění v jazyce, který podporuje funkce upravit a pokračovat, ale **upravit a pokračovat** není k dispozici pro typ provedené změny kódu. Chybová zpráva uvnitř pole poskytuje podrobnější vysvětlení. Možné příčiny zobrazení dialogovému oknu patří:  
  
-   Pokusili jste se při ladění nespravovaného kódu bylo povoleno upravit spravovaný kód. Upravit a pokračovat nefunguje s ladění ve smíšeném režimu.  
  
-   Pokusili jste se upravovat kód systému SQL Server.  
  
-   Pokusili jste se úpravy kódu během ladění zotavení po havárii. Watson s výpisem paměti.  
  
-   Jste se pokusili upravit kód následující po došlo k neošetřené výjimce a možnost "**vrátit zásobník volání v případě neošetřených výjimek**" nebyla vybrána.  
  
-   Pokusili jste se úpravy kódu během ladění aplikace vložený modul runtime.  
  
-   Pokusili jste se upravovat kód v programu v jazyce, který jste připojili nespouštět z **ladění** nabídky.  
  
-   Pokusili jste se upravit optimalizovaný kód.  
  
-   Pokusili jste se upravit spravovaný kód, pokud jsou cílem 64bitových aplikací. Pokud chcete k použití operace upravit a pokračovat, je nutné nastavit cíl na x86. (*Projektu* **vlastnosti**, **kompilaci** kartě **Advanced kompilátoru** nastavení.).  
  
-   Pokusili jste se úpravy kódu v sestavení, která byla změněna během ladění a má znovu načten.  
  
-   Pokusili jste se úpravy kódu v sestavení, který není načtený.  
  
-   Spuštění ladění starší verzi aplikace (protože nová verze má chyby sestavení).  
  
-   Pokusili jste se úpravy kódu byla spuštěna.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **OK**  
 Zavřete dialogové okno a zrušit bezprostředně předcházející pokus upravit.  
  
## <a name="see-also"></a>Viz také  
 [Podporované změny kódu (C++)](../debugger/supported-code-changes-cpp.md)



