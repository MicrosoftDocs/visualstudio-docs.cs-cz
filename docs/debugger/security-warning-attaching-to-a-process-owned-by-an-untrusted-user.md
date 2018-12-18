---
title: 'Upozornění zabezpečení: Připojení k procesu vlastníkem nedůvěryhodné uživatele může být nebezpečný. Pokud tyto informace nezdá nebo si nejste jistí, nepřipojujte tohoto procesu | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68d88e01dde07789467272db830cae45ca5d60c4
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34178005"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Upozornění zabezpečení: Připojení k procesu vlastníkem nedůvěryhodné uživatele může být nebezpečný. Pokud tyto informace nezdá nebo si nejste jistí, nepřipojujte tohoto procesu
Toto dialogové okno upozornění se zobrazí, když se připojit k procesu, který obsahuje částečně důvěryhodného kódu nebo vlastní nedůvěryhodné uživatele okamžitě předtím, než dojde k připojení. Nedůvěryhodné proces, který obsahuje škodlivý kód se může poškodit počítač to ladění. Pokud máte důvod k nechtějí proces, a měli byste kliknout na **zrušit** aby se zabránilo ladění.  
  
 Toto upozornění při ladění legitimní scénář potlačit, zavřete Visual Studio a nastavte hodnotu tohoto klíče registru na 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`a pak restartujte Visual Studio. Po dokončení ladění scénář, obnovte hodnotu na 0 a restartujte Visual Studio.  
  
 "Důvěryhodné uživatelé" zahrnout sami a sada standardních uživatelů, kteří jsou obvykle definovány na počítače, které mají rozhraní .NET Framework nainstalované, jako například `aspnet`, `localsystem`, `networkservice`, a `localservice`.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 Název  
 Název sestavení požádal o ladění  
  
 Uživatel  
 Aktuální uživatel  
  
 Připojit  
 Chcete-li pokračovat v ladění připojením, klikněte na  
  
 Nemáte připojení  
 Nepřipojujte k procesu  
  
## <a name="see-also"></a>Viz také  
 [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)