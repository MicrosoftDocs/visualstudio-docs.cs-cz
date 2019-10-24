---
title: 'Upozornění zabezpečení: Připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05b78ea0ca06a0ba9670e61cc065cf539ea21ebc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729779"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Upozornění zabezpečení: Připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud následující údaje vypadají podezřele nebo si nejste jistí, k tomuto procesu se nepřipojujte.
Toto dialogové okno s upozorněním se zobrazí, když se připojíte k procesu, který obsahuje částečně důvěryhodný kód nebo který je vlastněn nedůvěryhodným uživatelem hned předtím, než dojde k připojení. Nedůvěryhodný proces, který obsahuje škodlivý kód, má potenciál poškodit počítač laděním. Máte-li důvod k nedůvěryhodnému procesu, klikněte na tlačítko **Storno** , čímž zabráníte ladění.

 Chcete-li toto upozornění potlačit při ladění legitimního scénáře, zavřete sadu Visual Studio a nastavte hodnotu tohoto klíče registru na 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning` a pak restartujte aplikaci Visual Studio. Po dokončení ladění scénáře nastavte hodnotu na 0 a restartujte Visual Studio.

 "Důvěryhodní uživatelé" zahrnují sebe sama a sadu standardních uživatelů, kteří jsou obvykle definováni v počítačích s nainstalovaným .NET Framework, například `aspnet`, `localsystem`, `networkservice` a `localservice`.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 Název sestavení požadovaného k ladění

 Aktuální uživatel uživatele

 Pokud chcete pokračovat v ladění pomocí připojení, stiskněte klávesu ENTER.

 Nepřipojeno k procesu nepřipojujte

## <a name="see-also"></a>Viz také:
- [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)