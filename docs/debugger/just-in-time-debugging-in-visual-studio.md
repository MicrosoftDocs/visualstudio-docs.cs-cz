---
title: Zakázat Just-In-Time Debugger | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/23/18
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 147e16bab14a6a038622804cf9c57e5fdc92bf02
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382776"
---
# <a name="disable-the-just-in-time-debugger"></a>Zakázat Just-In-Time Debugger 

Dialogové okno ladicího programu za běhu může spustit při výskytu chyby v běžící aplikaci a aplikace zabrání v pokračování. 

Ladicí program za běhu poskytuje možnost pro spuštění sady Visual Studio pro ladění k chybě. Musíte mít [sady Visual Studio](http://visualstudio.microsoft.com) nebo jiné vybraný ladicí program nainstalovat zobrazit podrobné informace o chybě, nebo to zkuste začít ladit. 

Pokud jste uživatelem Visual Studio a zkusit ladit chyby najdete v tématu [ladění pomocí ladicího programu za běhu](../debugger/debug-using-the-just-in-time-debugger.md). Pokud nelze opravit chybu nebo chcete zachovat ladicí program za běhu otevřít, můžete si [zakázání Just-In-Time ladění ze sady Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling). 

Pokud máte nainstalovanou sadu Visual Studio, ale už nechcete, budete muset [zakázání Just-In-Time ladění z registru Windows](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry). 

Pokud nemáte nainstalovanou sadu Visual Studio, je možné zabránit Just-In-Time ladění tím, že zakážete ladění skriptů nebo ladění na straně serveru. 

- Pokud se snažíte spustit webovou aplikaci, zakážete ladění skriptů:
  
  Ve Windows **ovládací panely** > **síť a Internet** > **Možnosti Internetu**vyberte **skript zakázání (ladění Aplikace Internet Explorer)** a **zakázat ladění skriptů (ostatní)**. Přesný postup a nastavení závisí na vaší verzi Windows a prohlížeče.
  
  ![Možnosti Internetu JIT](../debugger/media/jitinternetoptions.png "Možnosti Internetu JIT")
  
- Pokud máte webovou aplikaci ASP.NET ve službě IIS, zakážete ladění na straně serveru:

  1. Ve Správci služby IIS **zobrazení funkcí**v části **ASP.NET** části, dvakrát klikněte na panel **kompilace .NET**, nebo ho vyberte a pak vyberte **otevřít funkci**v **akce** podokně. 
  1. V části **chování** > **ladění**vyberte **False**. Postup se liší ve starších verzích služby IIS.

Po zakázání Just-In-Time ladění aplikace moci chybu zpracovat a bude normálně fungovat. 

Pokud má stále neošetřené chybě, může se zobrazit chybová zpráva nebo může dojít k chybě nebo zablokování aplikace. Aplikace nespustí obvykle, dokud nebudou opraveny chyby. Zkuste kontaktovat vlastníka aplikace a požádejte ho, aby ho opravit.

