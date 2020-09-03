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
ms.openlocfilehash: 13ca035b01ec8af1277d70b3c792293a1af4687a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89325435"
---
Tyto kroky ukazují jenom základní konfiguraci služby IIS. Podrobné informace nebo informace o instalaci nástroje do stolního počítače s Windows najdete v tématu [publikování ve službě IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) nebo [IIS 8,0 s použitím ASP.NET 3,5 a ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Pro operační systémy Windows Server použijte průvodce **přidáním rolí a funkcí** prostřednictvím odkazu **Spravovat** nebo pomocí odkazu na **řídicí panel** v **Správce serveru**. V kroku **role serveru** zaškrtněte políčko **webový server (IIS)**.

![V kroku vybrat role serveru je vybraná role Webový server IIS.](../media/remotedbg-server-roles-ws2012.png)

V kroku **služby rolí** vyberte požadované služby role IIS nebo přijměte výchozí poskytnuté služby rolí. Pokud chcete povolit nasazení pomocí nastavení publikování a Nasazení webu, ujistěte se, že je vybraná možnost **skripty a nástroje správy služby IIS** .

Pokud chcete nainstalovat roli a služby webového serveru, postupujte podle kroků pro potvrzení. Po instalaci role Webový server (IIS) není nutné restartovat server nebo službu IIS.