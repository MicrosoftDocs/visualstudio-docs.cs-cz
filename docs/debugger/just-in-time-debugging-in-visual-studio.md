---
title: Zakázat program pro ladění za běhu | Microsoft Docs
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3155c2cdc9ea3dc5208a52e5fe37f697a4ad5ef6
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386118"
---
# <a name="disable-the-just-in-time-debugger"></a>Zakázání ladicího programu pro ladění za běhu

Dialogové okno ladicí program za běhu se může otevřít, když dojde k chybě ve spuštěné aplikaci a zabránit tomu, aby aplikace pokračovala.

Program pro ladění za běhu vám dává možnost spustit Visual Studio, aby se chyba mohla ladit. Pro zobrazení podrobných informací o chybě nebo pokusu o ladění je nutné mít nainstalovanou aplikaci Visual Studio nebo jiný vybraný ladicí program.

Pokud už jste uživatelem sady Visual Studio a chcete se pokusit ladit chybu, přečtěte si téma [ladění pomocí ladicího programu za běhu](../debugger/debug-using-the-just-in-time-debugger.md). Pokud nemůžete opravit chybu, nebo chcete zachovat otevření ladicího programu za běhu, můžete [z aplikace Visual Studio zakázat ladění za](debug-using-the-just-in-time-debugger.md#BKMK_Enabling)běhu.

Pokud máte nainstalovanou aplikaci Visual Studio, ale už ji neuděláte, možná budete muset v [registru Windows zakázat ladění za běhu](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry).

Pokud nemáte nainstalovanou aplikaci Visual Studio, můžete zabránit ladění za běhu tím, že zakážete ladění skriptů nebo ladění na straně serveru.

- Pokud se pokoušíte spustit webovou aplikaci, zakažte ladění skriptů:

  V **Ovládacích panelech Windows**  >  možnosti**sítě a Internet**  >  **Internet**vyberte možnost **Zakázat ladění skriptů (Internet Explorer)** a **Zakázat ladění skriptů (jiné)**. Přesné kroky a nastavení závisí na vaší verzi Windows a v prohlížeči.

  ![JIT – možnosti Internetu](../debugger/media/jitinternetoptions.png "JIT – možnosti Internetu")

- Pokud jste hostitelem webové aplikace v ASP.NET ve službě IIS, zakažte ladění na straně serveru:

  1. V **zobrazení funkcí**Správce služby IIS v části **ASP.NET** dvakrát klikněte na **kompilace rozhraní .NET**nebo vyberte možnost **otevřít funkci** v podokně **Akce** .
  1. V **Behavior**části  >  **ladění**chování vyberte **false (NEPRAVDA**). Postup se liší ve starších verzích služby IIS.

Po deaktivaci ladění za běhu může aplikace být schopná zpracovat chybu a normálně běžet.

Pokud má aplikace stále neošetřenou chybu, může se zobrazit chybová zpráva nebo může dojít k chybě aplikace nebo zastavení odezvy. Aplikace nebude fungovat normálně, dokud nebude chyba opravena. Můžete se pokusit kontaktovat vlastníka aplikace a požádat je o opravu.
