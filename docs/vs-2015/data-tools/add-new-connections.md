---
title: Přidat nové připojení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 03407962b4ea8160d492971367f121835fa39aae
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218502"
---
# <a name="add-new-connections"></a>Přidat nové připojení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Můžete otestovat připojení k databázi nebo službu a prozkoumat obsah databáze a schémat, pomocí **Průzkumníka serveru**, **Průzkumníka cloudu**, nebo **Průzkumník objektů systému SQL Server**. Funkce z těchto oken se překrývá do určité míry. Základní rozdíly jsou:  
  
 Průzkumník serveru  
 Ve výchozím nastavení v sadě Visual Studio nainstalované. Slouží k testování připojení a zobrazení databáze systému SQL Server, všechny databáze, které mají nainstalovaný poskytovatele ADO.NET a některé služby Azure. Také ukazuje objektů nízké úrovně, jako jsou čítače výkonu systému, protokoly událostí a fronty zpráv. Pokud zdroj dat nemá žádný poskytovatel ADO.NET, nebude tady nezobrazí, ale můžete ji mohou dál používat ze sady Visual Studio připojením prostřednictvím kódu programu.  
  
 Průzkumník cloudu  
 Ruční instalace tohoto okna jako rozšíření sady Visual Studio tak, že vyberete **nástroje** > **rozšíření a aktualizace** > **Online**  >  **Galerie sady visual Studio**. Poskytuje specializované funkce pro zkoumání a připojení ke službám Azure.  
  
 Průzkumník objektů systému SQL Server  
 Instalace SQL Server Data Tools a je viditelný v části **zobrazení** nabídky. Pokud ho nevidíte existuje, přejděte na **programy a funkce** v Ovládacích panelech, vyhledejte Visual Studio a pak vyberte **změnu** znovu spusťte instalační program po zaškrtnutí políčka pro SQL Server Data Tools. Použití **Průzkumník objektů systému SQL Server** pro databází SQL, view (v případě, že mají poskytovatele ADO.NET), vytvářet nové databáze, měnit schémata, vytvořit uložené procedury, načíst připojovací řetězce, zobrazení dat a další. Databáze SQL, které mají nainstalován žádný poskytovatel ADO.NET zde nezobrazí, ale můžete se připojit k nim prostřednictvím kódu programu.  
  
## <a name="add-a-connection-in-server-explorer"></a>Přidání připojení v Průzkumníku serveru  
 Chcete-li vytvořit připojení k databázi, klikněte na tlačítko **přidat připojení** ikonu v **Průzkumníka serveru**, nebo klikněte pravým tlačítkem na **Průzkumníka serveru** na **dat Připojení** uzel a vyberte možnost **přidat připojení**. Z tohoto místa můžete také připojit k databázi na jiném serveru, služby SharePoint nebo služby Azure.  
  
 ![Ikona nové připojení Průzkumníku serveru](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata ikona nové připojení Průzkumníku serveru")  
  
 Tím se zobrazí **přidat připojení** dialogové okno. Tady jsme zadali název instance serveru SQL Server LocalDB.  
  
 ![Přidat nové připojení](../data-tools/media/raddata-add-new-connection-dialog.png "raddata přidat nové dialogové okno připojení")  
  
## <a name="change-the-provider"></a>Změňte zprostředkovatele  
 Pokud je zdroj dat není to, co chcete, klikněte na tlačítko **změnu** vyberte nový zdroj dat a/nebo nového poskytovatele dat ADO.NET. Nový zprostředkovatel může požádat o přihlašovací údaje, v závislosti na tom, jak jste je nakonfigurovali.  
  
 ![Změňte poskytovatele dat AD0.NET](../data-tools/media/raddata-change-ad0-net-data-provider.png "raddata poskytovatel dat AD0.NET změny")  
  
## <a name="test-the-connection"></a>Test připojení  
 Po výběru zdroje dat, klikněte na tlačítko **Test připojení**. Pokud neproběhne úspěšně, je potřeba řešit podle v dokumentaci od výrobce.  
  
 ![Test připojení](../data-tools/media/raddata-test-connection.png "raddata Test připojení")  
  
 Pokud je test úspěšný, jste připraveni vytvořit *zdroj dat*, což je sada Visual Studio termín, který ve skutečnosti znamená, že *datový model* založený na základní databázi nebo službu.  
  
## <a name="see-also"></a>Viz také  
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

