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
ms.openlocfilehash: 95d76781f651b681b81e4dd18848b404d8a85664
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809255"
---
 Je třeba mít na ladění vašeho kódu se symboly, které vytvoříte na počítači aplikace Visual Studio. Výkon vzdáleného ladícího programu je mnohem lépe při použití místní symboly.  Pokud je nutné použít vzdálené symboly, budete muset říct sledování vzdáleného ladění hledat symboly ve vzdáleném počítači.  
  
 Od verze Visual Studio 2013 Update 2, vám pomůže následující msvsmon přepínač příkazového řádku pomocí vzdáleného symbolů pro spravovaný kód: `Msvsmon /FallbackLoadRemoteManagedPdbs`  
  
 Další informace najdete v tématu nápovědy vzdáleného ladění (stisknutím klávesy **F1** v okně vzdáleného ladicího programu, nebo klikněte na tlačítko **Nápověda > využití**). Další informace najdete [.NET změny vzdálené načítání symbolů v sadě Visual Studio 2012 a 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)