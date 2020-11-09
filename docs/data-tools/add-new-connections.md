---
title: Přidání nových připojení
description: Přidejte připojení do sady Visual Studio do databáze nebo služby a prozkoumejte obsah a schémata databáze pomocí Průzkumník serveru, Průzkumníka cloudu nebo Průzkumník objektů systému SQL Server.
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 34f3ef6823ddfae806de11b85cc5bfe6b14c9b19
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382413"
---
# <a name="add-new-connections"></a>Přidání nových připojení

Můžete testovat připojení k databázi nebo službě a prozkoumat obsah databáze a schémata pomocí **Průzkumník serveru** , **Průzkumníka cloudu** nebo **Průzkumník objektů systému SQL Server**. Funkčnost těchto oken se překrývá do určitého rozsahu. Základní rozdíly:

- Průzkumník serveru

   Ve výchozím nastavení nainstalovány v aplikaci Visual Studio. Dá se použít k otestování připojení a zobrazení SQL Serverch databází, všech ostatních databází, které mají nainstalovaného poskytovatele ADO.NET, a některých služeb Azure. Zobrazuje také objekty nízké úrovně, jako jsou čítače výkonu systému, protokoly událostí a fronty zpráv. Pokud zdroj dat nemá žádného poskytovatele ADO.NET, nezobrazí se tady, ale můžete ho i nadále používat ze sady Visual Studio, a to tak, že se připojíte prostřednictvím kódu programu.

- Průzkumník cloudu

   Nainstalujte toto okno ručně jako rozšíření sady Visual Studio z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS). Poskytuje specializované funkce pro zkoumání a připojování ke službám Azure.

- Průzkumník objektů systému SQL Server

   Instaluje se s nástroji SQL Server Data Tools a zobrazují se v nabídce **zobrazení** . Pokud tam není zobrazená, přejděte do části **programy a funkce** v Ovládacích panelech, najděte Visual Studio a pak vyberte **změnit** a znovu spusťte instalační program po zaškrtnutí políčka pro nástroje SQL Server Data Tools. Pomocí **Průzkumník objektů systému SQL Server** můžete zobrazit databáze SQL (pokud mají poskytovatele ADO.NET), vytvářet nové databáze, měnit schémata, vytvářet uložené procedury, načítat připojovací řetězce, zobrazovat data a další. Databáze SQL, které nemají nainstalovaného poskytovatele ADO.NET, se tady nezobrazí, ale můžete se k nim pořád připojit prostřednictvím kódu programu.

## <a name="add-a-connection-in-server-explorer"></a>Přidání připojení v Průzkumník serveru

Chcete-li vytvořit připojení k databázi, klikněte na ikonu **Přidat připojení** v **Průzkumník serveru** nebo klikněte pravým tlačítkem myši v **Průzkumník serveru** v uzlu **datová připojení** a vyberte možnost **Přidat připojení**. Odtud se můžete připojit také k databázi na jiném serveru, službě SharePoint nebo službě Azure.

![Ikona Průzkumník serveru nového připojení](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Tím se otevře dialogové okno **Přidat připojení** . Tady jsme zadali název instance SQL Server LocalDB.

![Přidat nové připojení](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Změna zprostředkovatele

Pokud zdroj dat není požadovaný, klikněte na tlačítko **změnit** a vyberte nový zdroj dat nebo nového poskytovatele dat ADO.NET. Nový poskytovatel může požádat o vaše přihlašovací údaje v závislosti na tom, jak jste ji nakonfigurovali.

![Změnit Zprostředkovatel dat AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Otestování připojení

Po výběru zdroje dat klikněte na tlačítko **Test připojení**. Pokud to nepomůže, budete muset řešit problémy na základě dokumentace od dodavatele.

![Testovat připojení](../data-tools/media/raddata-test-connection.png)

Pokud je test úspěšný, jste připraveni vytvořit *zdroj dat* , což je Visual Studio Term, který se skutečně označuje jako *datový model* založený na podkladové databázi nebo službě.

## <a name="see-also"></a>Viz také

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
