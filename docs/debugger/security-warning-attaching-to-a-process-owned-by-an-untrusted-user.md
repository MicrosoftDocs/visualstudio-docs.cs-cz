---
title: 'Upozornění zabezpečení: Připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu | Microsoft Docs'
ms.date: 1/15/2021
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ec174a03e62cb8cb033be0b92db679fb19f0180
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881253"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Upozornění zabezpečení: Připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud následující údaje vypadají podezřele nebo si nejste jistí, k tomuto procesu se nepřipojujte.

Toto dialogové okno s upozorněním se zobrazí, když se připojíte k procesu, který obsahuje částečně důvěryhodný kód nebo který je vlastněn nedůvěryhodným uživatelem hned předtím, než dojde k připojení. Nedůvěryhodný proces, který obsahuje škodlivý kód, má potenciál poškodit počítač laděním. Máte-li důvod k nedůvěryhodnému procesu, klikněte na tlačítko **Storno** , čímž zabráníte ladění.

V případech služby IIS se toto upozornění může zobrazit, pokud použijete vlastní fond aplikací, který je nedůvěryhodný.

Pro potlačení tohoto upozornění při ladění legitimního scénáře:

1. Zavřete Visual Studio.

1. Nastavte hodnotu `DisableAttachSecurityWarning` klíče registru na 1.

   Vyhledejte nebo vytvořte klíč v oblasti `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger` a nastavte jej na hodnotu 1.

   Pokud chcete zobrazit kompletní nastavení registru, začněte v aplikaci Visual Studio 2017, je nutné načíst privátní podregistr registru. Další informace najdete v tématu [Kontrola registru sady Visual Studio 2017](https://github.com/microsoft/VSProjectSystem/blob/master/doc/overview/examine_registry.md). Před spuštěním sady Visual Studio se ujistěte, že jste odčetli privátní podregistr registru.

1. Restartujte Visual Studio.

1. Po dokončení ladění scénáře nastavte hodnotu na 0 a restartujte Visual Studio.

"Důvěryhodní uživatelé" zahrnují sebe sama a sadu standardních uživatelů, kteří jsou obvykle definováni v počítačích s nainstalovaným .NET Framework, například, `aspnet` `localsystem` , `networkservice` a `localservice` .

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

 Název sestavení požadovaného k ladění

 Aktuální uživatel uživatele

 Pokud chcete pokračovat v ladění pomocí připojení, stiskněte klávesu ENTER.

 Nepřipojeno k procesu nepřipojujte

## <a name="see-also"></a>Viz také
- [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
