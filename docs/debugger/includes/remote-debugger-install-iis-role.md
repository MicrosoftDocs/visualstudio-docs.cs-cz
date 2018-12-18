---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 103000c2ded944236762ffd55603877ece7b7968
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809444"
---
Tyto kroky ukazují jenom základní konfiguraci služby IIS. Podrobnější informace nebo informace o instalaci na počítač s Windows Desktop, najdete v článku [publikování do služby IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) nebo [IIS 8.0 pomocí technologie ASP.NET 3.5 a technologii ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Pro operační systémy Windows Server, použijte **přidat role a funkce** prostřednictvím průvodce **spravovat** odkaz nebo **řídicí panel** odkaz v **správce serveru**. Na **role serveru** krok, zaškrtněte políčko u **webového serveru (IIS)**.

![V kroku výběr serveru role je vybrána role webového serveru IIS.](../media/remotedbg-server-roles-ws2012.png)

Na **služeb rolí** kroku, vyberte roli služby IIS potřeby nebo přijměte výchozí nastavení role služby poskytované. Pokud budete chtít povolit nasazení s použitím nastavení a nasazení webu publikování, ujistěte se, že **IIS skripty a nástroje správy** zaškrtnuto.

Pokračujte kroky potvrzení instalace role webového serveru a služby. Po instalaci role webového serveru (IIS) není potřeba restartovat server/IIS.