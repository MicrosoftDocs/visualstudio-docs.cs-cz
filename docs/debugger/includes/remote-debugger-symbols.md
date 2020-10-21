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
ms.openlocfilehash: 5033580f253a5eb42cbc64656e8c4661a2e246c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72912844"
---
Měli byste být schopni ladit kód pomocí symbolů, které vygenerujete v počítači se sadou Visual Studio. Výkon vzdáleného ladicího programu je mnohem lepší při použití místních symbolů.  Pokud je nutné použít vzdálené symboly, je nutné oznámit sledování vzdáleného ladění, aby vyhledalo symboly na vzdáleném počítači.  

Počínaje Visual Studio 2013 Update 2 můžete použít následující přepínač příkazového řádku msvsmon k použití vzdálených symbolů pro spravovaný kód: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Další informace naleznete v nápovědě pro vzdálené ladění (stiskněte klávesu **F1** v okně vzdáleného ladicího programu, nebo klikněte na tlačítko **Nápověda > používání**). Další informace najdete v informacích o [změnách vzdáleného načítání symbolů .NET v nástroji Visual Studio 2012 a 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
